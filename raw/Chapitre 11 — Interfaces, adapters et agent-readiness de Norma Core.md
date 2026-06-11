## 0. Mini-carte des chapitres restants

- **Chapitre 11 — Interfaces, adapters et agent-readiness** : définir comment Norma Core sera exposé ou connecté sans transformer ces interfaces en core.
    
- **Chapitre 12 — Structure de spec globale et ADRs** : organiser la spec complète et préparer les décisions d’architecture.
    
- **Chapitre 13 — MVP demo brief** : formuler la démo vérité du MVP.
    
- **Chapitre 14 — Roadmap MVP** : ordonner les étapes produit/tech du MVP.
    
- **Chapitre 15 — Plan PR / plan développeur** : traduire la spec en plan d’exécution développeur.
    

---



## 1. Verdict sur interfaces et adapters

Le verdict est strict :

> **Les interfaces et adapters sont des clients du core. Ils exposent, traduisent, affichent, importent ou exportent Norma Core ; ils ne définissent pas Norma Core.**

Norma Core reste le moteur déterministe qui applique des systèmes proportionnels versionnés à des espaces structurés pour produire constructions, mesures, évaluations, décisions et artifacts reproductibles. Cette frontière a déjà été posée : le core applique des systèmes proportionnels à des espaces structurés, tandis que tout ce qui affiche, capture, appelle, exporte, héberge ou connecte Norma est un client ou un adapter.

Un adapter existe pour connecter Norma à un environnement externe : caméra, CLI, API, MCP, Figma, AutoCAD, Blender, Rhino, Revit, Photoshop, ChatGPT, Claude, Codex, etc. Sa règle centrale est déjà claire : il peut transformer des données vers ou depuis Norma Core, mais il ne doit jamais redéfinir les règles proportionnelles.

Phrase à verrouiller :

> **Le core calcule. Les packs décrivent les systèmes. Les interfaces appellent. Les adapters traduisent. Les artifacts représentent.**

Conséquences :

- une CLI ne devient pas le modèle ;
    
- un SDK ne devient pas la vérité métier ;
    
- une API ne devient pas le core ;
    
- un serveur MCP ne décide pas des rules ;
    
- un plugin ne définit pas les ratios ;
    
- une caméra ne définit pas la géométrie ;
    
- un export SVG/DXF/PDF ne devient jamais source de vérité ;
    
- un agent ne peut pas inventer de ratio, de rule, de score ou d’explication.
    

La frontière est nécessaire pour préserver les invariants déjà verrouillés : données structurées, packs versionnés, opérations déterministes, warnings explicites, artifacts dérivés, `Run`, `PackLock`, idempotence et replay.

---

## 2. Frontière core / interface

## 2.1 Ce qui appartient au core

Appartient au core tout ce qui est nécessaire pour produire un résultat Norma déterministe, traçable et replayable.

|Domaine|Appartient au core|
|---|---|
|Modèle géométrique|`SegmentSpace`, `SurfaceSpace`, composition 2D simple, points, segments, lignes, rectangles, guides, zones, grid cells, intersections.|
|Coordonnées|Repère Norma, système de coordonnées, normalisation, métrique, tolérances.|
|Packs|Résolution de `RatioPack`, `Ratio`, `RatioSequence`, `Rule`, `RuleSet`, `PackLock`.|
|Opérations|Validation, résolution, construction, mesure, dérivation, évaluation, comparaison, explication.|
|Constructions|`Construction`, `Guide`, `Zone`, `Grid`, `IntersectionPoint`, relations dérivées.|
|Measurements|Distances, positions, angles, aires, ratios, containment, overlap, coverage, relations directionnelles basiques.|
|Evaluation|`Evaluation`, `Score`, `Decision`, `Explanation`, profiles, component scores, confidence, warnings.|
|Artifacts conceptuels|`StructuredResultArtifact`, summaries, reports structurés, visual artifact simple comme projection dérivée.|
|Reproductibilité|`Run`, `OperationContext`, `PackLock`, warnings, errors, provenance, idempotence, replay.|

Le core reçoit des entrées structurées et retourne des résultats structurés. Les opérations acceptent uniquement des entrées structurées, ne dépendent pas d’image, caméra, UI, plugin, cloud ou modèle IA, et doivent conserver inputs, pack, rules, contexte, warnings et provenance pour préparer idempotence et replay.

---

## 2.2 Ce qui appartient aux interfaces

Appartient aux interfaces tout ce qui concerne l’appel, la présentation, l’expérience utilisateur, l’intégration ou le transport.

|Domaine|Appartient aux interfaces/adapters|
|---|---|
|Interaction|CLI commands, UI screens, forms, panels, gestures, selections.|
|Transport|HTTP, local process call, SDK method, MCP tool call, plugin bridge.|
|Présentation|couleurs, thèmes, zoom, pan, hover, sélection, calques visuels.|
|Import|lecture de fichiers externes, parsing de formats, extraction de géométrie.|
|Export|conversion d’artifacts vers SVG, CSV, DXF, PDF, plugin payload, formats natifs futurs.|
|Environnement|caméra, canvas, outil design, CAD, agent, client web, desktop, mobile.|
|État client|session, viewport, préférences UI, historique d’écran, device pixel ratio.|
|Mapping externe|conversion coordonnées écran/CAD/design tool vers coordonnées Norma.|

Les interfaces peuvent choisir comment présenter un résultat. Elles ne peuvent pas changer ce que le résultat est.

Phrase à verrouiller :

> **Une interface peut décider comment appeler Norma et comment afficher ses sorties. Elle ne peut pas décider ce que Norma calcule.**

---

## 2.3 Frontière pratique

|Question|Réponse|
|---|---|
|Qui définit les ratios ?|Les packs.|
|Qui applique les ratios ?|Le core.|
|Qui transforme un calque Figma ou une entité CAD en input Norma ?|L’adapter.|
|Qui mesure distances, aires, angles, overlap ?|Le core.|
|Qui choisit les couleurs d’un overlay ?|L’interface ou l’export layer.|
|Qui produit un warning si une donnée externe est ambiguë ?|L’adapter pour l’import, puis le core pour la validation/calcul.|
|Qui décide qu’un SVG est stale ?|Le modèle artifact/replay du core.|
|Qui expose une opération à un agent ?|MCP/API/skill, mais l’opération reste core.|
|Qui invente une rule manquante ?|Personne. Erreur ou warning.|

---

## 3. Types d’interfaces futures

## 3.1 Classification conceptuelle

|Interface / adapter|Catégorie|Rôle|Ce que ce n’est pas|
|---|---|---|---|
|CLI|Interface d’appel locale|Exécuter des opérations Norma avec inputs structurés et produire outputs/artifacts.|Pas le modèle core.|
|SDK|Interface développeur|Fournir une surface d’appel stable aux opérations core.|Pas une logique métier parallèle.|
|API|Interface réseau/process|Exposer les opérations via un contrat de transport.|Pas une source de vérité distante.|
|MCP server|Interface agent|Exposer des opérations comme tools invocables par agents.|Pas un moteur d’inférence Norma.|
|Plugins|Interface logicielle intégrée|Connecter un outil externe à Norma.|Pas un endroit où définir rules/packs.|
|Camera app|Client de capture/overlay|Transformer une scène ou annotation en input structuré, afficher des guides.|Pas une dépendance core.|
|CAD adapters|Adapters métier géométriques|Traduire entités CAD simplifiées vers objets Norma et artifacts vers formats CAD.|Pas un moteur CAD natif.|
|Design tool adapters|Adapters design/layout|Traduire frames, rectangles, bounds, guides, selections vers Norma.|Pas un modèle design tool dans le core.|
|Agent skills/playbooks|Couche d’orchestration agent|Guider un agent pour appeler Norma correctement.|Pas une source de ratios, rules ou résultats.|

---

## 3.2 CLI

La CLI est une interface d’appel. Elle prend des fichiers ou données structurées, appelle les opérations core, puis écrit des résultats structurés ou artifacts.

Elle peut :

- valider un pack ;
    
- lancer une construction ;
    
- mesurer une composition ;
    
- produire un JSON structuré ;
    
- produire un SVG simple ;
    
- afficher warnings/errors ;
    
- rejouer un `Run` si toutes les dépendances sont disponibles.
    

Elle ne doit pas :

- définir des ratios inline comme vérité ;
    
- choisir implicitement un pack ;
    
- masquer les warnings ;
    
- convertir un SVG en input core ;
    
- modifier les règles pour simplifier une commande.
    

Statut recommandé : **V1.5**, sauf usage très minimal de démo hors définition du core strict.

---

## 3.3 SDK

Le SDK est une surface d’appel pour développeurs.

Il peut :

- exposer les opérations publiques ;
    
- fournir des types d’inputs/outputs ;
    
- aider à construire des objets Norma valides ;
    
- retourner résultats, warnings, errors, provenance ;
    
- faciliter replay et artifact generation.
    

Il ne doit pas :

- dupliquer le moteur ;
    
- avoir ses propres règles de scoring ;
    
- hardcoder les ratios ;
    
- “corriger” silencieusement les inputs ;
    
- cacher le `Run`, le `PackLock` ou les warnings.
    

Statut recommandé : **V1.5**, après stabilisation conceptuelle des opérations publiques.

---

## 3.4 API

L’API expose Norma par transport. Elle peut être locale ou distante plus tard, mais conceptuellement elle reste une interface.

Elle peut :

- recevoir structured input ;
    
- appeler une opération core ;
    
- retourner structured output ;
    
- exposer errors/warnings ;
    
- exposer artifacts ;
    
- référencer `Run`, `PackLock`, operation version.
    

Elle ne doit pas :

- faire dépendre le core d’un serveur ;
    
- introduire un état global caché ;
    
- transformer un timestamp ou une session en identité core ;
    
- permettre des opérations non déterministes ;
    
- accepter prompt libre comme source de vérité.
    

Statut recommandé : **V1.5 / futur**, selon besoin produit.

---

## 3.5 MCP server

Le serveur MCP est une interface agent. Il expose des opérations Norma comme tools.

Il peut :

- proposer des tools comme `validatePack`, `generateConstruction`, `evaluateCompositionBasic`, `compareCompositionsBasic`, `createArtifact` ;
    
- déclarer schemas d’input/output ;
    
- retourner warnings/errors structurés ;
    
- fournir des artifact references ;
    
- permettre à un agent de rejouer ou inspecter un `Run`.
    

Il ne doit pas :

- inventer un ratio absent ;
    
- générer une rule depuis une formulation vague ;
    
- créer un score sans profile ;
    
- produire une explanation non traçable ;
    
- transformer une préférence d’agent en vérité core ;
    
- choisir automatiquement le “meilleur système” sans opération déclarée.
    

Statut recommandé : **V1.5 minimal**, puis futur complet.

---

## 3.6 Plugins

Un plugin connecte Norma à un logiciel externe.

Il peut :

- lire une sélection ;
    
- extraire des bounds structurés ;
    
- transformer des objets natifs en `SurfaceSpace`, `Element`, `Guide`, `Zone` si possible ;
    
- appeler le core ;
    
- afficher ou insérer un artifact ;
    
- conserver provenance vers l’objet externe.
    

Il ne doit pas :

- faire entrer l’objet natif dans le core ;
    
- imposer la structure interne du logiciel au modèle Norma ;
    
- créer des rules dans le plugin ;
    
- transformer des layers en source proportionnelle ;
    
- masquer les pertes de conversion.
    

Statut recommandé : **futur**.

---

## 3.7 Camera app

Une camera app est un client de capture et de visualisation.

Elle peut :

- afficher des guides ou zones dérivés ;
    
- recevoir des annotations structurées ;
    
- transformer des points, rectangles ou anchors validés en input Norma ;
    
- associer une source externe à une provenance ;
    
- produire des warnings de calibration ou de confiance.
    

Elle ne doit pas :

- faire de l’image brute une entrée core V1 ;
    
- faire dépendre le core du tracking ;
    
- imposer le repère caméra comme repère Norma ;
    
- inférer automatiquement l’intention ;
    
- transformer un overlay en construction source.
    

Statut recommandé : **futur**. La V1 stricte exclut caméra, image, vision et tracking.

---

## 3.8 CAD adapters

Un CAD adapter traduit des entités CAD simples vers objets Norma ou des artifacts Norma vers formats CAD.

Il peut traduire :

- lignes simples → `Segment` ou `Guide` candidat ;
    
- rectangles axis-aligned → `Rect`, `Element`, `Zone` ;
    
- dimensions de plan → `SurfaceSpace` ;
    
- calques sélectionnés → groupes externes avec provenance ;
    
- guides Norma → lignes CAD exportées ;
    
- zones Norma → contours ou annotations CAD.
    

Il ne doit pas inventer :

- contraintes CAD natives comme vérité core ;
    
- polygones complexes V1 ;
    
- tolérances métier implicites ;
    
- ratios architecturaux non présents dans un pack ;
    
- axes ou modules non produits par une operation.
    

Warnings obligatoires si :

- entité non axis-aligned ;
    
- polygone ou courbe ignoré ;
    
- unité CAD ambiguë ;
    
- calque sans rôle clair ;
    
- coordonnées converties avec perte ;
    
- format cible ne peut pas préserver provenance ;
    
- export CAD est lossy ou non replayable.
    

Statut recommandé : **futur / prototype V1.5 non-core**.

---

## 3.9 Design tool adapters

Un design tool adapter connecte Norma à Figma, Sketch, Illustrator, InDesign ou outils similaires.

Il peut traduire :

- frame/artboard → `SurfaceSpace` ;
    
- rectangle/layer bounds → `Element` ;
    
- guides existants → guides externes déclarés, pas rules ;
    
- groupes plats → composition simple ;
    
- constraints simples → metadata externe ;
    
- artifact visuel Norma → overlay ou calques de guides.
    

Il ne doit pas inventer :

- ratios depuis noms de layers ;
    
- rules depuis une auto-layout rule ;
    
- hiérarchie perceptive depuis un ordre de calque ;
    
- score depuis un rendu ;
    
- geometry depuis style ou couleur.
    

Warnings obligatoires si :

- rotation présente ;
    
- masques/clips actifs ;
    
- auto-layout transforme la géométrie ;
    
- bounds ne reflètent pas la forme réelle ;
    
- texte ou image ne peut être représenté que par rectangle ;
    
- calques imbriqués exigent une hiérarchie hors V1 ;
    
- coordonnées écran converties vers repère Norma.
    

Statut recommandé : **V1.5 / futur**.

---

## 3.10 Agent skills / playbooks

Les agent skills/playbooks sont des instructions d’orchestration pour agents.

Ils peuvent :

- expliquer à un agent quelles opérations appeler ;
    
- imposer de fournir pack, rules, tolérances, context ;
    
- vérifier qu’un output contient warnings/errors ;
    
- demander replay ou provenance ;
    
- guider la formulation d’une explanation ;
    
- empêcher les claims interdits.
    

Ils ne doivent pas :

- créer un ratio ;
    
- créer une rule ;
    
- choisir une tolérance implicite ;
    
- interpréter un score comme beauté ;
    
- résumer un warning critique en “OK” ;
    
- écrire une conclusion non supportée par `Measurement`, `Evaluation` ou `Decision`.
    

Statut recommandé : **V1.5**, après stabilisation des opérations publiques et des outputs structurés.

---

## 4. Adapter contract

## 4.1 Définition

Un adapter est une couche de traduction entre un environnement externe et Norma Core.

Phrase à verrouiller :

> **Un adapter traduit. Il ne calcule pas à la place du core. Il ne définit pas les ratios. Il ne redéfinit pas les rules. Il ne transforme pas un export externe en vérité Norma.**

---

## 4.2 Chaîne de transformation autorisée

Chaîne correcte :

```txt
external data
→ Norma structured input
→ core operation
→ Norma result
→ artifact
→ external target format
```

Directions strictes :

1. **external data → Norma structured input**  
    L’adapter lit un environnement externe et produit des objets Norma valides ou des erreurs/warnings.
    
2. **Norma structured input → core operation**  
    Le core reçoit uniquement des objets structurés, packs, rules, tolérances, contexte.
    
3. **Norma result → artifact**  
    Le core produit ou référence des résultats structurés ; un artifact les représente.
    
4. **artifact → external target format**  
    L’adapter convertit l’artifact vers le format cible : SVG, DXF, plugin payload, overlay, etc.
    
5. **external target format ≠ source de vérité core**  
    Un fichier, layer, SVG, DXF, screenshot ou payload plugin ne devient jamais la vérité Norma.
    

Les artifacts sont déjà définis comme représentations dérivées, jamais source de vérité ; un export externe ne doit jamais imposer son modèle au core.

---

## 4.3 Responsabilités obligatoires d’un adapter

Un adapter doit :

- identifier la source externe ;
    
- extraire ou recevoir des données géométriques ;
    
- convertir les coordonnées vers le repère Norma ;
    
- produire des objets Norma structurés ;
    
- déclarer les pertes de conversion ;
    
- déclarer les hypothèses ;
    
- préserver provenance ;
    
- appeler des opérations core explicites ;
    
- transmettre pack, rules, tolérances et contexte ;
    
- retourner warnings/errors sans les masquer ;
    
- produire ou transformer des artifacts ;
    
- marquer les exports lossy, stale ou non replayable si nécessaire.
    

---

## 4.4 Interdictions d’un adapter

Un adapter ne doit pas :

- contenir des ratios cachés ;
    
- créer des rules ;
    
- choisir un pack implicite ;
    
- choisir une tolérance implicite qui change le résultat ;
    
- transformer un calque, layer, block CAD ou node Figma en modèle core natif ;
    
- supprimer des warnings ;
    
- produire une évaluation sans measurements ;
    
- produire une explanation sans sources ;
    
- transformer un artifact externe en input core sans re-normalisation ;
    
- utiliser l’ordre de sélection UI comme ordre sémantique sauf déclaration explicite.
    

---

## 4.5 Warnings génériques d’adapter

|Warning|Sens|
|---|---|
|`ExternalGeometrySimplified`|Une géométrie externe a été simplifiée vers une primitive V1.|
|`UnsupportedExternalGeometry`|Une géométrie externe ne peut pas être traduite en V1.|
|`CoordinateSystemConverted`|Les coordonnées ont été converties vers le repère Norma.|
|`CoordinateSystemAmbiguous`|Le repère source n’est pas suffisamment déclaré.|
|`UnitAmbiguous`|L’unité externe est absente ou incertaine.|
|`LossyImport`|L’import perd style, hiérarchie, courbes, rotation ou provenance.|
|`LossyExport`|L’export ne peut pas porter toute la sémantique Norma.|
|`ExternalOrderingNotSemantic`|L’ordre externe ne doit pas être interprété comme ordre métier.|
|`ExternalLayerRoleAmbiguous`|Un layer/calque/groupe n’a pas de rôle Norma fiable.|
|`NativeObjectNotCoreObject`|Un objet natif externe a été référencé, mais non intégré au core.|
|`ExternalTargetMayModifyGeometry`|Le logiciel cible peut réinterpréter ou modifier la géométrie.|
|`NonReplayableExternalReference`|La source externe ne suffit pas pour replay strict.|

---

## 4.6 Contrat par adapter

|Adapter|Peut traduire|Ne doit pas inventer|Warnings requis si incomplet/ambigu|
|---|---|---|---|
|CLI|Fichiers/données structurées vers inputs Norma ; outputs vers JSON/SVG simple.|Packs, rules, tolérances implicites.|Input incomplet, pack absent, chemin non stable, artifact demandé sans source.|
|SDK|Objets applicatifs vers objets Norma typés ; résultats vers objets client.|Logique core parallèle, scoring SDK, ratios hardcodés.|Champs manquants, contexte absent, opération incompatible.|
|API|Payload structuré vers opération core ; résultat vers payload de transport.|État serveur comme vérité, defaults cachés.|Payload non canonique, context absent, version mismatch.|
|MCP server|Tool calls vers opérations core ; outputs structurés pour agents.|Rules générées par prompt, ratios hallucinated, conclusions libres.|Prompt insuffisant, tool input incomplet, pack/rule absent, demande de claim interdit.|
|Plugin|Sélection externe vers surface/elements/guides ; artifacts vers overlay/calques.|Structure native comme modèle Norma, pack plugin caché.|Objet natif non supporté, selection partielle, mapping coordonnées incertain.|
|Camera app|Annotations structurées, surfaces calibrées, anchors validés vers Norma.|Géométrie depuis image brute en core V1, intention, tracking comme vérité.|Calibration faible, perspective non corrigée, confidence basse, source non replayable.|
|CAD adapter|Lignes/rectangles/dimensions simples vers Norma ; artifacts vers lignes/zones CAD.|Contraintes CAD natives, polygones V1, modules métier implicites.|Unités ambiguës, entités non axis-aligned, courbes/polygones ignorés.|
|Design tool adapter|Frames, rectangles, bounds, guides, groups plats vers Norma.|Ratios depuis layers, scoring depuis rendu, auto-layout comme rule core.|Rotation, mask, clip, nested frames, text bounds approximés, repère écran converti.|
|Agent playbook|Intentions structurées vers séquence d’opérations autorisées.|Ratios, rules, scores, explanations non sourcés.|Demande vague, conflit pack/profile, résultat ambigu, warning critique présent.|

---

## 5. Agent-readiness

## 5.1 Verdict

Norma doit être utilisable par des agents, mais seulement si les agents appellent le core comme une machine déterministe.

Phrase à verrouiller :

> **Un agent ne pense pas à la place de Norma. Il prépare des inputs, appelle des opérations, lit des outputs, respecte les warnings et cite la provenance.**

L’agent-readiness n’est pas une couche de magie. C’est une discipline d’interface.

---

## 5.2 Ce que Norma doit offrir aux agents

Norma doit offrir :

|Besoin agent|Exigence Norma|
|---|---|
|Opérations explicites|Chaque capacité exposée doit correspondre à une opération nommée et versionnée.|
|Structured inputs|Un agent doit fournir surface, composition, pack, rules, tolérances, context.|
|Structured outputs|Résultat machine-readable : construction, measurements, evaluation, decision, artifacts, warnings/errors.|
|Warnings/errors|Les agents doivent recevoir des statuts explicites et ne pas deviner.|
|Replay|Un agent doit pouvoir demander ou référencer un `Run`.|
|Artifacts|Les agents doivent pouvoir récupérer un artifact sans le traiter comme vérité.|
|Explanations|Les agents doivent recevoir des explanations dérivées des measurements.|
|Pack locks|L’agent doit savoir quel pack/version/content identity a été utilisé.|
|Operation context|L’agent doit savoir quelles versions, tolérances, policies et coordinate system ont servi.|
|No hallucinated ratios|Un ratio absent du pack doit produire erreur ou warning, pas invention.|

Le `Run` est l’enveloppe centrale de reproductibilité et doit contenir operation, operation version, input, context, pack refs, rule refs, tolerances, coordinate system, output refs, warnings et errors. Le `PackLock` verrouille pack id, pack version et content identity.

---

## 5.3 Comportement attendu d’un agent

Un agent doit :

- demander ou fournir un pack explicite ;
    
- demander ou fournir une operation explicite ;
    
- fournir un input structuré ;
    
- ne jamais substituer un prompt à une géométrie ;
    
- ne jamais cacher warnings/errors ;
    
- ne jamais transformer une evaluation en beauty score ;
    
- ne jamais dire “Norma pense que…” sans source ;
    
- formuler les résultats comme relatifs au pack, au profile, aux tolérances et au contexte ;
    
- demander replay si un résultat doit être vérifié.
    

Formulation correcte :

> “Selon le pack `norma.basic-proportions`, le centre de l’élément est à 0.012 du guide `x=1/3`, sous la tolérance déclarée.”

Formulation interdite :

> “L’agent voit que la composition est belle parce qu’elle suit les tiers.”

---

## 5.4 Erreurs spécifiques agent-readiness

|Erreur|Sens|
|---|---|
|`AgentPromptNotStructuredInput`|Le prompt ne contient pas d’input Norma exploitable.|
|`AgentRequestedImplicitPack`|L’agent demande une opération sans pack explicite.|
|`AgentInventedRatioRejected`|L’agent a introduit un ratio absent du pack.|
|`AgentInventedRuleRejected`|L’agent a demandé une rule non déclarée.|
|`AgentExplanationNotTraceable`|L’explication demandée ne peut pas être dérivée des sources.|
|`AgentAestheticClaimRejected`|L’agent demande beauté/intention/qualité universelle.|
|`AgentIgnoredWarnings`|L’agent tente de produire une conclusion malgré warnings critiques.|
|`AgentReplayMissingDependencies`|Replay impossible car pack/input/context manquant.|

---

## 5.5 Warnings spécifiques agent-readiness

|Warning|Sens|
|---|---|
|`AgentInputUnderSpecified`|Input incomplet mais partiellement exploitable.|
|`AgentOutputPartial`|Résultat partiel à cause de données insuffisantes.|
|`AgentAmbiguousIntent`|L’intention utilisateur doit être convertie en opération plus explicite.|
|`AgentSelectedDefaultNotCoreTruth`|Un choix d’agent est un choix d’orchestration, pas une règle core.|
|`AgentSummaryMayOmitDetails`|Résumé agent potentiellement lossy ; consulter output structuré.|
|`AgentNeedsPackSelection`|Plusieurs packs possibles ; aucun ne doit être supposé.|

---

## 6. Interfaces V1 strict / V1.5 / futur

## 6.1 V1 strict

La V1 stricte ne doit pas dépendre d’une interface riche. Elle doit seulement rendre le core appelable conceptuellement.

À garder dans V1 strict :

- opérations core explicites ;
    
- inputs structurés ;
    
- outputs structurés ;
    
- warnings/errors structurés ;
    
- artifacts structurés ;
    
- provenance ;
    
- `Run` conceptuel ;
    
- `PackLock` conceptuel ;
    
- replay-readiness ;
    
- séparation stricte core/interface.
    

La V1 stricte peut avoir une interface minimale de test ou de démonstration, mais cette interface ne doit pas être définie comme une capacité core.

---

## 6.2 V1.5

V1.5 peut introduire des surfaces d’appel plus concrètes :

- CLI minimale ;
    
- SDK minimal ;
    
- API locale ou process boundary ;
    
- MCP minimal ;
    
- CSV pour measurements ;
    
- design tool adapter prototype ;
    
- CAD export prototype non-core ;
    
- agent playbooks stricts ;
    
- replay command/tool minimal.
    

Ces éléments deviennent utiles quand les opérations, artifacts, warnings et `Run` sont suffisamment stables.

---

## 6.3 Futur

À garder pour plus tard :

- plugins natifs complets ;
    
- camera app ;
    
- CAD adapters robustes ;
    
- design tool plugins complets ;
    
- API cloud ;
    
- marketplace ;
    
- pack registry public ;
    
- workflows agents avancés ;
    
- imports image/vision ;
    
- native file formats ;
    
- 3D adapters ;
    
- multi-user/cloud/project layer.
    

---

## 7. Risques d’interface leakage

## 7.1 UI qui définit les ratios

Risque : une interface ajoute “tiers”, “golden”, “3:4:5” ou “custom harmony” comme options UI et ces valeurs deviennent des vérités implicites.

Conséquence : deux interfaces peuvent produire des résultats différents pour le même système.

Protection :

> **Aucun ratio UI. Tout ratio doit venir d’un pack verrouillé.**

---

## 7.2 SVG qui devient modèle

Risque : un SVG exporté devient l’objet modifiable ou rejoué.

Conséquence : Norma commence à raisonner en traits, couleurs, layers et coordonnées de rendu au lieu de guides, zones, mesures et provenance.

Protection :

> **SVG est un visual artifact, jamais une construction source.**

---

## 7.3 Plugin qui impose sa structure

Risque : Figma, AutoCAD, Blender ou autre impose ses nodes, layers, blocks ou constraints au modèle core.

Conséquence : le core devient dépendant d’un outil externe.

Protection :

> **Les objets natifs restent externes. Ils sont traduits vers des objets Norma structurés.**

---

## 7.4 MCP qui invente des rules

Risque : un agent appelle un tool avec une phrase comme “utilise une règle harmonique adaptée” et le serveur crée une rule ad hoc.

Conséquence : résultats non reproductibles, packs contournés, replay impossible.

Protection :

> **MCP expose des opérations. Il ne crée pas de knowledge proportionnelle.**

---

## 7.5 Caméra qui impose le modèle

Risque : la caméra impose repère écran, perspective, tracking, calibration, crop ou overlay comme modèle interne.

Conséquence : le core devient dépendant d’un flux instable.

Protection :

> **La caméra produit au mieux des données structurées avec provenance et confidence. Elle ne définit pas le core.**

---

## 7.6 API qui cache un état

Risque : une API utilise un pack courant, une session, une tolérance globale ou un contexte serveur non déclaré.

Conséquence : même input apparent, output différent.

Protection :

> **Tout ce qui change le résultat doit être dans l’input, le context, le pack lock ou l’operation version.**

---

## 7.7 SDK qui duplique la logique

Risque : un SDK réimplémente une partie du core pour aider le développeur.

Conséquence : divergence entre environnements.

Protection :

> **Un SDK appelle le core ; il ne recalcule pas la vérité Norma.**

---

## 7.8 Agent qui résume trop

Risque : un agent transforme un résultat `ambiguous` ou `low confidence` en phrase positive.

Conséquence : perte de confiance, claims faux, warnings masqués.

Protection :

> **Les warnings critiques doivent être visibles dans les réponses agent et artifacts.**

---

## 8. Matrice de priorité

|Interface / adapter|Statut|Pourquoi|Risque si inclus trop tôt|
|---|---|---|---|
|Inputs/outputs structurés|V1 strict|Condition de base pour tous les clients futurs.|Core inutilisable par agents/adapters.|
|Warnings/errors structurés|V1 strict|Évite les guesses silencieux.|Interfaces masquent l’ambiguïté.|
|`Run` / `PackLock` exposables|V1 strict conceptuel|Prépare replay et audit.|Résultats non vérifiables.|
|`StructuredResultArtifact`|V1 strict|Format principal pour machines, tests, agents.|Agents/plugins lisent des exports lossy.|
|Simple visual artifact|V1 strict limité|Démo visuelle utile.|SVG-driven architecture.|
|CLI|V1.5|Bon outil d’appel/test, mais pas core.|CLI impose syntaxe et defaults trop tôt.|
|SDK|V1.5|Surface développeur utile après stabilisation des opérations.|SDK duplique ou fige trop tôt le modèle.|
|API locale/process|V1.5|Utile pour intégrations.|État caché, versioning prématuré.|
|MCP server minimal|V1.5|Rend Norma agent-callable.|Agents inventent ratios/rules si contrats faibles.|
|Agent skills/playbooks|V1.5|Encadre l’usage agent sans changer le core.|Playbooks deviennent logique métier parallèle.|
|CSV export|V1.5|Utile pour measurements tabulaires.|Perte de structure/provenance.|
|Design tool adapter prototype|V1.5 / futur|Très utile pour layouts rectangulaires.|Nodes/layers contaminent le modèle.|
|CAD adapter prototype|Futur ou V1.5 non-core|Utile pour lignes/rectangles simples.|CAD impose contraintes et formats.|
|Plugins natifs|Futur|Besoin d’un core stable avant intégration profonde.|Le plugin devient le produit.|
|Camera app|Futur|Dépend calibration, vision, tracking, overlay.|On teste la caméra au lieu du core.|
|API cloud|Futur|Distribution/exécution distante.|Cloud/state/auth contaminent le moteur.|
|Native file imports|Futur|Formats riches et spécifiques.|Le format externe devient modèle.|
|Marketplace / registry public|Futur|Distribution de packs/adapters.|Gouvernance avant format stable.|
|3D adapters|Futur|Nouveau modèle géométrique.|Explosion de scope.|

---

## 9. Questions ouvertes

À ne pas résoudre maintenant :

- forme exacte des contrats CLI ;
    
- noms exacts des commandes ou tools ;
    
- structure exacte d’un SDK ;
    
- surface publique exacte des opérations ;
    
- choix transport API ;
    
- versioning des interfaces ;
    
- versioning des tool schemas MCP ;
    
- policy d’authentification si API future ;
    
- format exact des adapter warnings ;
    
- format exact des source references externes ;
    
- niveau minimal de provenance exigé par adapter ;
    
- mapping exact Norma → SVG ;
    
- mapping exact Norma → DXF futur ;
    
- mapping exact Figma/Design tool → Norma ;
    
- mapping exact CAD → Norma ;
    
- traitement des unités CAD ;
    
- traitement des rotations importées ;
    
- traitement des masques/clips design tools ;
    
- stratégie d’import depuis image annotée ;
    
- seuils de confidence pour camera/vision future ;
    
- statut exact d’un adapter officiel vs expérimental ;
    
- séparation entre playbook agent et MCP tools ;
    
- politique d’autorisation des packs user-defined dans agents ;
    
- façon de présenter warnings critiques aux agents ;
    
- règles de replay à travers un adapter externe ;
    
- format de `SourceReference` ;
    
- stockage des artifacts et runs ;
    
- compatibilité entre versions d’adapters et versions du core.
    

---

## 10. Décisions à verrouiller

Décisions copiables dans la spec globale :

1. **Les interfaces et adapters sont des clients du core, pas le core.**
    
2. **Le core calcule ; les packs décrivent les systèmes ; les interfaces appellent ; les adapters traduisent ; les artifacts représentent.**
    
3. **Aucune interface ne doit définir des ratios, rules, scores ou résultats Norma.**
    
4. **Un adapter transforme des données externes en objets Norma structurés, appelle des opérations core, puis transforme les résultats ou artifacts vers un format cible.**
    
5. **La direction correcte est : external data → Norma structured input → core operation → Norma result → artifact → external target format.**
    
6. **Un external target format ne doit jamais devenir source de vérité du core.**
    
7. **Les objets natifs externes ne doivent pas entrer dans le modèle canonique Norma Core V1.**
    
8. **Un adapter doit conserver provenance, source externe, pertes de conversion, warnings et limitations.**
    
9. **Un adapter ne doit jamais redéfinir les rules proportionnelles.**
    
10. **Une CLI, un SDK, une API ou un serveur MCP expose Norma ; ils ne déterminent pas la logique Norma.**
    
11. **Un serveur MCP peut exposer des opérations core comme tools, mais ne doit pas inventer ratios, rules, scores ou explanations.**
    
12. **Les agents doivent utiliser des operations explicites, structured inputs, structured outputs, warnings/errors, replay, artifacts et explanations traçables.**
    
13. **Un agent ne doit jamais halluciner de ratio, rule, pack, score ou claim esthétique.**
    
14. **Les plugins, camera apps, CAD adapters et design tool adapters sont hors V1 strict.**
    
15. **V1 strict doit seulement garantir que le core est interface-ready : opérations explicites, résultats structurés, provenance, warnings/errors, artifacts, `Run`, `PackLock` et replay-readiness.**
    
16. **CLI, SDK, API locale, MCP minimal et agent playbooks sont V1.5 si les opérations publiques et artifacts sont stabilisés.**
    
17. **Camera, plugins natifs, CAD robuste, design tool plugins complets, cloud, marketplace et 3D sont futurs.**
    
18. **Toute donnée externe incomplète, ambiguë, lossy ou non replayable doit produire warning ou erreur explicite.**
    
19. **Les interfaces ne doivent jamais masquer les warnings critiques du core.**
    
20. **Aucun résultat Norma ne doit dépendre d’un état UI, d’une session, d’un viewport, d’une caméra, d’un plugin, d’un serveur ou d’un ordre de sélection externe non déclaré.**
    

---

