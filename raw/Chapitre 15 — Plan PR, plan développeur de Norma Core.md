

## 1. Verdict sur le plan PR

Le plan PR doit transformer la roadmap MVP en **séquence d’exécution développeur courte, vérifiable et non ambiguë**.

Il doit permettre de construire progressivement le moteur MVP :

```txt
guardrails
→ core skeleton
→ operation contracts
→ geometry
→ pack minimal
→ rules
→ construction
→ measurements
→ evaluation
→ comparison
→ artifacts
→ Run / PackLock / OperationContext
→ demo harness
```

Ce plan ne doit pas construire l’écosystème autour de Norma.

La spec et la roadmap verrouillent déjà que Norma Core V1 est un moteur déterministe appliquant des systèmes proportionnels versionnés à des segments 1D, surfaces rectangulaires 2D et compositions 2D simples, avec données structurées, packs, rules, constructions, measurements, evaluation, artifacts, `Run`, `PackLock`, `OperationContext`, warnings/errors et replay-readiness.

Le plan PR doit accomplir ceci :

- rendre le core exécutable par petits incréments ;
    
- stabiliser les contrats d’opération avant les interfaces ;
    
- prouver la chaîne MVP de bout en bout ;
    
- garder les artifacts dérivés ;
    
- rendre `Run`, `PackLock` et `OperationContext` visibles ;
    
- produire la démo vérité **Surface proportionnelle évaluée** ;
    
- empêcher les dérives : UI, caméra, plugin, CAD natif, cloud, marketplace, beauty score, prompt libre, SVG comme source.
    

Il ne doit pas accomplir ceci :

- produire une UI complète ;
    
- produire une caméra ou pipeline image ;
    
- produire un plugin ;
    
- produire une API cloud ;
    
- produire un SDK complet ;
    
- produire un MCP complet ;
    
- produire un CAD adapter ;
    
- produire une marketplace ;
    
- créer des packs riches ;
    
- implémenter `replayRun` complet ;
    
- faire de l’optimisation créative ;
    
- juger la beauté.
    

Phrase à verrouiller :

> **Le plan PR construit le moteur Norma Core MVP. Il ne construit pas encore les interfaces, les adapters ou l’écosystème.**

---

# 2. Principes d’exécution

## 2.1 Petits PRs

Chaque PR doit avoir :

- un objectif unique ;
    
- un scope fermé ;
    
- un hors scope explicite ;
    
- des critères d’acceptation ;
    
- un gate de validation ;
    
- des tests conceptuels ;
    
- une liste d’erreurs à éviter.
    

Un PR ne doit pas devenir une phase complète de produit. Il doit être assez petit pour être relu et validé.

---

## 2.2 Pas de UI

Aucun PR MVP ne doit introduire :

- écran ;
    
- canvas interactif ;
    
- drag-and-drop ;
    
- thème ;
    
- sélection visuelle ;
    
- layout editor ;
    
- workflow utilisateur riche.
    

Le MVP peut produire un **simple visual artifact**, mais ce visual artifact est une projection dérivée, jamais la source du résultat.

---

## 2.3 Pas de caméra, image, vision, plugin ou CAD natif

Ces sujets restent hors MVP.

La démo MVP doit utiliser uniquement des données géométriques structurées et rester sans caméra, image, OpenCV, tracking, plugin, CAD natif, cloud ou marketplace.

---

## 2.4 Pas de pack riche

Le MVP utilise un seul pack minimal :

```txt
norma.basic-proportions@0.1.0
```

Il doit couvrir seulement :

- `1/2`;
    
- `1/3`;
    
- `2/3`;
    
- `1:1:1`;
    
- thirds ;
    
- halves ;
    
- rule set minimal de grille de tiers.
    

Tout pack riche est post-MVP.

---

## 2.5 Pas de scoring avant measurements

Aucun score ne doit exister avant que les measurements sources existent.

La règle déjà verrouillée est stricte :

```txt
Measurement = fait calculé
Evaluation  = lecture structurée
Score       = résumé
Decision    = conclusion
Explanation = justification traçable
```

Le score ne doit pas remplacer l’evaluation.

Norma ne doit pas évaluer la beauté ou l’intention.

---

## 2.6 Pas d’artifact avant source objects

Un artifact ne doit jamais créer la vérité.

La vérité Norma reste dans les objets structurés du core :

- `Construction`;
    
- `Measurement`;
    
- `Evaluation`;
    
- `Decision`;
    
- `Run`;
    
- pack ;
    
- versions.
    

Un artifact est une projection de cette vérité.

S’il contredit l’objet source, l’objet source gagne.

---

## 2.7 Pas de `replayRun` complet avant replay-readiness

Le MVP doit produire :

- `Run` visible ;
    
- `PackLock` visible ;
    
- `OperationContext` visible ;
    
- idempotence ;
    
- mismatch policy ;
    
- deterministic ordering ;
    
- replay-readiness.
    

Mais `replayRun`, `verifyRun` et `verifyArtifactFreshness` restent V1.5.

La spec consolidée verrouille cette distinction.

---

## 2.8 Chaque PR doit avoir un critère de fin clair

Un PR n’est terminé que si :

- son scope est atteint ;
    
- son hors scope n’a pas été violé ;
    
- ses outputs sont structurés ;
    
- ses warnings/errors sont présents si nécessaire ;
    
- sa provenance est conservée si un objet dérivé est produit ;
    
- ses gates passent.
    

---

## 2.9 Provenance minimale obligatoire dès PR6

`Run`, `PackLock` et `OperationContext` sont finalisés en PR11, mais ils sont prévus dès PR1/PR2.

À partir de PR6, aucun objet dérivé ne peut être produit sans provenance minimale, même si `Run` n’est pas encore finalisé.

Cela concerne :

- guides ;
    
- zones ;
    
- grid cells ;
    
- diagonales ;
    
- intersections ;
    
- measurements ;
    
- evaluations ;
    
- decisions ;
    
- explanations ;
    
- artifacts.
    

Objectif : éviter que PR11 devienne un gros refactor de provenance.

---

# 3. Plan PR recommandé

La séquence recommandée suit l’ordre de la roadmap MVP :

```txt
spec
→ operation contracts
→ geometry
→ pack
→ rules
→ construction
→ measurements
→ evaluation
→ comparison
→ artifacts
→ Run / replay-readiness
→ demo harness
```

|PR|Titre|But|
|--:|---|---|
|PR0|Spec freeze / project guardrails|Verrouiller les règles d’exécution MVP.|
|PR1|Core skeleton|Poser le squelette minimal du core sans logique métier lourde.|
|PR2|Operation contracts and canonical variables|Stabiliser comment une opération est appelée et ce qu’elle retourne.|
|PR3|Geometry model V1|Poser `SegmentSpace`, `SurfaceSpace`, `Composition2D` et primitives V1.|
|PR4|Minimal ratio pack model|Poser `RatioPack`, ratios, sequences et pack minimal.|
|PR5|Rule declarations and rule resolution|Poser rule declarations, rule types supportés et résolution de rule set.|
|PR6|Construction generation|Produire guides, zones, grille, diagonales, intersections.|
|PR7|Measurements|Mesurer distances, positions, aires, containment, overlap, coverage.|
|PR8|Evaluation profile and scoring minimal|Évaluer une composition selon measurements/profile/pack/tolérances.|
|PR9|Comparison and decision|Comparer A/B et produire decision/explanation traçable.|
|PR10|Artifacts|Produire artifacts structurés et visual artifact simple dérivé.|
|PR11|Run, PackLock, OperationContext|Finaliser replay-readiness, identité et contexte effectif.|
|PR12|MVP demo harness|Assembler la démo vérité “Surface proportionnelle évaluée”.|

## Ajustement important

`Run`, `PackLock` et `OperationContext` apparaissent formellement en PR11, mais leurs **références minimales doivent être prévues dès PR1/PR2**.

Sinon, il faudra réécrire toutes les opérations plus tard.

Donc :

- PR1 crée les placeholders conceptuels ;
    
- PR2 les inscrit dans le contrat d’opération ;
    
- PR6 commence à imposer la provenance minimale sur les objets dérivés ;
    
- PR11 les finalise comme enveloppe de reproductibilité.
    

---

# 4. Plan détaillé par PR

---

## PR0 — Spec freeze / project guardrails

### Objectif

Verrouiller les règles qui empêchent le MVP de dériver.

### Scope exact

- Définition MVP.
    
- Liste V1 strict.
    
- Liste hors MVP.
    
- Règles anti-dérive.
    
- Gates PR.
    
- Glossaire court des objets critiques.
    
- Référence aux ADRs fondateurs.
    
- Définition de la démo cible.
    
- Section explicite : `Blocked capabilities for MVP`.
    

### Blocked capabilities for MVP

Les capacités suivantes sont interdites dans le MVP :

- UI complète ;
    
- écran ;
    
- canvas interactif ;
    
- drag-and-drop ;
    
- caméra ;
    
- image ;
    
- vision ;
    
- OpenCV ;
    
- tracking ;
    
- plugin ;
    
- CAD natif ;
    
- cloud ;
    
- marketplace ;
    
- prompt libre comme source ;
    
- beauty score ;
    
- SVG comme modèle ;
    
- export comme source de vérité ;
    
- adapter comme source de logique Norma ;
    
- agent-created rules ;
    
- pack implicite ;
    
- ratio implicite ;
    
- tolérance cachée ;
    
- recommendation créative ;
    
- optimisation automatique ;
    
- inférence d’intention.
    

### Hors scope

- code ;
    
- architecture d’interface ;
    
- CLI ;
    
- SDK ;
    
- MCP ;
    
- UI ;
    
- formats exacts ;
    
- algorithmes ;
    
- tickets détaillés.
    

### Livrables attendus

- document de guardrails MVP ;
    
- checklist PR ;
    
- liste des capacités interdites ;
    
- définition de “PR terminé” ;
    
- critères anti-beauty ;
    
- critères anti-SVG-source ;
    
- critères anti-pack-implicit.
    

### Zones conceptuelles probables

- documentation normative ;
    
- ADR index ;
    
- checklist de validation ;
    
- notes de scope MVP.
    

### Critères d’acceptation

- Le scope V1 strict est lisible.
    
- Les exclusions sont explicites.
    
- Le scénario MVP est nommé : **Surface proportionnelle évaluée**.
    
- Le plan interdit caméra, image, plugin, CAD natif, UI complète, cloud, marketplace.
    
- Les décisions ouvertes ne sont pas utilisées comme décisions implicites.
    
- Les capacités bloquées sont listées avec des mots exacts utilisables en review.
    

### Tests conceptuels à prévoir

- Revue : “ce PR autorise-t-il une UI ?” → non.
    
- Revue : “ce PR autorise-t-il caméra/image ?” → non.
    
- Revue : “ce PR autorise-t-il beauty score ?” → non.
    
- Revue : “ce PR exige-t-il outputs structurés avant visual artifact ?” → oui.
    
- Revue : “ce PR autorise-t-il SVG comme modèle ?” → non.
    
- Revue : “ce PR autorise-t-il pack implicite ?” → non.
    

### Risques

- Trop de documentation.
    
- Guardrails trop vagues.
    
- Confusion entre roadmap et plan PR.
    

### Erreurs à éviter

- Transformer PR0 en spec complète réécrite.
    
- Ajouter des décisions produit futures.
    
- Ouvrir les sujets CLI/SDK/MCP.
    

### Dépendances

Aucune.

### Gate de validation

**Guardrail gate** : aucun PR suivant ne peut inclure une capacité explicitement hors MVP.

Aucun PR suivant ne peut introduire UI, caméra, image, plugin, CAD natif, cloud, marketplace, prompt libre comme source, beauty score ou SVG comme modèle.

---

## PR1 — Core skeleton

### Objectif

Créer le squelette minimal du core pour accueillir les objets et opérations futures sans implémenter encore la logique géométrique complète.

PR1 doit créer un noyau vide mais strict, capable d’accueillir les objets futurs sans laisser entrer UI, caméra, plugin, formats natifs, prompts libres ou résultats non structurés.

### Scope exact

- Frontière conceptuelle du core.
    
- Types ou structures minimales d’identification.
    
- Status minimal.
    
- Error/warning minimal.
    
- Provenance minimale.
    
- Operation registry vide ou minimal.
    
- Placeholders conceptuels pour `Run`, `PackLock`, `OperationContext`.
    
- Documentation courte : “ce que le skeleton autorise / interdit”.
    

### Diagnostics obligatoires dès PR1

PR1 doit inclure ces erreurs/warnings minimaux comme obligatoires :

- `MissingOperation`;
    
- `UnsupportedOperation`;
    
- `NotImplemented`;
    
- `InvalidInputShape`;
    
- `CriticalWarningNotSuppressible`;
    
- `MissingProvenance`.
    

Ces diagnostics ne sont pas optionnels.

### Hors scope

- calcul géométrique ;
    
- ratio pack complet ;
    
- construction ;
    
- measurements ;
    
- scoring ;
    
- artifacts ;
    
- demo harness ;
    
- UI ;
    
- adapters ;
    
- replayRun.
    

### Livrables attendus

- squelette de domaine core ;
    
- conventions de naming ;
    
- liste des capacités futures ;
    
- stubs conceptuels d’opérations ;
    
- statuts de base ;
    
- erreurs/warnings de base ;
    
- documentation minimale.
    

### Zones conceptuelles probables

- core domain ;
    
- core operations shell ;
    
- diagnostics ;
    
- provenance ;
    
- runtime placeholders ;
    
- documentation de skeleton.
    

### Critères d’acceptation

- Le core peut représenter un résultat vide ou non implémenté avec `status`, `warnings`, `errors`, `provenance`.
    
- Le skeleton ne contient aucune dépendance UI/caméra/plugin/cloud.
    
- Les stubs ne prétendent pas produire de construction ou measurement réelle.
    
- Les placeholders `Run`, `PackLock`, `OperationContext` existent au niveau conceptuel.
    
- Les erreurs “unsupported operation” ou “not implemented” sont structurées.
    
- Les diagnostics obligatoires PR1 existent.
    
- Le skeleton peut échouer proprement.
    
- Le skeleton ne produit aucun faux résultat.
    

### Tests conceptuels à prévoir

- Appel sans opération → `MissingOperation`.
    
- Appel d’une opération inconnue → `UnsupportedOperation`.
    
- Appel d’une opération stub → `NotImplemented`, pas résultat inventé.
    
- Input mal formé → `InvalidInputShape`.
    
- Warning critique → ne peut pas être supprimé par le shell.
    
- Résultat dérivé sans provenance → `MissingProvenance`.
    
- Tentative d’ajouter un objet UI → refus par guardrail.
    

### Risques

- Skeleton trop abstrait.
    
- Skeleton qui fige déjà une API finale.
    
- Stub qui retourne un faux succès.
    
- Runtime placeholders oubliés.
    

### Erreurs à éviter

- Ajouter des calculs prématurés.
    
- Ajouter un format JSON final rigide.
    
- Ajouter un rendu.
    
- Ajouter un fichier image, SVG source, ou exemple visuel comme vérité.
    
- Nommer des concepts avec des termes vagues comme `data`, `config`, `result` sans type.
    

### Dépendances

- PR0.
    

### Gate de validation

**Core skeleton gate** : le core doit pouvoir retourner un résultat structuré minimal sans calculer ni inventer.

Le skeleton peut échouer proprement, mais ne peut pas produire de faux résultat.

---

## PR2 — Operation contracts and canonical variables

### Objectif

Stabiliser le contrat conceptuel d’appel et de résultat des opérations avant toute opération réelle.

Les observations de vérification ont identifié que la spec devait verrouiller :

- le contrat minimal d’appel ;
    
- les variables canoniques obligatoires ;
    
- les statuts de résultat ;
    
- la séparation entre contrat conceptuel et schéma JSON/API final.
    

PR2 est critique. C’est probablement le PR le plus important après PR0.

### Scope exact

- `Operation Call Contract`.
    
- `Operation Result Contract`.
    
- Variables canoniques.
    
- Status taxonomy minimale.
    
- Error/warning shape.
    
- Validation levels.
    
- Registry conceptuel des opérations V1.
    
- Règle : une operation peut être orchestratrice, mais jamais opaque.
    
- Règle : `Any default that changes output must be explicit, versioned, or rejected`.
    

### Contrat d’appel

Chaque appel d’opération significatif doit pouvoir porter :

- `operation`;
    
- `operationVersion`;
    
- `input`;
    
- `operationContext`;
    
- `packLock` si pack utilisé ;
    
- `ruleRefs` ou `ruleSetRef` si rules ;
    
- `evaluationProfileRef` si evaluation ;
    
- `tolerances` si mesure/comparaison ;
    
- `coordinateSystem` si géométrie ;
    
- `metricPolicy` si mesures ;
    
- `requestedOutputs`;
    
- `requestedArtifacts`;
    
- `featureFlags` si effet sur résultat.
    

### Contrat de résultat

Chaque résultat doit pouvoir porter :

- `status`;
    
- `run` ou `runRef`;
    
- `result` ou `outputRefs`;
    
- `warnings`;
    
- `errors`;
    
- `provenance`;
    
- `packLock` effectif si applicable ;
    
- `operationContext` effectif ;
    
- `artifactRefs` si artifacts produits ;
    
- `explanationRefs` si explanations produites.
    

### Hors scope

- géométrie réelle ;
    
- pack réel ;
    
- construction réelle ;
    
- measurements ;
    
- scoring ;
    
- CLI/SDK/API/MCP ;
    
- schéma JSON final ;
    
- transport HTTP ;
    
- serialization complète.
    

### Livrables attendus

- contrat d’appel conceptuel ;
    
- contrat de résultat conceptuel ;
    
- dictionnaire des variables ;
    
- status génériques ;
    
- validation levels ;
    
- shape `Error` / `Warning`.
    

### Zones conceptuelles probables

- operation contracts ;
    
- diagnostics ;
    
- validation ;
    
- operation registry ;
    
- canonical variables.
    

### Critères d’acceptation

Chaque appel d’opération significatif doit pouvoir porter les champs du contrat d’appel.

Chaque résultat doit pouvoir porter les champs du contrat de résultat.

Aucune opération publique ne peut accepter :

- prompt libre comme source ;
    
- pack implicite ;
    
- tolérance cachée ;
    
- état UI ;
    
- objet natif externe comme source.
    

Tout default qui change l’output doit être :

- explicite ;
    
- versionné ;
    
- ou rejeté.
    

### Tests conceptuels à prévoir

- Operation sans `operationVersion` → erreur ou warning critique.
    
- Pack implicite demandé → erreur.
    
- Tolérance cachée → erreur.
    
- Prompt libre comme input → erreur.
    
- Résultat sans warnings/errors arrays → invalide.
    
- Résultat sans provenance pour output dérivé → invalide.
    
- Default qui change l’output mais n’est pas explicite/versionné → erreur.
    

### Risques

- Confondre contrat conceptuel et API finale.
    
- Trop retarder les variables obligatoires.
    
- Laisser les clients futurs inventer leur propre contrat.
    

### Erreurs à éviter

- Accepter `prompt` comme substitut d’input structuré.
    
- Accepter `config` vague comme contexte.
    
- Retourner un simple booléen de succès.
    
- Masquer warnings/errors.
    
- Cacher des defaults qui changent l’output.
    

### Dépendances

- PR0 ;
    
- PR1.
    

### Gate de validation

**Operation contract gate** : aucune opération future ne peut être ajoutée si elle ne respecte pas le call/result contract.

Aucune opération publique ne peut accepter prompt libre, pack implicite, tolérance cachée, état UI ou objet natif externe comme source.

---

## PR3 — Geometry model V1

### Objectif

Poser le modèle géométrique V1 minimal : petit, rectangulaire, explicite, mesurable et reproductible.

Le modèle géométrique V1 doit utiliser :

- segments 1D ;
    
- surfaces rectangulaires 2D ;
    
- compositions simples ;
    
- coordonnées normalisées ;
    
- métrique explicite.
    

Il exclut :

- 3D ;
    
- polygones complexes ;
    
- courbes ;
    
- image ;
    
- tracking caméra ;
    
- géométrie CAD avancée.
    

### Scope exact

- `SegmentSpace`.
    
- `SurfaceSpace`.
    
- `Composition2D`.
    
- `CoordinateSystem`.
    
- `MetricPolicy`.
    
- `TolerancePolicy`.
    
- `Point`.
    
- `Segment`.
    
- `Line` limitée.
    
- `Rect` axis-aligned.
    
- `Anchor`.
    
- `Element` rectangulaire.
    

### Hors scope

- rotations ;
    
- polygones ;
    
- courbes ;
    
- 3D ;
    
- image regions ;
    
- CAD objects ;
    
- layers natifs ;
    
- rendering ;
    
- visual artifact ;
    
- measurements avancées ;
    
- construction.
    

### Livrables attendus

- modèle géométrique V1 minimal ;
    
- validation géométrique structurale ;
    
- repère Norma canonique ;
    
- règles de rejet hors V1 ;
    
- exemples canoniques : segment, surface `1200 × 800`, composition avec rectangles.
    

### Zones conceptuelles probables

- geometry model ;
    
- coordinate policies ;
    
- metric/tolerance policies ;
    
- composition model ;
    
- geometry validation.
    

### Critères d’acceptation

- Une `SurfaceSpace` rectangulaire peut être représentée.
    
- Une `Composition2D` simple peut contenir des rectangles.
    
- Les coordonnées normalisées sont séparées des mesures métriques.
    
- Le repère est explicite.
    
- Une géométrie hors V1 est rejetée ou marquée unsupported.
    
- Aucun objet image, CAD natif ou UI n’entre dans le core.
    
- Aucune géométrie n’est acceptée sans coordinate system explicite.
    

### Tests conceptuels à prévoir

- Surface `1200 × 800` valide.
    
- Rectangle normalisé dans `[0,1]` valide.
    
- Rectangle avec rotation → rejet.
    
- Polygone → rejet.
    
- Image comme geometry → rejet.
    
- Coordonnées sans coordinate system → erreur.
    
- `normalized coordinates ≠ metric measurements`.
    

Un point normalisé peut être valide, mais une distance, une aire ou un angle doit déclarer sa métrique.

### Risques

- Laisser entrer trop de géométrie.
    
- Confondre `SurfaceSpace` avec canvas/rendu.
    
- Confondre coordonnées normalisées et pixels.
    
- Confondre coordonnées normalisées et measurements métriques.
    

### Erreurs à éviter

- Ajouter style, couleur, layer ou font.
    
- Accepter rectangle tourné “pour plus tard”.
    
- Ajouter import depuis fichier externe.
    
- Mesurer sans metric policy.
    

### Dépendances

- PR0 ;
    
- PR1 ;
    
- PR2.
    

### Gate de validation

**Geometry gate** : aucune construction ne peut être produite tant que la surface, le repère et les primitives V1 ne sont pas stables.

Aucune géométrie sans coordinate system explicite.

Aucune image, aucun layer natif, aucun objet CAD natif.

---

## PR4 — Minimal ratio pack model

### Objectif

Créer le modèle minimal de pack proportionnel et le pack MVP :

```txt
norma.basic-proportions@0.1.0
```

Les packs doivent contenir :

- ratios ;
    
- ratio families ;
    
- ratio sequences ;
    
- partition patterns ;
    
- rule declarations ;
    
- rule sets ;
    
- conventions ;
    
- metadata ;
    
- provenance ;
    
- compatibility ;
    
- limits.
    

Ils ne doivent pas contenir :

- code client ;
    
- UI ;
    
- rendu ;
    
- plugin ;
    
- caméra ;
    
- modèle IA ;
    
- scoring esthétique universel.
    

### Scope exact

- `RatioPack`.
    
- `Ratio`.
    
- `RatioFamily`.
    
- `RatioSequence`.
    
- `PartitionPattern` minimal.
    
- Metadata.
    
- Provenance.
    
- Compatibility.
    
- Limits.
    
- Pack validation conceptuelle.
    
- Pack minimal :
    
    - `1/2`;
        
    - `1/3`;
        
    - `2/3`;
        
    - `1:1:1`;
        
    - `halves`;
        
    - `thirds`.
        
- Rule set minimal déclaré dans le pack :
    

```txt
surface-basic-third-grid
```

- Début de `PackLock` conceptuel ou pré-lock.
    

### Hors scope

- pack registry ;
    
- signatures ;
    
- packs riches ;
    
- golden ratio ;
    
- Modulor ;
    
- root rectangles riches ;
    
- user-defined packs ;
    
- marketplace ;
    
- external pack distribution ;
    
- packs historiques ;
    
- packs expérimentaux.
    

### Livrables attendus

- modèle pack minimal ;
    
- pack MVP ;
    
- validation de ratio ;
    
- validation de sequence ;
    
- limites no beauty / no intention ;
    
- pack identity conceptuelle ;
    
- début de `PackLock` ou placeholder ;
    
- rule set minimal déclaré, sans exécution complète.
    

### Zones conceptuelles probables

- proportional system model ;
    
- pack validation ;
    
- pack fixture MVP ;
    
- ratio sequence normalization ;
    
- pack metadata.
    

### Critères d’acceptation

- Le pack minimal est validable.
    
- `1:1:1` est une `RatioSequence`, pas trois ratios indépendants.
    
- Ratio absent → erreur.
    
- Pack sans version → erreur.
    
- Pack sans identity conceptuelle → warning critique ou erreur selon policy.
    
- Pack sans `contentIdentity` → warning critique ou erreur selon policy.
    
- Pack contenant une claim beauté → rejet.
    
- Aucun ratio utilisé hors pack.
    
- Aucun ratio hardcodé dans le core.
    

### Tests conceptuels à prévoir

- Résoudre `1/3` → succès.
    
- Résoudre `2/3` → succès.
    
- Résoudre `1:1:1` → parts normalisées.
    
- Résoudre ratio absent → erreur.
    
- Ratio duplicate → erreur.
    
- Rule references missing ratio → erreur.
    
- Pack with beauty claim → rejet.
    
- Pack without contentIdentity → warning critique ou erreur.
    
- Pack avec UI/style → rejet.
    
- Pack avec “rend beau” → rejet.
    

### Risques

- Hardcoder les ratios dans le core.
    
- Autoriser les clients à injecter des ratios.
    
- Confondre `Ratio` et `RatioSequence`.
    
- Transformer le pack en preset UI.
    

### Erreurs à éviter

- Transformer le pack en config UI.
    
- Ajouter un pack riche trop tôt.
    
- Ajouter un score esthétique dans le pack.
    
- Mettre des ratios dans le core.
    
- Mettre des ratios dans les clients.
    

### Dépendances

- PR0 ;
    
- PR1 ;
    
- PR2.
    

### Gate de validation

**Pack gate** : aucune construction proportionnelle ne peut être générée avec un ratio absent du pack.

Aucun ratio utilisé hors pack.

Aucun ratio hardcodé dans le core.

Pack absent = erreur.

Ratio absent = erreur.

Content identity absente = warning critique ou erreur.

---

## PR5 — Rule declarations and rule resolution

### Objectif

Stabiliser la séparation entre rule declarations dans les packs et rule types exécutables par le core.

Décision normative :

```txt
rule declarations vivent dans les packs
rule types et algorithmes d’exécution vivent dans le core
```

Le pack déclare quoi appliquer.

Le core exécute seulement les rule types supportés.

### Scope exact

- `RuleDeclaration`.
    
- `Rule`.
    
- `RuleType`.
    
- `RuleSet`.
    
- `RuleRef`.
    
- Rule type registry V1.
    
- `resolveRuleSet`.
    
- `resolveRatio`.
    
- `resolveRatioSequence`.
    
- Compatibility rule type.
    
- Warnings/errors pour rule unsupported.
    
- Validation rule → pack refs.
    
- Validation rule type supported/unsupported.
    
- Compatibility V1.
    

Rule set MVP :

```txt
surface-basic-third-grid
```

Rule types MVP :

- `divideSurfaceVertical`;
    
- `divideSurfaceHorizontal`;
    
- `createGuidesFromCandidates`;
    
- `createSimpleGrid`;
    
- `createDiagonals`;
    
- `deriveIntersections`.
    

### Sortie obligatoire de résolution

PR5 doit produire une trace minimale de résolution :

```txt
resolvedRuleSet =
  ruleSetRef
  + orderedRules
  + resolvedRatioRefs
  + unsupportedRules
  + warnings
```

Cette trace évite que PR6 reconstruise ou devine la logique de résolution.

### Hors scope

- construction réelle complète ;
    
- génération complète des guides ;
    
- zones ;
    
- grid ;
    
- measurements ;
    
- evaluation ;
    
- scoring ;
    
- plugin rules ;
    
- user-defined rule language ;
    
- rule code dans pack ;
    
- agent-created rules ;
    
- UI preset.
    

### Livrables attendus

- modèle rule declaration ;
    
- résolution de rule set ;
    
- mapping declaration → rule type ;
    
- errors/warnings de compatibilité ;
    
- rule provenance ;
    
- trace minimale de résolution.
    

### Zones conceptuelles probables

- rule model ;
    
- rule resolution ;
    
- pack compatibility ;
    
- operation registry integration ;
    
- diagnostics.
    

### Critères d’acceptation

- Le rule set MVP est résolvable.
    
- Une rule sans type supporté est rejetée ou warning critique.
    
- Une rule absente du pack est rejetée.
    
- Une interface ou agent ne peut pas créer une rule ad hoc.
    
- La résolution conserve provenance pack/rule.
    
- Une rule declaration sans ratio/rule type/support explicite échoue.
    
- Un rule type unsupported retourne error/warning de compatibilité.
    
- `resolvedRuleSet` contient la trace minimale requise.
    

### Tests conceptuels à prévoir

- Résoudre `surface-basic-third-grid` → succès.
    
- Rule type unsupported → erreur.
    
- Rule sans ratio requis → erreur.
    
- Rule declaration avec code client → rejet.
    
- Rule inventée par prompt → rejet.
    
- Rule declaration sans support explicite → erreur/warning critique.
    
- Résolution sans `resolvedRuleSet` traçable → invalide.
    

### Risques

- Mettre les algorithmes dans le pack.
    
- Hardcoder le système de tiers dans le core.
    
- `RuleSet` qui devient preset UI.
    
- PR6 qui reconstruit la logique de résolution.
    

### Erreurs à éviter

- Exécuter une rule non résolue.
    
- Appliquer une rule sans pack source.
    
- Cacher une rule unsupported comme warning faible.
    
- Laisser une interface, un adapter ou un agent inventer une rule.
    

### Dépendances

- PR2 ;
    
- PR4.
    

### Gate de validation

**Rule resolution gate** : aucune construction ne peut être produite sans rule declaration résolue et rule type supporté.

Une rule declaration sans ratio/rule type/support explicite échoue.

Un rule type unsupported retourne error/warning de compatibilité.

---

## PR6 — Construction generation

### Objectif

Produire la construction proportionnelle source de la démo :

- guides ;
    
- zones ;
    
- grille ;
    
- diagonales ;
    
- intersections.
    

Une `Construction` est le résultat structuré produit quand Norma applique des rules à un espace.

Elle n’est pas :

- un export ;
    
- une measurement ;
    
- une evaluation ;
    
- un rendu ;
    
- un SVG.
    

### Scope exact

- `Construction`.
    
- `Guide`.
    
- `Zone`.
    
- `Grid`.
    
- `GridCell`.
    
- `IntersectionPoint`.
    
- `generateConstruction`.
    
- `generateGuides`.
    
- `generateZones`.
    
- `generateSimpleGrid`.
    
- `generateDiagonals`.
    
- `deriveIntersections`.
    
- Trace rule → output object.
    
- `constructionTrace`.
    

### Sortie MVP attendue

Pour une surface rectangulaire :

- guides `x=1/3`, `x=1/2`, `x=2/3`;
    
- guides `y=1/3`, `y=1/2`, `y=2/3`;
    
- zones de tiers ;
    
- grille `3 × 3`;
    
- 9 cells ;
    
- deux diagonales ;
    
- intersection centrale ;
    
- intersections guide-guide ;
    
- intersections guide-border ;
    
- provenance de chaque objet dérivé.
    

### Sortie obligatoire : `constructionTrace`

Contenu minimal :

- `appliedRuleRefs`;
    
- `operationRefs`;
    
- `createdObjectRefs`;
    
- `warnings`.
    

### Règle de provenance PR6

À partir de PR6, chaque objet dérivé doit référencer au minimum :

- input ;
    
- pack ;
    
- rule ;
    
- operation.
    

Cette règle s’applique même si `Run`, `PackLock` et `OperationContext` ne sont finalisés qu’en PR11.

### Hors scope

- measurements avancées ;
    
- measurement A/B ;
    
- scoring ;
    
- artifacts ;
    
- SVG ;
    
- UI ;
    
- rendu ;
    
- interaction ;
    
- pattern detection riche ;
    
- CAD export ;
    
- recommendation ;
    
- polygones.
    

### Livrables attendus

Pour une surface rectangulaire :

- guides `x=1/3`, `x=1/2`, `x=2/3`;
    
- guides `y=1/3`, `y=1/2`, `y=2/3`;
    
- zones de tiers ;
    
- grille `3 × 3`;
    
- 9 cells ;
    
- deux diagonales ;
    
- intersection centrale ;
    
- intersections guide-guide ;
    
- intersections guide-border ;
    
- provenance de chaque objet dérivé ;
    
- `constructionTrace`.
    

### Zones conceptuelles probables

- construction model ;
    
- guide generation ;
    
- zone generation ;
    
- grid generation ;
    
- intersection derivation ;
    
- construction provenance.
    

### Critères d’acceptation

- La construction peut être générée depuis le pack/rule set MVP.
    
- Chaque guide référence sa rule source.
    
- Chaque zone référence ses guides sources.
    
- Chaque intersection référence ses géométries sources.
    
- Chaque objet dérivé référence input + pack + rule + operation.
    
- `generateConstruction` expose sa trace.
    
- `generateConstruction` ne doit jamais être opaque.
    
- Aucun SVG n’est produit comme source.
    

### Tests conceptuels à prévoir

- Surface `1200×800`, thirds → guides attendus.
    
- `1:1:1` vertical/horizontal → grid `3×3`.
    
- Diagonales → intersection centrale.
    
- Guide-guide intersections → succès.
    
- Guide-border intersections → succès.
    
- Rule manquante → erreur.
    
- Unsupported geometry → erreur.
    
- Trace absente → invalide.
    
- Objet dérivé sans provenance minimale → invalide.
    

### Risques

- `generateConstruction` devient boîte noire.
    
- La grille devient le modèle entier.
    
- Les objets dérivés manquent de provenance.
    
- PR11 devient un refactor massif de provenance.
    

### Erreurs à éviter

- Produire des guides sans source rule.
    
- Utiliser un rendu comme construction.
    
- Arrondir `1/3` en valeur source sans conserver l’origine.
    
- Produire un objet dérivé sans input/pack/rule/operation.
    

### Dépendances

- PR3 ;
    
- PR4 ;
    
- PR5.
    

### Gate de validation

**Construction gate** : la construction est acceptée seulement si chaque objet dérivé est traçable vers input + pack + rule + operation.

`generateConstruction` ne doit jamais être opaque.

---

## PR7 — Measurements

### Objectif

Mesurer la construction et les compositions A/B sans produire encore de score.

PR7 doit interdire toute evaluation.

### Scope exact

- `Measurement`.
    
- `DistanceMeasurement`.
    
- `PositionMeasurement`.
    
- `AlignmentMeasurement`.
    
- `AreaMeasurement`.
    
- `RatioMeasurement`.
    
- `AngleMeasurement`.
    
- `ContainmentMeasurement`.
    
- `OverlapMeasurement`.
    
- `CoverageMeasurement`.
    
- `DirectionalRelation` minimal.
    
- `SurfaceHierarchy` minimal.
    
- `measureGeometry`.
    
- `measureAreas`.
    

### Interdiction explicite

PR7 ne doit produire aucun `ComponentScore`.

Le PR peut produire des écarts mesurés, mais pas encore de score.

```txt
No componentScore in PR7.
```

### Hors scope

- score ;
    
- component score ;
    
- evaluation ;
    
- comparison ;
    
- decision ;
    
- beauty ;
    
- intention ;
    
- recommendation ;
    
- perception avancée.
    

### Livrables attendus

- Measurements pour composition A.
    
- Measurements pour composition B.
    
- Distances aux guides.
    
- Alignements bords/centres.
    
- Aires.
    
- Containment.
    
- Overlap.
    
- Coverage.
    
- Warnings pour gaps/overlaps/hors tolérance.
    
- Provenance measurement.
    

### Zones conceptuelles probables

- measurement model ;
    
- geometry measurement operations ;
    
- area measurement operations ;
    
- relation derivation ;
    
- measurement diagnostics.
    

### Critères d’acceptation

- Chaque measurement référence ses inputs.
    
- Chaque measurement déclare unité/normalisation.
    
- Chaque measurement déclare metric/tolerance policy.
    
- Aucune measurement ne contient jugement ou score.
    
- Aucun `ComponentScore` n’existe en PR7.
    
- Une géométrie invalide produit error/warning structuré.
    
- Aucune evaluation ne peut être produite sans measurements traçables.
    

### Tests conceptuels à prévoir

- Distance d’un bord à `x=1/3`.
    
- Alignment d’un rectangle avec un guide.
    
- Aire relative d’un rectangle.
    
- Overlap entre deux rectangles.
    
- Coverage d’une zone par elements.
    
- Measurement sans source geometry → erreur.
    
- Measurement sans metric policy → erreur.
    
- Tentative de produire `ComponentScore` en PR7 → rejet.
    

### Risques

- Glisser vers scoring.
    
- Mélanger mesure et jugement.
    
- Oublier la tolérance.
    
- Introduire un score sous forme cachée.
    

### Erreurs à éviter

- “Bonne composition” dans une measurement.
    
- Calculer un score de proximité ici.
    
- Mesurer sans contexte métrique.
    
- Ajouter `ComponentScore`.
    

### Dépendances

- PR2 ;
    
- PR3 ;
    
- PR6.
    

### Gate de validation

**Measurement gate** : aucune evaluation ne peut être produite sans measurements traçables.

Aucun score avant measurements.

Aucun `ComponentScore` en PR7.

---

## PR8 — Evaluation profile and scoring minimal

### Objectif

Évaluer une composition simple selon un profile explicite, sans comparison A/B encore.

Un `EvaluationProfile` définit comment lire des measurements.

Il ne définit pas :

- les ratios ;
    
- les rules ;
    
- les measurements ;
    
- les claims esthétiques universels.
    

### Scope exact

- `EvaluationProfile`.
    
- `Evaluation`.
    
- `ComponentScore`.
    
- `Score` minimal.
    
- `Confidence`.
    
- `evaluateCompositionBasic`.
    
- Profile MVP `basic-grid-alignment`.
    

Components MVP :

- `guide_proximity`;
    
- `alignment`;
    
- `containment`;
    
- `overlap_penalty`;
    
- `coverage_match`;
    
- `area_ratio_match`.
    

### Erreurs obligatoires PR8

PR8 doit inclure ces erreurs :

- `MissingMeasurements`;
    
- `MissingEvaluationProfile`;
    
- `MissingPackLock`;
    
- `MissingTolerancePolicy`;
    
- `BeautyScoreRejected`;
    
- `IntentInferenceRejected`.
    

### Hors scope

- comparison A/B ;
    
- global ranking riche ;
    
- recommendations ;
    
- optimization ;
    
- multi-pack evaluation ;
    
- beauty score ;
    
- intention claim.
    

### Livrables attendus

Profile MVP avec components :

- `guide_proximity`;
    
- `alignment`;
    
- `containment`;
    
- `overlap_penalty`;
    
- `coverage_match`;
    
- `area_ratio_match`.
    

Evaluation pour A et B :

- component scores ;
    
- score résumé si autorisé ;
    
- confidence séparée ;
    
- status ;
    
- warnings ;
    
- measurements sources.
    

### Zones conceptuelles probables

- evaluation model ;
    
- profile model ;
    
- scoring components ;
    
- confidence policy ;
    
- evaluation diagnostics.
    

### Critères d’acceptation

- Evaluation impossible sans measurements.
    
- Evaluation impossible sans profile.
    
- Evaluation impossible sans pack.
    
- Evaluation impossible sans `PackLock`.
    
- Evaluation impossible sans tolerances.
    
- Evaluation impossible sans `TolerancePolicy`.
    
- Score impossible sans evaluation.
    
- Confidence séparée du score.
    
- Aucun beauty score.
    
- Aucune inférence d’intention.
    

### Tests conceptuels à prévoir

- A proche → `match` ou `near_match`.
    
- B moins proche → score plus faible.
    
- Measurements absentes → `MissingMeasurements`.
    
- Profile absent → `MissingEvaluationProfile`.
    
- Pack absent → erreur.
    
- PackLock absent → `MissingPackLock`.
    
- TolerancePolicy absente → `MissingTolerancePolicy`.
    
- Beauty score demandé → `BeautyScoreRejected`.
    
- Claim intentionnelle → `IntentInferenceRejected`.
    

### Risques

- Score devient héros du système.
    
- Confidence mélangée au score.
    
- Profile crée des ratios.
    
- Evaluation devient jugement esthétique.
    

### Erreurs à éviter

- `score = vérité`.
    
- `score = beauté`.
    
- `profile` qui définit une rule.
    
- Explanation inventée sans measurements.
    
- Inférer l’intention de l’auteur.
    

### Dépendances

- PR2 ;
    
- PR4 ;
    
- PR7.
    

### Gate de validation

**Evaluation gate** : aucun score n’est accepté sans measurements + profile + pack + tolérances.

Confidence séparée du score.

Aucun beauty score.

---

## PR9 — Comparison and decision

### Objectif

Comparer deux evaluations A/B dans le même contexte et produire une decision limitée, traçable et non esthétique.

La démo MVP doit comparer deux compositions selon :

- le même pack ;
    
- le même profile ;
    
- les mêmes tolérances ;
    
- le même contexte.
    

La decision doit dire :

```txt
plus proche du système déclaré
```

Elle ne doit jamais dire :

```txt
meilleure
plus belle
```

### Scope exact

- `compareCompositionsBasic`.
    
- `Decision`.
    
- `Comparison`.
    
- `Explanation` structurée minimale.
    
- Tie policy.
    
- Non-comparable policy.
    

Statuses :

- `a_closer`;
    
- `b_closer`;
    
- `tie`;
    
- `ambiguous`;
    
- `non_comparable`.
    

### Hors scope

- multi-candidate ranking riche ;
    
- multi-pack comparison ;
    
- recommendation ;
    
- optimization ;
    
- creative correction ;
    
- beauty ;
    
- intent inference.
    

### Livrables attendus

- Comparison A/B.
    
- Decision.
    
- Explanation structurée.
    
- Warnings pour tie/ambiguous/non-comparable.
    
- Validation du contexte partagé.
    

### Zones conceptuelles probables

- comparison model ;
    
- decision model ;
    
- explanation model ;
    
- comparison operation ;
    
- non-comparable diagnostics.
    

### Critères d’acceptation

A/B comparables seulement si même :

- pack ;
    
- pack lock ;
    
- profile ;
    
- tolerances ;
    
- surface ;
    
- coordinate system ;
    
- metric policy ;
    
- operation context.
    

Decision référence measurements/evaluations.

Tie et ambiguous sont des résultats valides.

Non-comparable si context différent.

Pas de “meilleur” ou “plus beau”.

### Tests conceptuels à prévoir

- A plus proche que B → `a_closer`.
    
- B plus proche que A → `b_closer`.
    
- Scores sous tie tolerance → `tie`.
    
- Same scores but `scoreDelta < tieTolerance` → `tie`.
    
- Measurements insuffisantes → `ambiguous`.
    
- Profiles différents → `non_comparable`.
    
- Different profile → `non_comparable`.
    
- Tolérances différentes → `non_comparable`.
    
- Different tolerances → `non_comparable`.
    
- Beauty claim → rejet.
    

### Risques

- Comparaison devient recommandation.
    
- Decision non traçable.
    
- Tie/ambiguous mal gérés.
    
- Context différent accepté par erreur.
    

### Erreurs à éviter

- “A est meilleure”.
    
- Comparer avec packs différents.
    
- Comparer avec profiles différents.
    
- Comparer avec tolérances différentes.
    
- Masquer warnings de comparaison.
    
- Faire une explanation textuelle sans sources.
    

### Dépendances

- PR2 ;
    
- PR8.
    

### Gate de validation

**Comparison gate** : aucune decision n’est acceptée si elle ne peut pas être retracée vers measurements, evaluations, profile, pack et context.

Pas de decision si A/B ne partagent pas packLock, profile, tolerances, surface, coordinateSystem, metricPolicy et operationContext.

---

## PR10 — Artifacts

### Objectif

Produire des artifacts structurés et un visual artifact simple comme projections dérivées des source objects Norma.

PR10 est correct dans son objectif, mais sa dépendance doit inclure PR2.

Un artifact doit utiliser :

- l’enveloppe de résultat ;
    
- warnings/errors ;
    
- provenance ;
    
- status ;
    
- output refs ;
    
- run/runRef conceptuel.
    

Ces éléments viennent de PR2.

### Scope exact

- `Artifact`.
    
- `StructuredResultArtifact`.
    
- `ConstructionSummaryArtifact`.
    
- `EvaluationReportArtifact`.
    
- `ExplanationArtifact`.
    
- `SimpleVisualArtifact`.
    
- Artifact status :
    
    - `current`;
        
    - `lossy`;
        
    - `stale`;
        
    - `non_replayable`.
        
- Source refs.
    
- Provenance.
    
- Warnings.
    
- Artifact generation operations.
    
- Erreur obligatoire : `ArtifactWouldBecomeSourceOfTruth`.
    

### Hors scope

- DXF ;
    
- PDF ;
    
- PNG overlay ;
    
- plugin payload ;
    
- interactive rendering ;
    
- rich visual style ;
    
- artifact as input ;
    
- import from SVG ;
    
- CSV measurements, qui reste V1.5.
    

### Livrables attendus

- Artifact structuré principal.
    
- Résumé de construction.
    
- Rapport d’évaluation.
    
- Artifact d’explication.
    
- Visual artifact simple limité.
    
- Warnings visibles dans artifacts.
    
- Source refs obligatoires.
    
- Status artifact minimal.
    
- Erreur `ArtifactWouldBecomeSourceOfTruth`.
    

### Zones conceptuelles probables

- artifact model ;
    
- structured artifact generation ;
    
- visual artifact descriptor ;
    
- artifact provenance ;
    
- artifact diagnostics.
    

### Critères d’acceptation

- Chaque artifact référence ses source objects.
    
- Chaque artifact référence provenance, warnings, options explicites et run/runRef conceptuel.
    
- Artifact sans provenance → invalide.
    
- Visual artifact marqué dérivé.
    
- Artifact ne contient aucun ratio/rule/measurement/score absent des sources.
    
- SVG ou rendu ne peut pas devenir input core.
    
- Warnings critiques visibles.
    
- Artifact ne devient jamais source de vérité.
    
- Si un artifact risque de devenir source de vérité → `ArtifactWouldBecomeSourceOfTruth`.
    

### Tests conceptuels à prévoir

- Structured artifact depuis run/evaluation → success.
    
- Visual artifact depuis construction → success.
    
- Artifact sans sourceRefs → erreur.
    
- Artifact sans run/runRef conceptuel → erreur ou `non_replayable`.
    
- Artifact invente une measurement → erreur.
    
- SVG modifié → ne modifie pas construction source.
    
- Artifact stale → warning/status.
    
- Artifact utilisé comme source core → `ArtifactWouldBecomeSourceOfTruth`.
    

### Risques

- Visual artifact devient produit principal.
    
- SVG devient modèle.
    
- Artifact cache warnings.
    
- Artifact bypass le contrat de résultat PR2.
    

### Erreurs à éviter

- Ajouter styles comme vérité.
    
- Réimporter visual artifact.
    
- Produire un report qui contient beauty claim.
    
- Créer une explanation dans l’artifact sans source.
    
- Oublier PR2 dans les dépendances.
    

### Dépendances

- PR2 ;
    
- PR6 ;
    
- PR7 ;
    
- PR8 ;
    
- PR9.
    

### Gate de validation

**Artifact gate** : un artifact ne passe que s’il est dérivé, sourcé, traçable et non source de vérité.

Aucun artifact sans source objects, provenance, warnings, options explicites et référence run/runRef conceptuelle.

---

## PR11 — Run, PackLock, OperationContext

### Objectif

Finaliser la replay-readiness MVP :

- identité ;
    
- contexte effectif ;
    
- pack lock ;
    
- output refs ;
    
- deterministic ordering ;
    
- mismatch policy.
    

Norma doit pouvoir prouver pourquoi un résultat existe, avec :

- quelles entrées ;
    
- quelles versions ;
    
- quelles règles ;
    
- quelles tolérances ;
    
- quelles sources.
    

La règle d’idempotence est :

```txt
same input
+ same pack
+ same rules
+ same tolerances
+ same coordinate system
+ same operation version
+ same context
= same output
```

PR11 ne doit pas devenir un moteur de replay complet.

### Scope exact

- `Run`.
    
- `PackLock`.
    
- `OperationContext`.
    
- `RunInput`.
    
- `RunOutput`.
    
- `OutputRefs`.
    
- Deterministic ordering.
    
- Mismatch policy.
    
- Replay-readiness status.
    
- No full `replayRun`.
    

### Mismatches explicites à couvrir

PR11 doit rendre explicites ces mismatches :

- pack version mismatch ;
    
- pack content identity mismatch ;
    
- operation version mismatch ;
    
- geometry model version mismatch ;
    
- tolerance policy mismatch ;
    
- coordinate policy mismatch ;
    
- metric policy mismatch ;
    
- feature flags mismatch ;
    
- artifact stale ;
    
- missing source.
    

### Hors scope

- `replayRun` complet ;
    
- `verifyRun`;
    
- `verifyArtifactFreshness`;
    
- cryptographic signatures ;
    
- pack registry ;
    
- storage strategy ;
    
- content-addressable cache complet ;
    
- remote verification ;
    
- hash final figé.
    

### Livrables attendus

Run envelope pour opérations significatives.

PackLock complet :

- pack id ;
    
- pack version ;
    
- pack schema version ;
    
- content identity.
    

OperationContext :

- core version ;
    
- operation version ;
    
- geometry model version ;
    
- coordinate policy ;
    
- metric policy ;
    
- tolerance policy ;
    
- rounding/numeric/ordering policy ;
    
- feature flags.
    

Mismatch warnings/errors.

OutputRefs vers :

- construction ;
    
- measurements ;
    
- evaluation ;
    
- decision ;
    
- artifacts.
    

### Zones conceptuelles probables

- runtime identity ;
    
- run model ;
    
- pack lock model ;
    
- operation context ;
    
- mismatch diagnostics ;
    
- deterministic ordering.
    

### Critères d’acceptation

- Chaque résultat significatif référence un run/runRef.
    
- PackLock visible dans outputs concernés.
    
- OperationContext effectif visible.
    
- Same input + same pack + same rules + same context → same output.
    
- Pack version mismatch → warning/error.
    
- Pack content identity mismatch → error.
    
- Operation version mismatch → warning/error.
    
- Geometry model version mismatch → warning/error.
    
- Tolerance policy mismatch → non-comparable ou warning/error.
    
- Coordinate policy mismatch → warning/error.
    
- Metric policy mismatch → warning/error.
    
- Feature flags mismatch → warning/error.
    
- Artifact stale possible.
    
- Missing source → error ou warning critique.
    
- `replayRun` complet non exposé.
    

### Tests conceptuels à prévoir

- Deux runs identiques → outputs identiques.
    
- Pack version mismatch → warning/error.
    
- Pack content identity mismatch → error.
    
- Operation version mismatch → warning/error.
    
- Geometry model version mismatch → warning/error.
    
- Tolerance policy mismatch → non-comparable ou warning/error.
    
- Coordinate policy mismatch → warning/error.
    
- Metric policy mismatch → warning/error.
    
- Feature flags mismatch → warning/error.
    
- OperationContext incomplet → error.
    
- Artifact sans run/source → `non_replayable`.
    
- Missing source → error ou warning critique.
    

### Risques

- Faire du replay complet trop tôt.
    
- Oublier le context effectif.
    
- Ajouter un hash final prématuré.
    
- Cacher des mismatches dans des defaults.
    

### Erreurs à éviter

- Timestamp comme identité principale.
    
- Artifact comme source de replay.
    
- Pack version sans content identity.
    
- Context caché dans defaults.
    
- Exposer `replayRun` complet trop tôt.
    

### Dépendances

- PR2 ;
    
- PR4 ;
    
- PR6 ;
    
- PR7 ;
    
- PR8 ;
    
- PR9 ;
    
- PR10.
    

### Gate de validation

**Replay-readiness gate** : un résultat MVP n’est acceptable que si ses dépendances déterministes sont visibles.

Un résultat MVP n’est acceptable que si les dépendances déterministes qui produisent l’output sont visibles.

---

## PR12 — MVP demo harness

### Objectif

Assembler la démo vérité :

```txt
Surface proportionnelle évaluée
```

La démo MVP recommandée reçoit :

- une surface rectangulaire ;
    
- un pack de tiers ;
    
- deux compositions A/B ;
    
- un profile ;
    
- des tolérances ;
    
- un operation context.
    

Puis elle produit :

- construction ;
    
- measurements ;
    
- evaluation ;
    
- comparison ;
    
- explanation ;
    
- artifacts.
    

Elle couvre le cœur V1 tout en restant sans image, UI, plugin, CAD ou scoring esthétique.

PR12 doit rester un harness, pas une UI.

### Scope exact

- Surface rectangulaire de démo.
    
- Surface `1200 × 800` ou équivalent.
    
- Pack minimal `norma.basic-proportions@0.1.0`.
    
- Rule set `surface-basic-third-grid`.
    
- Composition A proche.
    
- Composition B moins proche.
    
- Evaluation profile `basic-grid-alignment`.
    
- Operation sequence.
    
- Outputs structurés.
    
- Artifacts structurés.
    
- Visual artifact simple.
    
- Run/replay envelope.
    
- Warnings/errors.
    
- Negative cases.
    
- Demo report minimal.
    

### Cas négatifs obligatoires minimum

PR12 ne doit pas seulement montrer le happy path.

Il doit inclure au minimum :

- 1 cas success A/B ;
    
- 1 cas `non_comparable` ;
    
- 1 cas beauty score rejected ;
    
- 1 cas missing pack/rule/profile rejected.
    

Cas négatifs minimum à inclure :

- `MissingPackLock` → error/critical_warning ;
    
- `MissingProfile` → evaluation impossible ;
    
- `DifferentTolerancesForComparison` → `non_comparable` ;
    
- `BeautyScoreRequested` → rejected ;
    
- `RatioAbsentFromPack` → error.
    

### Hors scope

- UI interactive ;
    
- caméra ;
    
- image ;
    
- plugin ;
    
- CAD ;
    
- cloud ;
    
- MCP ;
    
- SDK ;
    
- recommendations ;
    
- optimization ;
    
- beauty.
    

### Livrables attendus

- Démo end-to-end.
    
- Input structuré.
    
- Construction.
    
- Measurements A/B.
    
- Evaluation A/B.
    
- Comparison decision.
    
- Explanation.
    
- Structured artifacts.
    
- Simple visual artifact.
    
- Run/PackLock/OperationContext.
    
- Warnings/errors.
    
- Cas de rejet contrôlé.
    
- Cas `non_comparable`.
    
- Cas beauty score rejected.
    
- Cas missing pack/rule/profile rejected.
    

### Zones conceptuelles probables

- demo scenario ;
    
- demo input fixtures ;
    
- demo operation orchestration ;
    
- demo output snapshots conceptuels ;
    
- demo validation report.
    

### Critères d’acceptation

- La démo démarre depuis données structurées.
    
- Le pack est validé/verrouillé.
    
- La construction produit guides/zones/grid/diagonales/intersections.
    
- A et B sont mesurées.
    
- A et B sont évaluées avec le même profile.
    
- Comparison happy path produit `a_closer`, `b_closer`, `tie` ou `ambiguous`.
    
- Cas négatif produit `non_comparable`.
    
- Explanation dérive des measurements.
    
- Artifacts sont dérivés.
    
- Run/PackLock/OperationContext visibles.
    
- Beauty score rejeté.
    
- Pack implicite rejeté.
    
- Missing pack/rule/profile rejeté.
    
- Même input + même pack + même context → même output.
    
- La démo montre au moins un cas négatif contrôlé.
    

### Tests conceptuels à prévoir

- Happy path complet.
    
- Ratio absent → erreur.
    
- Rule absente → erreur.
    
- Profile absent → erreur.
    
- Pack implicite → erreur.
    
- MissingPackLock → error/critical_warning.
    
- DifferentTolerancesForComparison → `non_comparable`.
    
- Beauty score demandé → rejet.
    
- Visual artifact modifié → source objects inchangés.
    
- Mismatch context → warning/error ou `non_comparable`.
    

### Risques

- Démo devient UI.
    
- Démo devient SVG.
    
- Démo devient score esthétique.
    
- Démo masque warnings.
    
- Démo ne montre que le happy path.
    

### Erreurs à éviter

- Montrer visual artifact avant output structuré.
    
- Dire “A est meilleure”.
    
- Oublier `Run`.
    
- Oublier cas négatif.
    
- Laisser croire que le SVG, une UI, une image, un plugin, un agent ou un score esthétique est le produit.
    

### Dépendances

- PR0 à PR11.
    

### Gate de validation

**Demo truth gate** : la démo doit prouver la reproductibilité du moteur avant l’ergonomie.

La démo échoue si elle laisse croire que le SVG, une UI, une image, un plugin, un agent ou un score esthétique est le produit.

---

# 5. PR1 détaillé — Norma Core Skeleton

## 5.1 Rôle de PR1

PR1 n’est pas le moment de construire :

- la géométrie ;
    
- les packs ;
    
- les rules ;
    
- les constructions ;
    
- les measurements ;
    
- les evaluations ;
    
- les artifacts.
    

PR1 sert à poser :

> **un noyau vide mais strict, capable d’accueillir les objets futurs sans laisser entrer UI, caméra, plugin, formats natifs, prompts libres ou résultats non structurés.**

PR1 doit éviter deux erreurs opposées :

- être trop vide pour guider PR2 ;
    
- être trop ambitieux et commencer la logique métier.
    

---

## 5.2 Scope exact de PR1

PR1 doit inclure :

### A. Frontière core minimale

Le skeleton doit établir que le core est indépendant :

- des interfaces ;
    
- des adapters ;
    
- des fichiers natifs ;
    
- de l’image ;
    
- de la caméra ;
    
- du cloud ;
    
- du rendu ;
    
- des agents.
    

Les interfaces et adapters sont des clients du core.

Ils appellent, traduisent, affichent ou exportent, mais ne définissent pas la logique Norma.

### B. Résultat structuré minimal

Même sans calcul réel, le skeleton doit pouvoir représenter :

- `status`;
    
- `warnings`;
    
- `errors`;
    
- `provenance`;
    
- `outputRefs` vide ou minimal ;
    
- `runRef` placeholder si opération significative.
    

### C. Diagnostics minimaux

PR1 doit permettre des diagnostics conceptuels obligatoires :

- `MissingOperation`;
    
- `UnsupportedOperation`;
    
- `NotImplemented`;
    
- `InvalidInputShape`;
    
- `CriticalWarningNotSuppressible`;
    
- `MissingProvenance`.
    

PR1 doit aussi permettre les diagnostics suivants :

- `OperationNotImplemented`;
    
- `MissingOperationName`;
    
- `MissingOperationVersion`;
    
- `InternalInvariantViolation`;
    
- `ForbiddenCoreDependency`.
    

Le fichier de vérification demande que `Error` ou `Warning` contienne conceptuellement :

- `code`;
    
- `severity`;
    
- `message`;
    
- `targetRef`;
    
- `source`;
    
- `blocking`;
    
- `provenance`.
    

Les severities vont de `info` à `fatal`.

### D. Provenance minimale

Tout résultat dérivé futur doit pouvoir dire :

- par quelle opération il est produit ;
    
- depuis quel input ;
    
- avec quelle source conceptuelle ;
    
- avec quels warnings/errors.
    

En PR1, cela peut rester minimal.

### E. Placeholders runtime

PR1 doit réserver les concepts :

- `Run`;
    
- `PackLock`;
    
- `OperationContext`.
    

Ils ne sont pas complets en PR1.

Ils ne doivent pas être absents.

---

## 5.3 Ce qui ne doit pas changer dans PR1

PR1 ne doit pas :

- choisir un framework UI ;
    
- choisir un transport API ;
    
- choisir un format final de fichier ;
    
- implémenter une géométrie complète ;
    
- implémenter un pack ;
    
- produire un SVG ;
    
- produire un score ;
    
- produire une démo ;
    
- créer un adapter ;
    
- ajouter un agent tool ;
    
- promettre replay complet.
    

---

## 5.4 Objets minimaux de PR1

|Objet|Rôle PR1|
|---|---|
|`CoreVersion`|Identifier la version conceptuelle du core.|
|`OperationName`|Nommer une opération.|
|`OperationVersion`|Préparer le versioning comportemental.|
|`OperationStatus`|Statut minimal.|
|`Diagnostic`|Base commune error/warning.|
|`Error`|Diagnostic bloquant.|
|`Warning`|Diagnostic non bloquant ou critique.|
|`Provenance`|Source minimale d’un résultat.|
|`SourceReference`|Placeholder de source.|
|`RunRef`|Référence future vers run.|
|`PackLockRef`|Référence future vers pack lock.|
|`OperationContextRef`|Référence future vers context.|
|`CoreResult`|Enveloppe minimale de résultat structuré.|

Ces objets doivent rester génériques.

Ils ne doivent pas porter de logique géométrique.

---

## 5.5 Opérations minimales ou stubs conceptuels

PR1 peut introduire un registry vide ou quelques stubs :

|Stub|Rôle|
|---|---|
|`unsupportedOperation`|Retourner une erreur structurée.|
|`notImplementedOperation`|Retourner un status explicite sans résultat inventé.|
|`validateCoreSkeleton`|Vérifier que le skeleton répond au contrat minimal.|

Ces stubs ne doivent pas être présentés comme capacités métier.

---

## 5.6 Erreurs/warnings minimaux

|Code|Type|Sens|
|---|---|---|
|`MissingOperation`|error|Appel sans opération.|
|`UnsupportedOperation`|error|Operation inconnue.|
|`NotImplemented`|error ou warning critique|Operation connue mais non disponible.|
|`OperationNotImplemented`|error ou warning critique|Operation connue mais non disponible.|
|`InvalidInputShape`|error|Input structurellement invalide.|
|`MissingOperationName`|error|Appel sans operation name.|
|`MissingOperationVersion`|warning critique / error|Version d’opération manquante.|
|`MissingProvenance`|warning critique|Résultat dérivé sans provenance.|
|`CriticalWarningNotSuppressible`|invariant|Un client ne peut pas masquer un warning critique.|
|`ForbiddenCoreDependency`|error|Tentative d’introduire UI/caméra/plugin/cloud.|

---

## 5.7 Documentation minimale

PR1 doit documenter :

- ce que le skeleton contient ;
    
- ce qu’il ne contient pas ;
    
- comment les PRs suivantes doivent s’y brancher ;
    
- les termes interdits ou dangereux ;
    
- la règle “structured result always” ;
    
- la règle “no silent failure” ;
    
- la règle “no client dependency”.
    

---

## 5.8 Acceptance criteria PR1

PR1 est accepté seulement si :

1. Le skeleton peut retourner un résultat structuré minimal.
    
2. Toute opération absente retourne une erreur structurée.
    
3. Toute opération inconnue retourne une erreur structurée.
    
4. Toute opération non implémentée retourne un status explicite.
    
5. Aucun stub ne retourne un succès trompeur.
    
6. Warnings/errors ont code, severity, message, source et blocking flag conceptuels.
    
7. Provenance existe comme concept.
    
8. `Run`, `PackLock`, `OperationContext` existent comme placeholders.
    
9. Aucune dépendance UI/caméra/plugin/cloud n’est introduite.
    
10. Aucun ratio, rule, construction, measurement ou score n’est hardcodé.
    
11. Les diagnostics obligatoires PR1 existent.
    
12. La documentation explique clairement que PR1 ne prouve pas encore le moteur métier.
    
13. Les PRs suivantes peuvent s’appuyer sur le skeleton sans deviner les invariants de base.
    

---

## 5.9 Risques PR1

|Risque|Protection|
|---|---|
|Skeleton trop abstrait|Inclure result envelope + diagnostics + provenance.|
|Skeleton trop ambitieux|Interdire geometry/pack/scoring/artifact réels.|
|Faux succès|Stub doit retourner not implemented ou unsupported.|
|Diagnostics faibles|Shape minimale d’erreur/warning obligatoire.|
|Runtime oublié|Placeholders `Run`, `PackLock`, `OperationContext`.|

---

## 5.10 Cas limites PR1

- Operation absente.
    
- Operation inconnue.
    
- Operation connue mais non implémentée.
    
- Input vide.
    
- Input mal formé.
    
- Warning critique tenté comme warning simple.
    
- Résultat dérivé sans provenance.
    
- Tentative d’introduire un objet UI.
    
- Tentative d’introduire une image ou un SVG comme source.
    

---

## 5.11 Vérifications à faire

Checklist PR1 :

- Le skeleton ne calcule rien de proportionnel.
    
- Le skeleton ne dessine rien.
    
- Le skeleton ne lit aucune image.
    
- Le skeleton ne parle pas de plugin.
    
- Le skeleton ne choisit aucun pack.
    
- Le skeleton n’a aucun ratio hardcodé.
    
- Le skeleton peut exprimer un échec propre.
    
- Le skeleton peut exprimer un warning critique.
    
- Le skeleton prépare PR2 sans figer une API finale.
    

---

# 6. Matrice de dépendances corrigée

|PR|Dépend de|Pourquoi|
|--:|---|---|
|PR0|—|Base normative.|
|PR1|PR0|Skeleton doit respecter les guardrails.|
|PR2|PR0, PR1|Les contracts s’appuient sur le skeleton.|
|PR3|PR0, PR1, PR2|La géométrie doit respecter les operation contracts.|
|PR4|PR0, PR1, PR2|Le pack doit être validable et appelé via contracts.|
|PR5|PR2, PR4|Les rules dépendent des packs et des contracts.|
|PR6|PR3, PR4, PR5|Construction = geometry + pack + rules.|
|PR7|PR2, PR3, PR6|Measurements mesurent geometry/construction et respectent les contracts.|
|PR8|PR2, PR4, PR7|Evaluation = pack/profile + measurements + contracts.|
|PR9|PR2, PR8|Comparison = evaluations + context contract.|
|PR10|PR2, PR6, PR7, PR8, PR9|Artifacts représentent source objects et utilisent l’enveloppe de résultat PR2.|
|PR11|PR2, PR4, PR6, PR7, PR8, PR9, PR10|Run/replay-readiness relie toutes les sorties.|
|PR12|PR0–PR11|Demo harness assemble tout.|

Correction principale :

```txt
PR10 dépend de PR2, PR6, PR7, PR8, PR9.
```

Pas besoin de faire dépendre PR10 de PR11 si PR2 a bien prévu `runRef` conceptuel.

PR11 finalise la replay-readiness.

---

# 7. Roadmap PR finale compacte pour dev

|PR|Titre|Livrable dev principal|Gate bloquant|
|--:|---|---|---|
|PR0|Spec freeze / guardrails|Guardrails MVP + checklist|Aucun hors-scope MVP autorisé|
|PR1|Core skeleton|Result envelope + diagnostics + placeholders runtime|Aucun faux résultat|
|PR2|Operation contracts|Call/result contracts + variables canoniques|Aucun pack/rule/tolérance implicite|
|PR3|Geometry model V1|Segment/Surface/Composition/primitives|Aucune géométrie hors V1|
|PR4|Minimal ratio pack|`norma.basic-proportions@0.1.0` + PackLock conceptuel|Aucun ratio hardcodé|
|PR5|Rule declarations/resolution|RuleSet + rule type registry + resolution trace|Rule unsupported = error/warning|
|PR6|Construction generation|guides/zones/grid/diagonals/intersections|Chaque objet dérivé est traçable|
|PR7|Measurements|distances/positions/areas/overlap/coverage|Aucun score avant measurements|
|PR8|Evaluation minimal|profile + component scores + confidence|Aucun score sans profile/pack/tolérances|
|PR9|Comparison/decision|A/B decision + explanation structurée|Même contexte obligatoire|
|PR10|Artifacts|structured/report/explanation/visual artifacts|Artifact jamais source|
|PR11|Replay-readiness|Run/PackLock/OperationContext/mismatches|Dépendances déterministes visibles|
|PR12|Demo harness|Surface proportionnelle évaluée end-to-end|Démo vérité, pas UI/score esthétique|

---

# 8. MVP completion gate

Le MVP est terminé seulement si les critères suivants sont vrais.

## 8.1 Core et inputs

- Une surface structurée peut être créée.
    
- Une composition 2D simple peut être créée.
    
- Les elements rectangulaires sont acceptés.
    
- Les géométries hors V1 sont rejetées.
    
- Coordinate system, metric policy et tolerance policy sont visibles.
    

---

## 8.2 Pack

- Le pack minimal peut être validé.
    
- Le pack minimal peut être verrouillé.
    
- `PackLock` expose pack id, version, schema version, content identity.
    
- Ratio absent = erreur.
    
- Rule absente = erreur.
    
- Pack implicite = rejet.
    

---

## 8.3 Rules/construction

- Le rule set minimal peut être résolu.
    
- Guides verticaux/horizontaux sont produits.
    
- Zones sont produites.
    
- Grille `3×3` est produite.
    
- Diagonales sont produites.
    
- Intersections sont produites.
    
- Guide-border intersections sont produites.
    
- Chaque objet dérivé a provenance.
    
- `constructionTrace` est produit.
    

---

## 8.4 Measurements

- Deux compositions simples peuvent être mesurées.
    
- Distances aux guides produites.
    
- Alignments produits.
    
- Aires produites.
    
- Containment produit.
    
- Overlap produit.
    
- Coverage produit.
    
- Warnings structurés produits si nécessaire.
    
- Aucun `ComponentScore` n’est produit en PR7.
    

---

## 8.5 Evaluation/comparison

- Deux evaluations peuvent être produites avec le même profile.
    
- Component scores visibles.
    
- Confidence séparée.
    
- Comparison A/B produit `a_closer`, `b_closer`, `tie`, `ambiguous` ou `non_comparable`.
    
- Comparison impossible si pack/profile/tolérances/context diffèrent.
    
- Beauty score rejeté.
    
- Intent inference rejetée.
    

---

## 8.6 Explanation

- Explanation structurée produite depuis measurements.
    
- Explanation référence écarts, tolérances, profile, pack et warnings.
    
- Pas d’intention supposée.
    
- Pas de claim esthétique.
    

---

## 8.7 Artifacts

- `StructuredResultArtifact` produit.
    
- `ConstructionSummaryArtifact` produit.
    
- `EvaluationReportArtifact` produit.
    
- `ExplanationArtifact` produit.
    
- `SimpleVisualArtifact` produit comme projection dérivée.
    
- Artifact status disponible : `current`, `lossy`, `stale`, `non_replayable`.
    
- Aucun artifact ne devient source de vérité.
    
- Provenance et warnings visibles.
    
- `ArtifactWouldBecomeSourceOfTruth` existe et bloque le cas interdit.
    

---

## 8.8 Replay-readiness

- `Run` visible.
    
- `PackLock` visible.
    
- `OperationContext` visible.
    
- Operation/version/input/context/outputRefs visibles.
    
- Warnings/errors visibles.
    
- Même input + même pack + mêmes rules + mêmes tolérances + même context + même operation version = même output.
    
- Mismatch pack/context/operation version produit warning/error.
    
- Mismatches explicites couverts :
    
    - pack version mismatch ;
        
    - pack content identity mismatch ;
        
    - operation version mismatch ;
        
    - geometry model version mismatch ;
        
    - tolerance policy mismatch ;
        
    - coordinate policy mismatch ;
        
    - metric policy mismatch ;
        
    - feature flags mismatch ;
        
    - artifact stale ;
        
    - missing source.
        
- `replayRun` complet non requis.
    

---

## 8.9 Demo truth

- La démo **Surface proportionnelle évaluée** fonctionne de bout en bout.
    
- Elle utilise une seule surface.
    
- Elle utilise un seul pack minimal.
    
- Elle utilise deux compositions A/B.
    
- Elle utilise un seul profile.
    
- Elle produit outputs structurés avant visual artifact.
    
- Elle inclut au minimum :
    
    - 1 cas success A/B ;
        
    - 1 cas `non_comparable` ;
        
    - 1 cas beauty score rejected ;
        
    - 1 cas missing pack/rule/profile rejected.
        
- Elle ne contient pas caméra, image, plugin, CAD natif, cloud, UI complète ou marketplace.
    

La démo doit prouver la reproductibilité avant l’ergonomie, exposer warnings/errors, et garder le visual artifact comme projection dérivée.

---

# 9. Ce qui doit rester après le MVP

Après le MVP, seulement après stabilisation du moteur :

|Sujet post-MVP|Statut|
|---|---|
|CLI minimale|V1.5|
|SDK minimal|V1.5|
|API locale/process|V1.5|
|MCP minimal|V1.5|
|Agent playbooks|V1.5|
|`replayRun` complet|V1.5|
|`verifyRun`|V1.5|
|`verifyArtifactFreshness`|V1.5|
|CSV measurements|V1.5|
|Packs plus riches|V1.5 / futur|
|Pack registry|futur|
|User-defined packs|futur|
|Design tool adapter prototype|V1.5 / futur|
|CAD adapter prototype non-core|V1.5 / futur|
|Plugins natifs|futur|
|Camera app|futur|
|Image/vision pipeline|futur|
|CAD natif robuste|futur|
|Cloud API|futur|
|Marketplace|futur|
|3D|futur|
|Polygones complexes|futur|
|Formats natifs|futur|
|Recommandations créatives|futur, seulement après policy stricte|
|Optimisation automatique|futur, hors MVP|

La spec classe déjà CLI, SDK, API locale/process, MCP minimal et agent playbooks comme V1.5, tandis que plugins natifs, camera app, CAD adapters robustes, cloud API et autres intégrations restent futures.

---

# 10. Décisions à verrouiller

Décisions copiables dans le plan développeur :

1. **Le plan PR construit le moteur Norma Core MVP, pas une UI, pas une caméra, pas un plugin, pas une API cloud et pas une marketplace.**
    
2. **Chaque PR doit être petit, relisible, vérifiable et limité à un objectif.**
    
3. **Chaque PR doit déclarer scope, hors scope, livrables, critères d’acceptation, tests conceptuels, risques, dépendances et gate.**
    
4. **PR0 verrouille les guardrails avant toute exécution.**
    
5. **PR0 doit inclure une section `Blocked capabilities for MVP` avec les capacités explicitement interdites.**
    
6. **PR1 pose un skeleton strict, sans logique géométrique, sans pack, sans scoring et sans artifact réel.**
    
7. **PR1 doit inclure les diagnostics obligatoires `MissingOperation`, `UnsupportedOperation`, `NotImplemented`, `InvalidInputShape`, `CriticalWarningNotSuppressible` et `MissingProvenance`.**
    
8. **PR2 stabilise les operation contracts et variables canoniques avant toute interface.**
    
9. **Aucune future CLI, SDK, API, MCP tool ou adapter ne doit précéder la stabilisation des operation contracts.**
    
10. **Tout default qui change l’output doit être explicite, versionné ou rejeté.**
    
11. **PR3 stabilise le modèle géométrique V1 avant toute construction.**
    
12. **Les coordonnées normalisées ne sont pas des measurements métriques.**
    
13. **PR4 stabilise le pack minimal avant tout pack riche.**
    
14. **Les ratios vivent dans les packs, pas dans le core ni dans les clients.**
    
15. **PR4 doit tester ratio absent, ratio duplicate, rule references missing ratio, pack with beauty claim et pack without contentIdentity.**
    
16. **PR5 stabilise la séparation rule declarations dans packs / rule types dans core.**
    
17. **Aucune rule ne doit être inventée par une interface, un adapter ou un agent.**
    
18. **PR5 doit produire une trace minimale `resolvedRuleSet`.**
    
19. **PR6 produit une construction traçable ; `generateConstruction` ne doit jamais être opaque.**
    
20. **À partir de PR6, aucun objet dérivé ne peut être produit sans provenance minimale, même si `Run` n’est pas encore finalisé.**
    
21. **PR6 doit produire `constructionTrace`.**
    
22. **PR7 produit measurements avant toute evaluation.**
    
23. **PR7 ne doit produire aucun `ComponentScore`.**
    
24. **Aucun score ne doit exister sans measurements, profile, pack et tolérances.**
    
25. **PR8 produit evaluation et scoring minimal sans beauty score.**
    
26. **PR8 doit rejeter beauty score et intent inference.**
    
27. **PR9 produit comparison et decision uniquement dans le même pack/profile/tolérances/context.**
    
28. **Une decision doit dire “plus proche du système déclaré”, jamais “meilleur” ou “plus beau”.**
    
29. **PR9 doit produire `tie` si `scoreDelta < tieTolerance`.**
    
30. **PR9 doit produire `non_comparable` si les tolérances ou le profile diffèrent.**
    
31. **PR10 produit artifacts dérivés après source objects.**
    
32. **PR10 dépend de PR2, PR6, PR7, PR8 et PR9.**
    
33. **Aucun SVG, export ou visual artifact ne doit devenir source de vérité.**
    
34. **PR10 doit inclure les statuts `current`, `lossy`, `stale`, `non_replayable`.**
    
35. **PR10 doit inclure l’erreur `ArtifactWouldBecomeSourceOfTruth`.**
    
36. **PR11 finalise `Run`, `PackLock`, `OperationContext` et replay-readiness sans implémenter `replayRun` complet.**
    
37. **PR11 doit rendre explicites les mismatches pack version, pack content identity, operation version, geometry model version, tolerance policy, coordinate policy, metric policy, feature flags, artifact stale et missing source.**
    
38. **PR12 assemble la démo vérité “Surface proportionnelle évaluée”.**
    
39. **PR12 doit produire outputs structurés avant visual artifact.**
    
40. **PR12 doit inclure au minimum un success A/B, un `non_comparable`, un beauty score rejected et un missing pack/rule/profile rejected.**
    
41. **Warnings/errors doivent être structurés dès le début et ne doivent jamais être masqués.**
    
42. **Un `critical_warning` ou un `error` ne doit jamais être supprimé par un client, adapter ou agent.**
    
43. **Même input + même pack + mêmes rules + mêmes tolérances + même context + même operation version doit produire le même output.**
    
44. **Toute tentative de pack implicite, ratio absent, rule absente, profile absent, beauty score ou prompt libre comme source doit être rejetée.**
    
45. **Tout ce qui est caméra, image, vision, OpenCV, tracking, plugin, CAD natif, cloud, marketplace, UI complète, MCP complet, SDK complet, recommandations créatives, optimisation automatique, inférence d’intention, 3D, polygones complexes ou formats natifs reste hors MVP.**