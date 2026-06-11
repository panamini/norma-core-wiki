# 

## 1. Verdict sur la roadmap MVP

La roadmap MVP doit construire **le moteur minimal vérifiable** de Norma Core.

Elle doit organiser la progression suivante :

```
spec stable→ contrats d’opération→ modèle géométrique minimal→ pack minimal→ rules→ construction→ measurements→ evaluation→ comparison→ artifacts→ Run / PackLock / OperationContext→ demo harness minimal
```

Le MVP doit prouver la chaîne centrale déjà verrouillée :

```
structured input→ proportional system→ rule resolution→ construction→ measurement→ evaluation→ decision→ explanation→ artifact→ run / replay-readiness
```

Norma Core est déjà défini comme un moteur déterministe, géométrique, proportionnel, structuré, versionné, explicable, replay-ready et indépendant des interfaces. Il doit savoir diviser une surface, générer guides/zones/grilles/diagonales/intersections, mesurer, évaluer une composition simple, comparer deux compositions, produire des artifacts dérivés et relier les résultats à un `Run`.

La roadmap doit donc construire :

- le noyau conceptuel exécutable ;
- les objets canoniques ;
- les opérations structurées ;
- les résultats déterministes ;
- les warnings/errors ;
- les artifacts dérivés ;
- la replay-readiness ;
- la démo vérité **Surface proportionnelle évaluée**.

Elle ne doit pas construire :

- une UI complète ;
- une caméra ;
- un moteur image/vision ;
- un plugin ;
- un adapter CAD natif ;
- une API cloud ;
- une marketplace ;
- un agent autonome ;
- une expérience graphique riche ;
- un système de recommandation créative ;
- un beauty score.

Phrase à verrouiller :

> **La roadmap MVP construit Norma Core comme moteur. Elle ne construit pas encore l’écosystème autour du moteur.**

---

## 2. Principes de découpage

## 2.1 Règles de phasage

La roadmap doit suivre ces règles :

1. **Core avant interface**  
    Les opérations et objets du core doivent exister avant CLI, SDK, API, MCP, plugins ou adapters. Les interfaces et adapters restent des clients du core, pas le core.
2. **Données structurées avant rendu**  
    La vérité doit être dans les objets structurés. Le rendu vient après comme projection.
3. **Pack minimal avant packs riches**  
    Un seul pack minimal suffit pour prouver la mécanique. Les packs riches ouvriraient trop tôt le scope.
4. **Rules avant constructions**  
    Une construction doit toujours être le résultat traçable de rules déclarées.
5. **Constructions avant measurements**  
    Les measurements doivent mesurer des objets sources stables : surface, guides, zones, grille, diagonales, intersections, compositions.
6. **Measurements avant evaluation**  
    Aucun score, decision ou explanation ne doit exister sans measurements.
7. **Evaluation avant comparison**  
    Une comparaison A/B n’a de sens que si A et B ont été évaluées dans le même contexte.
8. **Artifacts après source objects**  
    Un artifact représente des objets Norma déjà produits. Il ne crée pas de connaissance.
9. **Run / PackLock / OperationContext avant toute promesse de replay**  
    Le MVP doit être replay-ready avant de promettre un replay opérationnel complet. La distinction `replay-readiness V1 strict` vs `replayRun V1.5` est déjà verrouillée.
10. **Demo harness après noyau testable**  
    La démo doit assembler le moteur ; elle ne doit pas compenser un core incomplet.
11. **Warnings/errors dès le début**  
    Les warnings et errors ne sont pas une finition. Ils font partie de la vérité du moteur.
12. **Aucun score sans measurements/profile/pack/tolérances**  
    Le score est un résumé relatif, pas une preuve autonome. Le `EvaluationProfile` lit des measurements ; il ne crée pas ratios, rules, measurements ou claims esthétiques.

---

## 2.2 Ordre logique strict

```
1. Stabiliser les mots2. Stabiliser les contrats d’opération3. Stabiliser la géométrie4. Stabiliser le pack minimal5. Appliquer les rules6. Produire la construction7. Mesurer8. Évaluer9. Comparer10. Expliquer11. Produire les artifacts12. Relier au Run13. Montrer la démo
```

Cette séquence empêche les inversions dangereuses :

- score avant mesure ;
- SVG avant construction ;
- interface avant operation ;
- replay repoussé ;
- pack implicite ;
- visual demo qui remplace la vérité structurée.

---

# 3. Phases MVP recommandées

## Vue d’ensemble

|Phase|Nom|But|
|---|---|---|
|0|Spec freeze MVP|Verrouiller le cadre normatif minimal.|
|1|Contrats d’opération et variables canoniques|Stabiliser comment le core est appelé et ce qu’il retourne.|
|2|Modèle géométrique minimal|Stabiliser les espaces et primitives V1.|
|3|Ratio pack minimal|Fournir la connaissance proportionnelle versionnée minimale.|
|4|Rules et construction|Produire guides, zones, grille, diagonales, intersections.|
|5|Measurements|Mesurer les compositions et constructions.|
|6|Evaluation, scoring minimal et comparison|Évaluer A/B sans beauté ni intention.|
|7|Artifacts structurés et visual artifact simple|Représenter les résultats sans devenir source de vérité.|
|8|Run, PackLock, OperationContext et replay-readiness|Rendre les résultats traçables et reproductibles conceptuellement.|
|9|Demo harness minimal|Assembler la démo vérité “Surface proportionnelle évaluée”.|

---

# 4. Détail par phase

## Phase 0 — Spec freeze MVP

### Objectif

Verrouiller ce que le MVP doit prouver et ce qu’il ne doit pas inclure.

Le MVP doit rester aligné sur le périmètre V1 strict : segments 1D, surfaces rectangulaires 2D, compositions 2D simples, données structurées, packs versionnés, rules, constructions, measurements, evaluation, artifacts, `Run`, `PackLock`, `OperationContext`, warnings/errors et replay-readiness.

### Livrables conceptuels

- définition MVP ;
- scope V1 strict ;
- exclusions MVP ;
- vocabulaire canonique ;
- décisions verrouillées ;
- gates de validation ;
- liste des open questions non bloquantes.

### Dépendances

Aucune. C’est le point de départ.

### Critères de fin

La phase est terminée si :

- le MVP est défini comme moteur, pas interface ;
- le scénario cible est **Surface proportionnelle évaluée** ;
- les exclusions sont explicites ;
- les décisions bloquantes sont séparées des questions ouvertes ;
- les termes `Rule`, `Operation`, `Construction`, `Measurement`, `Evaluation`, `Score`, `Decision`, `Explanation`, `Artifact`, `Run` et `PackLock` sont non ambigus.

### Gate de validation

**Spec gate** : aucune phase suivante ne commence si le scope MVP laisse entrer caméra, image, plugin, CAD natif, UI complète, cloud, marketplace ou beauty score.

### Risques

|Risque|Protection|
|---|---|
|Scope trop large|Lister V1 strict / V1.5 / futur.|
|MVP trop vague|Définir la démo vérité comme critère de sortie.|
|Ambiguïté vocabulaire|Glossaire canonique obligatoire.|
|Décisions ouvertes utilisées comme implicites|Open questions séparées des décisions.|

### Exclusions

- UI complète ;
- caméra ;
- image ;
- plugin ;
- CAD natif ;
- cloud ;
- marketplace ;
- agent autonome ;
- formats natifs.

### Peut rester stubbed, conceptuel ou minimal

- format exact des fichiers ;
- hashing exact ;
- syntaxe exacte des warnings/errors ;
- style exact du visual artifact ;
- transport d’interface.

### Ne peut pas être repoussé

- scope V1 ;
- exclusions ;
- définition de la source de vérité ;
- anti-beauty rule ;
- séparation core / interface / artifact ;
- rôle de `Run`, `PackLock`, `OperationContext`.

---

## Phase 1 — Contrats conceptuels d’opération et variables canoniques

### Objectif

Stabiliser la surface exécutable du core avant toute interface.

Les opérations sont déjà définies comme des actions déterministes qui reçoivent des objets structurés Norma, appliquent une logique explicite, puis retournent un résultat structuré avec errors, warnings, provenance et sorties traçables. Elles ne sont ni des objets du domaine, ni des rules, ni des écrans, ni des exports, ni des plugins.

### Livrables conceptuels

- `Operation Call Contract` ;
- `Operation Result Contract` ;
- dictionnaire des variables canoniques ;
- status taxonomy minimale ;
- shape conceptuelle `Error` / `Warning` ;
- validation levels ;
- registry conceptuel des opérations V1.

### Dépendances

- Phase 0.

### Critères de fin

La phase est terminée si tout appel conceptuel peut porter :

- `operation` ;
- `operationVersion` ;
- `input` ;
- `operationContext` ;
- `packLock` si pack utilisé ;
- `ruleRefs` ou `ruleSetRef` si construction/rule ;
- `evaluationProfileRef` si evaluation ;
- `tolerances` si mesure/comparaison ;
- `coordinateSystem` ;
- `metricPolicy` ;
- `requestedOutputs` ;
- `requestedArtifacts` si demandé ;
- `featureFlags` si effet sur résultat.

Un résultat conceptuel doit porter :

- `status` ;
- `run` ou `runRef` ;
- `result` ou `outputRefs` ;
- `warnings`, même vide ;
- `errors`, même vide ;
- `provenance` ;
- `packLock` si applicable ;
- `operationContext` effectif ;
- `artifactRefs` si artifacts produits ;
- `explanationRefs` si explanation produite.

Ces compléments ont été explicitement identifiés comme nécessaires pour éviter que CLI/SDK/API/MCP/agents inventent leurs propres variables, defaults, résultats ou règles.

### Gate de validation

**Operation contract gate** : aucune opération publique conceptuelle ne passe si elle accepte un prompt libre, un pack implicite, une tolérance cachée, un état UI ou un objet externe natif comme source de vérité.

### Risques

|Risque|Protection|
|---|---|
|Contrat trop proche d’une API finale|Rester conceptuel, pas format final.|
|Variables trop ouvertes|Verrouiller les variables qui changent le résultat.|
|Defaults cachés|Tout default qui change un résultat doit être explicite, versionné ou rejeté.|
|Operation opaque|Chaque operation orchestratrice doit exposer sa trace.|

### Exclusions

- syntaxe finale JSON ;
- transport HTTP ;
- CLI syntax ;
- SDK methods ;
- MCP tool schemas complets ;
- serialization détaillée.

### Peut rester stubbed, conceptuel ou minimal

- noms exacts des champs ;
- forme exacte des payloads ;
- schéma strict final ;
- mapping transport.

### Ne peut pas être repoussé

- variables conceptuelles obligatoires ;
- `operationVersion` ;
- status ;
- warnings/errors ;
- provenance ;
- context effectif ;
- run/runRef conceptuel ;
- interdiction pack/rule/tolérance implicites.

---

## Phase 2 — Modèle géométrique minimal

### Objectif

Construire le modèle géométrique V1 minimal : petit, rectangulaire, explicite, mesurable et reproductible.

Le modèle V1 doit utiliser une géométrie rectangulaire normalisée avec métrique explicite : positions normalisées, mais distances, angles et aires doivent toujours préciser leur espace de référence et leur convention métrique.

### Livrables conceptuels

- `SegmentSpace` ;
- `SurfaceSpace` ;
- `Composition2D` simple ;
- `CoordinateSystem` ;
- `MetricPolicy` ;
- `TolerancePolicy` ;
- `Point` ;
- `Segment` ;
- `Line` limitée ;
- `Rect` axis-aligned ;
- `Anchor` ;
- `Element` rectangulaire.

### Dépendances

- Phase 0 ;
- Phase 1.

### Critères de fin

La phase est terminée si :

- une surface rectangulaire peut être décrite ;
- une composition simple peut référencer cette surface ;
- les elements rectangulaires sont structurés ;
- les coordonnées normalisées sont séparées des mesures métriques ;
- le repère Norma est explicite ;
- unités, métriques et tolérances sont déclarables ;
- les géométries hors V1 sont rejetées ou marquées hors scope.

### Gate de validation

**Geometry gate** : impossible de passer si une composition peut contenir image brute, layer natif, objet CAD natif, rectangle tourné, courbe, polygone complexe ou géométrie sans coordinate system.

### Risques

|Risque|Protection|
|---|---|
|Confondre surface et canvas UI|`SurfaceSpace` est géométrique, pas visuel.|
|Géométrie flottante|Coordinate system obligatoire.|
|Mélanger normalisé et métrique|`MetricPolicy` explicite.|
|Laisser entrer rotation/polygones|Axis-aligned seulement en V1.|

### Exclusions

- 3D ;
- polygones complexes ;
- courbes ;
- splines ;
- meshes ;
- CAD constraints ;
- image regions ;
- layers natifs ;
- rectangles tournés.

### Peut rester stubbed, conceptuel ou minimal

- exactitude numérique fine ;
- rounding exact ;
- hashing géométrique ;
- import/export géométrique externe.

### Ne peut pas être repoussé

- repère canonique ;
- coordonnées normalisées ;
- metric policy ;
- tolérances ;
- primitives V1 ;
- rejet des géométries hors V1.

---

## Phase 3 — Ratio pack minimal

### Objectif

Créer le pack minimal qui prouve que les ratios vivent dans un système proportionnel versionné, pas dans le core ni dans les clients.

Un ratio pack est déjà défini comme une source de connaissance proportionnelle versionnée, contenant ratios, familles, conventions, règles d’application, rule sets, metadata, provenance, limites d’usage et compatibilité. Le core calcule ; les packs décrivent les systèmes ; les clients affichent ou connectent.

### Livrables conceptuels

Pack recommandé :

```
norma.basic-proportions@0.1.0
```

Contenu minimal :

|Objet|Contenu|
|---|---|
|`Ratios`|`1/2`, `1/3`, `2/3`|
|`RatioSequence`|`1:1:1`|
|`RatioFamily`|`halves`, `thirds`|
|`Rule declarations`|vertical thirds, horizontal thirds, center axes, simple grid, diagonals|
|`RuleSet`|`surface-basic-third-grid`|
|`Provenance`|mathematical / Norma basic|
|`Limits`|no beauty claim, no intention claim|

Ce contenu correspond au brief de démo MVP recommandé : surface rectangulaire, pack de tiers, deux compositions A/B, construction, measurements, evaluation, comparison, explanation et artifacts.

### Dépendances

- Phase 0 ;
- Phase 1 ;
- Phase 2.

### Critères de fin

La phase est terminée si :

- le pack a un id ;
- le pack a une version ;
- le pack a une schema version conceptuelle ;
- le pack a une content identity conceptuelle ;
- les ratios sont nommés ;
- la sequence `1:1:1` est distincte des ratios isolés ;
- les rule declarations sont présentes ;
- le rule set minimal est résolvable ;
- les limites d’usage interdisent beauty/intention.

### Gate de validation

**Pack gate** : impossible de passer si un ratio est hardcodé dans le core, injecté par l’interface, inventé par une operation ou absent du pack.

### Risques

|Risque|Protection|
|---|---|
|Pack trop riche|Un seul pack minimal.|
|Ratios dans le core|Core applique, pack décrit.|
|Rule ad hoc|Rule declarations dans pack uniquement.|
|`1:1:1` traité comme trois ratios séparés|`RatioSequence` distincte.|

### Exclusions

- golden ratio pack ;
- Modulor ;
- root rectangles riches ;
- user-defined packs ;
- pack registry ;
- pack signing ;
- packs métier ;
- multi-pack comparison.

### Peut rester stubbed, conceptuel ou minimal

- validation complète du format pack ;
- signature ;
- registry ;
- provenance riche ;
- schema final.

### Ne peut pas être repoussé

- pack id ;
- pack version ;
- content identity conceptuelle ;
- ratios minimaux ;
- `RatioSequence`;
- rule declarations ;
- rule set ;
- no beauty/no intention limits.

---

## Phase 4 — Rules et construction

### Objectif

Produire la construction proportionnelle source : guides, zones, grille simple, diagonales et intersections.

Une `Rule` décrit une transformation ou dérivation possible ; une `Construction` est le résultat structuré produit quand Norma applique une ou plusieurs rules à un espace. La construction n’est pas un export, la measurement n’est pas une évaluation, et l’évaluation n’est pas un jugement esthétique.

### Livrables conceptuels

- distinction `rule declaration` dans pack vs `rule type` dans core ;
- `resolveRuleSet` ;
- `generateConstruction` traçable ;
- `generateGuides` ;
- `generateZones` ;
- `generateSimpleGrid` ;
- `generateDiagonals` ;
- `deriveIntersections` ;
- `Construction` avec provenance ;
- `Guide` ;
- `Zone` ;
- `Grid` ;
- `GridCell` ;
- `IntersectionPoint`.

### Dépendances

- Phase 1 ;
- Phase 2 ;
- Phase 3.

### Critères de fin

La phase est terminée si la surface MVP peut produire :

- guides verticaux `x=1/3`, `x=1/2`, `x=2/3` ;
- guides horizontaux `y=1/3`, `y=1/2`, `y=2/3` ;
- grille `3 × 3` ;
- 9 cellules ;
- diagonale principale ;
- diagonale secondaire ;
- intersection centrale ;
- intersections guide-guide ;
- zones de tiers et cellules ;
- provenance pack/rules/operation/input ;
- warnings si rule incompatible, geometry invalid ou tolérance absente.

### Gate de validation

**Construction gate** : impossible de passer si `generateConstruction` ne peut pas expliquer quelles rules ont été appliquées et quels objets elles ont produits.

### Risques

|Risque|Protection|
|---|---|
|`generateConstruction` boîte noire|Trace des opérations et rules obligatoire.|
|Confondre construction et artifact|Construction = source geometry.|
|Rule dans core hardcodée comme système|Core supporte rule type ; pack déclare rule.|
|Grille devient produit entier|Grille = construction parmi d’autres.|

### Exclusions

- patterns complexes ;
- partitions avancées ;
- polygones ;
- courbes ;
- CAD constraints ;
- interprétation perceptive riche ;
- recommandation de construction.

### Peut rester stubbed, conceptuel ou minimal

- dominance de segments avancée ;
- patterns riches ;
- surface mass relations avancées ;
- construction graph complet ;
- detection robuste.

### Ne peut pas être repoussé

- guides ;
- zones ;
- grille simple ;
- diagonales ;
- intersections ;
- provenance ;
- trace de rules ;
- errors/warnings.

---

## Phase 5 — Measurements

### Objectif

Mesurer les constructions et compositions, sans encore scorer.

Une `Measurement` est un fait calculé. Elle dit ce qui est mesuré ; elle ne dit pas encore si c’est bon.

### Livrables conceptuels

- `DistanceMeasurement` ;
- `PositionMeasurement` ;
- `AlignmentMeasurement` ;
- `AreaMeasurement` ;
- `RatioMeasurement` ;
- `AngleMeasurement` ;
- `ContainmentMeasurement` ;
- `OverlapMeasurement` ;
- `CoverageMeasurement` ;
- `DirectionalRelation` minimal ;
- `SurfaceHierarchy` minimal ;
- measurement provenance ;
- measurement status/warnings.

### Dépendances

- Phase 2 ;
- Phase 4.

### Critères de fin

La phase est terminée si A et B peuvent produire :

- distances aux guides ;
- alignements bords/centres ;
- positions normalisées ;
- containment dans surface/zones ;
- overlap entre rectangles ;
- coverage des zones ;
- aires absolues/relatives ;
- ratios d’aires simples ;
- relations directionnelles basiques si utiles ;
- warnings pour overlap/gap/insufficient measurement.

### Gate de validation

**Measurement gate** : impossible de passer si un score peut être produit sans measurements traçables.

### Risques

|Risque|Protection|
|---|---|
|Measurement devient jugement|Measurement = fait calculé uniquement.|
|Mesures sans espace de référence|Chaque measurement référence source geometry/context.|
|Métrique implicite|`MetricPolicy` obligatoire.|
|Tolérance implicite|`TolerancePolicy` obligatoire.|

### Exclusions

- perception avancée ;
- esthétique ;
- intention ;
- ML-based detection ;
- image features ;
- mesure CAD native ;
- géométrie complexe.

### Peut rester stubbed, conceptuel ou minimal

- formules fines de confidence ;
- relations directionnelles avancées ;
- surface mass center avancé ;
- patterns complexes.

### Ne peut pas être repoussé

- distance aux guides ;
- alignment ;
- area ;
- containment ;
- overlap ;
- coverage ;
- provenance ;
- warnings.

---

## Phase 6 — Evaluation, scoring minimal et comparison

### Objectif

Évaluer A et B selon un profile explicite, puis comparer leur correspondance au système déclaré.

Norma peut évaluer une cohérence géométrique mesurable par rapport à un système proportionnel déclaré, mais ne doit jamais prétendre évaluer la beauté, l’intention, la qualité artistique universelle ou la valeur esthétique absolue.

### Livrables conceptuels

- `EvaluationProfile` minimal ;
- `evaluateCompositionBasic` ;
- `Score` minimal par components ;
- `Confidence` séparée ;
- `Decision` ;
- `Explanation` structurée ;
- `compareCompositionsBasic` ;
- statuses : `match`, `near_match`, `weak_match`, `no_match`, `ambiguous`, `tie`, `non_comparable`.

Profile recommandé :

```
basic-grid-alignment
```

Components conceptuels :

|Component|Poids conceptuel|Source|
|---|---|---|
|`guide_proximity`|30 %|distances aux guides|
|`alignment`|25 %|bords/centres alignés|
|`containment`|15 %|elements dans zones|
|`overlap_penalty`|15 %|overlaps rectangles|
|`coverage_match`|10 %|couverture de zones|
|`area_ratio_match`|5 %|ratios d’aires simples|

Ce profile reprend le brief MVP : il lit des measurements, déclare poids/tolérances/status/confidence/tie policy, et interdit beauté, intention, style ou préférence créative.

### Dépendances

- Phase 3 ;
- Phase 5 ;
- Phase 8 conceptuelle pour `PackLock` / `OperationContext` si comparison.

### Critères de fin

La phase est terminée si :

- A peut être évaluée ;
- B peut être évaluée ;
- chaque evaluation référence pack, profile, measurements, tolérances et context ;
- component scores sont visibles ;
- score global est optionnel et explicable ;
- confidence est séparée du score ;
- comparison A/B produit `a_closer`, `b_closer`, `tie`, `ambiguous` ou `non_comparable` ;
- explanation référence measurements et écarts ;
- beauty score est impossible ;
- intention claim est impossible.

### Gate de validation

**Evaluation gate** : impossible de passer si un score existe sans pack, profile, measurements ou tolérances.

### Risques

|Risque|Protection|
|---|---|
|Score devient vérité|Score = résumé, evaluation = analyse.|
|Confidence mélangée au score|Champs séparés.|
|Comparaison hors contexte|Même pack/profile/tolérances/context obligatoire.|
|Beauty score déguisé|Anti-beauty gate obligatoire.|

### Exclusions

- recommandation créative ;
- optimisation automatique ;
- “best layout” ;
- multi-pack ranking ;
- esthétique universelle ;
- intention ;
- modèle perceptif riche.

### Peut rester stubbed, conceptuel ou minimal

- formules exactes de score ;
- seuils définitifs ;
- confidence formula fine ;
- duplicate/mirror policy avancée.

### Ne peut pas être repoussé

- pas de score sans measurements ;
- pas de score sans profile ;
- pas de score sans pack ;
- pas de score sans tolérances ;
- confidence séparée ;
- decision traçable ;
- explanation traçable ;
- anti-beauty rule.

---

## Phase 7 — Artifacts structurés et visual artifact simple

### Objectif

Produire des représentations dérivées des résultats, sans jamais les transformer en source de vérité.

Un `Artifact` est une représentation dérivée d’un résultat Norma. Il peut représenter construction, measurements, evaluation, decision ou explanation, mais ne doit jamais devenir source de vérité. Si un SVG contredit la construction, la construction gagne.

### Livrables conceptuels

- `StructuredResultArtifact` ;
- `ConstructionSummaryArtifact` ;
- `EvaluationReportArtifact` ;
- `ExplanationArtifact` ;
- `SimpleVisualArtifact` limité ;
- artifact provenance ;
- artifact status : `current`, `lossy`, `stale`, `non_replayable` ;
- warning `ArtifactIsDerived`.

Les opérations d’artifacts doivent être déclarées pour éviter que chaque client produise ses artifacts “à sa façon” : `createStructuredResultArtifact`, `createConstructionSummaryArtifact`, `createEvaluationReportArtifact`, `createExplanationArtifact`, `createSimpleVisualArtifact`.

### Dépendances

- Phase 4 ;
- Phase 5 ;
- Phase 6 ;
- Phase 8 conceptuelle pour `Run` refs.

### Critères de fin

La phase est terminée si :

- l’artifact structuré référence construction, measurements, evaluation, decision, explanation, pack et run ;
- le visual artifact montre surface, guides, grille, diagonales, compositions A/B et labels minimaux ;
- le visual artifact déclare ses sources ;
- un artifact peut être marqué lossy ;
- un artifact peut être marqué stale ;
- modifier l’artifact ne modifie pas le résultat source ;
- warnings critiques sont visibles dans les artifacts pertinents.

### Gate de validation

**Artifact gate** : impossible de passer si un artifact peut contenir un ratio, une rule, une measurement, un score ou une explanation absente des source objects Norma.

### Risques

|Risque|Protection|
|---|---|
|SVG devient modèle|Artifact dérivé seulement.|
|Artifact invente une explanation|Sources obligatoires.|
|Export cache warnings|Warnings dans artifact.|
|Visual demo remplace output structuré|Structured artifact d’abord.|

### Exclusions

- DXF robuste ;
- PDF report ;
- PNG overlay ;
- plugin payload ;
- visual style riche ;
- édition visuelle ;
- artifact comme input.

### Peut rester stubbed, conceptuel ou minimal

- style visuel ;
- layout exact du visual artifact ;
- format final ;
- export externe ;
- stale verification complète.

### Ne peut pas être repoussé

- source refs ;
- provenance ;
- artifact status ;
- no source-of-truth rule ;
- structured artifact ;
- simple visual artifact limité.

---

## Phase 8 — Run, PackLock, OperationContext et replay-readiness

### Objectif

Rendre le MVP traçable, idempotent et replay-ready.

Norma doit pouvoir prouver pourquoi un résultat existe, avec quelles entrées, versions, règles, tolérances et sources. La règle d’idempotence est : même input structuré + même pack + mêmes rules + mêmes tolérances + même système de coordonnées + même version d’opération + même contexte = même output.

### Livrables conceptuels

- `Run` ;
- `PackLock` ;
- `OperationContext` ;
- deterministic ordering ;
- mismatch policy conceptuelle ;
- replay-readiness flags ;
- output refs ;
- warnings/errors ;
- status `success`, `partial`, `failed`, `non_replayable`, `stale`.

### Dépendances

- Phase 1 ;
- Phase 3 ;
- Phase 4 ;
- Phase 5 ;
- Phase 6 ;
- Phase 7.

Cette phase peut commencer conceptuellement dès Phase 1, mais elle devient complète quand construction, measurements, evaluation et artifacts existent.

### Critères de fin

La phase est terminée si :

- chaque résultat significatif référence un run ou runRef ;
- `PackLock` inclut pack id, version, schema version, content identity ;
- `OperationContext` inclut operation version, geometry model version, coordinate policy, metric policy, tolerance policy, numeric/rounding/ordering policy ;
- warnings/errors sont présents ;
- outputRefs relient construction, measurements, evaluation, decision, explanation, artifacts ;
- mismatch pack/context/operation version produit warning/error ;
- `replayRun` complet reste V1.5, pas requis MVP strict.

### Gate de validation

**Replay-readiness gate** : impossible de passer si un résultat ne peut pas expliquer quelles dépendances déterminent son output.

### Risques

|Risque|Protection|
|---|---|
|Replay repoussé trop tard|`Run`, `PackLock`, `OperationContext` conceptuels dès MVP.|
|Confondre replay-ready et replayRun complet|`replayRun` opération complète V1.5.|
|Artifact utilisé comme source de replay|Run/source objects seulement.|
|Context incomplet|OperationContext obligatoire.|

### Exclusions

- replay opérationnel complet ;
- signature cryptographique ;
- registry de packs ;
- remote verification ;
- cache content-addressable complet ;
- hash exact final.

### Peut rester stubbed, conceptuel ou minimal

- canonicalization exacte ;
- hash exact ;
- signature ;
- replay engine complet ;
- storage durable.

### Ne peut pas être repoussé

- `Run` conceptuel ;
- `PackLock` conceptuel ;
- `OperationContext` conceptuel ;
- idempotence ;
- deterministic ordering ;
- mismatch warnings/errors ;
- replay-readiness.

---

## Phase 9 — Demo harness minimal “Surface proportionnelle évaluée”

### Objectif

Assembler le noyau MVP dans une démonstration minimale qui prouve le moteur sans dépendre d’une interface spectaculaire.

Le brief de démo recommande **Surface proportionnelle évaluée** : une surface rectangulaire, un pack de tiers, deux compositions A/B, puis construction, measurements, evaluation, comparison, explanation et artifacts. Cette variante couvre le cœur V1, parle à plusieurs publics, reste sans image/UI/plugin et est compatible avec replay.

### Livrables conceptuels

- scénario démo ;
- surface `1200 × 800` ou équivalent ;
- pack minimal `norma.basic-proportions@0.1.0` ;
- rule set `surface-basic-third-grid` ;
- composition A proche ;
- composition B moins proche ;
- evaluation profile `basic-grid-alignment` ;
- outputs structurés ;
- visual artifact simple ;
- warnings/errors visibles ;
- run/replay-readiness visible ;
- cas négatif minimal : pack implicite, ratio absent, profile absent, beauty score demandé ou tolérance absente.

### Dépendances

- Phases 0 à 8.

### Critères de fin

La phase est terminée si la démo montre :

- input structuré ;
- pack validé/verrouillé ;
- construction traçable ;
- guides/zones/grille/diagonales/intersections ;
- measurements A et B ;
- evaluation A et B ;
- comparison A/B ;
- decision `a_closer`, `tie` ou `ambiguous` ;
- explanation depuis measurements ;
- structured artifact ;
- visual artifact simple ;
- Run, PackLock, OperationContext ;
- rejection d’un beauty score ou pack implicite ;
- même input + même pack + même contexte = même output.

### Gate de validation

**Demo truth gate** : la démo échoue si le public peut croire que le SVG, une UI, un plugin, une image, un agent ou un score esthétique est le produit.

### Risques

|Risque|Protection|
|---|---|
|Démo trop visuelle|Output structuré avant visual artifact.|
|Démo trop scoring|Measurements et component scores visibles.|
|Démo trop UI|Harness minimal seulement.|
|Démo trop large|Une surface, un pack, deux compositions.|
|Démo trop esthétique|“Plus proche du système”, jamais “meilleur/beau”.|

### Exclusions

- UI complète ;
- interactions riches ;
- caméra ;
- image ;
- plugin ;
- CAD natif ;
- cloud ;
- marketplace ;
- MCP complet ;
- recommandations ;
- optimisation automatique.

### Peut rester stubbed, conceptuel ou minimal

- présentation visuelle ;
- packaging de démo ;
- style graphique ;
- rapport humain complet ;
- export avancé.

### Ne peut pas être repoussé

- scénario A/B ;
- outputs structurés ;
- warnings/errors ;
- artifacts dérivés ;
- run/replay-readiness ;
- anti-beauty rejection ;
- pack/rule/profile/tolerance explicitness.

---

# 5. Ordre de construction recommandé

L’ordre recommandé est :

```
Spec→ Operation contracts→ Geometry→ Pack→ Rules→ Construction→ Measurements→ Evaluation→ Comparison→ Artifacts→ Run/replay-readiness→ Demo harness
```

## Pourquoi cet ordre réduit les risques

### 5.1 Éviter scoring avant measurements

Un score sans measurements devient une opinion.  
Le Chapitre 8 verrouille que le score doit être dérivé de measurements, relatif à un pack/profile/context/tolérances, et séparé de la confidence.

Règle :

> **Aucun score avant measurements traçables.**

---

### 5.2 Éviter artifacts avant constructions

Un artifact avant construction devient modèle.  
Le Chapitre 9 verrouille que l’artifact est une projection dérivée, pas la source de vérité.

Règle :

> **Aucun artifact source avant source objects Norma.**

---

### 5.3 Éviter interface avant opérations

Une interface trop tôt impose sa syntaxe, ses defaults et ses contraintes.

Règle :

> **Les interfaces exposent les opérations ; elles ne définissent pas les opérations.**

---

### 5.4 Éviter demo visuelle avant output structuré

Si le SVG arrive trop tôt, la démo devient un dessin.

Règle :

> **Structured output d’abord ; visual artifact ensuite.**

---

### 5.5 Éviter replay repoussé trop tard

Si `Run`, `PackLock` et `OperationContext` arrivent à la fin, les outputs précédents seront difficiles à rendre reproductibles.

Règle :

> **Replay-readiness doit influencer les contrats dès le début.**

---

### 5.6 Éviter packs riches avant pack minimal

Un pack riche masque les bugs de modèle et élargit le débat.

Règle :

> **Un pack minimal qui marche vaut mieux qu’une bibliothèque proportionnelle instable.**

---

### 5.7 Éviter MCP/CLI/SDK avant opérations stabilisées

MCP, CLI et SDK figent des contrats publics. Les stabiliser avant les operations risque de bloquer le core autour d’une mauvaise surface d’appel.

Règle :

> **Les contrats d’opération précèdent les contrats d’interface.**

---

# 6. Ce qui doit être stable avant toute interface riche

Avant CLI, SDK, API, MCP, plugins ou adapters, les éléments suivants doivent être stables :

|Élément|Pourquoi|
|---|---|
|Objets canoniques|Évite les synonymes et doubles modèles.|
|`Operation Call Contract`|Empêche chaque interface d’inventer ses inputs.|
|`Operation Result Contract`|Empêche chaque interface d’inventer ses outputs.|
|Status/errors/warnings|Empêche les échecs silencieux.|
|Pack minimal|Empêche ratios implicites.|
|Rule declarations / rule types|Sépare pack et core.|
|Construction model|Source géométrique stable.|
|Measurement model|Faits calculés traçables.|
|Evaluation profile minimal|Score relatif et explicable.|
|Artifact model|Exports dérivés, pas vérité.|
|`Run`|Enveloppe de reproductibilité.|
|`PackLock`|Verrou pack id/version/content.|
|`OperationContext`|Contexte computationnel explicite.|
|Provenance|Explication et audit.|
|Deterministic ordering|Même output stable.|
|Anti-beauty rules|Protège la crédibilité.|

Aucune interface, function, tool, SDK method, CLI command ou MCP tool ne doit exposer une capacité qui ne correspond pas à une opération Norma déclarée. Les operation calls/results doivent porter operation, version, input, context, refs nécessaires, status, run/runRef, warnings, errors et provenance.

---

# 7. Ce qui reste hors roadmap MVP

|Hors roadmap MVP|Pourquoi|
|---|---|
|Caméra|Introduit calibration, device state, tracking, confiance capteur.|
|Image|Le core V1 reçoit des données structurées, pas des pixels.|
|Vision|Change le problème : détection au lieu de géométrie proportionnelle.|
|OpenCV|Dépendance vision hors core.|
|Tracking|Temporalité, état, device, non nécessaire au MVP.|
|Plugin|Risque de laisser l’outil externe définir le modèle.|
|CAD natif|Format/contraintes trop riches, hors géométrie V1.|
|Cloud|Ajoute réseau, auth, stockage, état distribué.|
|Marketplace|Gouvernance trop tôt.|
|UI complète|Détourne de la preuve moteur.|
|API cloud|Transport distant prématuré.|
|MCP complet|Risque agent/tool qui invente des capacités.|
|SDK complet|Risque de figer une surface trop tôt.|
|Recommandations créatives|Glisse vers optimisation et jugement subjectif.|
|Optimisation automatique|Pas nécessaire pour prouver mesurer/évaluer/comparer.|
|Beauty score|Explicitement interdit.|
|Inférence d’intention|Non mesurable dans V1.|
|3D|Nouveau modèle géométrique.|
|Polygones complexes|Explosion de complexité géométrique.|
|Formats natifs|Risque source-of-truth externe.|

Le brief de démo liste déjà ces anti-démos : caméra, image detection, screenshot import, OpenCV, plugins, CAD natif, UI riche, recommandations créatives, beauty score, agent autonome, SVG comme input, cloud et marketplace doivent rester hors MVP.

---

# 8. Gates de validation

## 8.1 Spec gate

Pour passer :

- définition MVP stable ;
- V1 strict listé ;
- exclusions listées ;
- source de vérité claire ;
- no camera/image/plugin/CAD/cloud/UI complete ;
- no beauty score.

Échec si :

- une capacité future est incluse comme MVP ;
- un terme central reste ambigu ;
- un artifact peut devenir source.

---

## 8.2 Operation contract gate

Pour passer :

- chaque operation a un nom conceptuel ;
- chaque operation a une version conceptuelle ;
- input structuré ;
- context explicite ;
- result structuré ;
- status/warnings/errors/provenance ;
- no pack/rule/tolerance implicit.

Échec si :

- prompt libre accepté comme input ;
- operation opaque ;
- résultat sans warnings/errors ;
- result sans run/runRef pour operation significative.

---

## 8.3 Geometry gate

Pour passer :

- `SurfaceSpace` axis-aligned ;
- `Composition2D` simple ;
- coordinates normalisées ;
- metric policy explicite ;
- tolerance policy déclarée ;
- primitives V1 seulement.

Échec si :

- image, layer natif, CAD object, polygone complexe, courbe ou rectangle tourné entre dans le core.

---

## 8.4 Pack gate

Pour passer :

- pack id ;
- pack version ;
- schema version conceptuelle ;
- content identity ;
- ratios minimaux ;
- `RatioSequence 1:1:1` ;
- rule declarations ;
- rule set ;
- limits no beauty/no intention.

Échec si :

- ratio hardcodé dans core/client ;
- pack absent accepté ;
- rule ad hoc acceptée.

---

## 8.5 Construction gate

Pour passer :

- guides ;
- zones ;
- grille ;
- diagonales ;
- intersections ;
- provenance ;
- trace rule → output.

Échec si :

- construction produite sans rule source ;
- `generateConstruction` cache sa logique ;
- SVG utilisé comme source.

---

## 8.6 Measurement gate

Pour passer :

- distances ;
- positions ;
- alignments ;
- aires ;
- containment ;
- overlap ;
- coverage ;
- status/warnings ;
- provenance.

Échec si :

- measurement sans source geometry ;
- metric/tolerance implicite ;
- score calculé avant measurements.

---

## 8.7 Evaluation gate

Pour passer :

- profile explicite ;
- pack explicite ;
- measurements sources ;
- component scores ;
- confidence séparée ;
- decision traçable ;
- explanation traçable ;
- tie/ambiguous/non_comparable possibles.

Échec si :

- score sans profile ;
- score sans measurements ;
- beauty/intention claim ;
- comparison avec contexts différents acceptée.

---

## 8.8 Artifact gate

Pour passer :

- structured artifact ;
- construction summary ;
- evaluation report ;
- explanation artifact ;
- simple visual artifact ;
- source refs ;
- provenance ;
- status current/lossy/stale/non_replayable.

Échec si :

- SVG devient modèle ;
- artifact invente une rule/ratio/measurement/score ;
- warnings masqués.

---

## 8.9 Replay-readiness gate

Pour passer :

- `Run` visible ;
- `PackLock` visible ;
- `OperationContext` visible ;
- outputRefs ;
- deterministic ordering ;
- mismatch policy ;
- replay-ready, sans promettre `replayRun` complet.

Échec si :

- output dépend d’état UI/session/timestamp ;
- pack content mismatch ignoré ;
- context incomplet ;
- artifact utilisé comme source de replay.

---

## 8.10 Warning/error gate

Pour passer :

- warnings/errors structurés ;
- severity ;
- targetRef ;
- source ;
- blocking flag ;
- provenance ;
- critical warnings non masqués.

Échec si :

- erreur silencieuse ;
- warning critique transformé en success simple ;
- client/agent/adapter peut supprimer warnings.

Le shape minimal `Error` / `Warning` doit inclure code, severity, message, targetRef, source, blocking et provenance ; les warnings critiques et errors ne doivent jamais être supprimés.

---

## 8.11 Anti-beauty gate

Pour passer :

- aucune sortie ne dit “beau”, “meilleur”, “qualité universelle” ;
- score toujours relatif ;
- explanation toujours dérivée ;
- no intention claim ;
- no creative recommendation.

Échec si :

- “A est meilleure” ;
- “score esthétique” ;
- “l’auteur voulait…” ;
- “make it better”.

---

## 8.12 Demo truth gate

Pour passer :

- la démo montre d’abord output structuré ;
- visual artifact seulement après ;
- Run/PackLock/OperationContext visibles ;
- A/B comparison relative ;
- warnings visibles ;
- cas de rejet contrôlé ;
- même input + même pack + même context = même output.

Échec si :

- démo perçue comme SVG demo ;
- démo perçue comme UI app ;
- démo perçue comme beauty scorer ;
- démo dépend d’image/plugin/cloud/agent.

---

# 9. Risques de roadmap

|Risque|Règle de protection|
|---|---|
|Scope creep|Chaque phase doit déclarer exclusions.|
|UI trop tôt|Core outputs structurés avant toute interface riche.|
|Scoring trop tôt|Aucun score avant measurements/profile/pack/tolérances.|
|Visual artifact source-of-truth|Artifact dérivé seulement ; source objects gagnent toujours.|
|Pack implicite|Pack absent = erreur ou warning critique.|
|Tolérances implicites|Toute tolérance qui change un résultat doit être déclarée.|
|`OperationContext` incomplet|Context requis dans chaque operation significative.|
|`Run` repoussé trop tard|Run conceptuel dès contrats d’opération.|
|Replay confondu avec `replayRun` complet|Replay-readiness V1 strict ; `replayRun` V1.5.|
|MCP trop tôt|MCP seulement après operation contracts stabilisés.|
|CLI/SDK impose l’API|Interfaces wrappers, pas source du modèle.|
|`generateConstruction` boîte noire|Trace rule → object obligatoire.|
|Warnings masqués|`critical_warning` et `error` jamais supprimés.|
|Démo SVG|Structured artifact d’abord, visual artifact ensuite.|
|Démo promesse esthétique|“Plus proche du système déclaré”, jamais “plus beau”.|
|Pack riche trop tôt|Un pack minimal seulement.|
|Comparison abusive|Même pack/profile/tolérances/context obligatoires.|
|Agent autonome|Hors MVP ; agent-readiness seulement conceptuelle.|
|Defaults cachés|Tout default qui change le résultat doit être explicite, versionné ou rejeté.|

Le brief de démo identifie déjà les protections critiques : montrer d’abord les outputs structurés, limiter le visual artifact, éviter l’agent autonome, refuser le beauty score, garder `Run`/`PackLock` visibles et exposer les warnings.

---

# 10. MVP exit criteria

Le MVP est terminé seulement si tous les critères suivants sont vrais.

## 10.1 Core geometry

- une surface structurée peut être créée ;
- une composition 2D simple peut être créée ;
- les éléments rectangulaires sont validés ;
- le coordinate system est explicite ;
- metric/tolerance policies sont visibles.

## 10.2 Pack

- le pack minimal peut être validé ;
- le pack minimal peut être verrouillé ;
- `PackLock` expose id, version, schema version, content identity ;
- ratio absent = erreur ;
- rule absente = erreur ;
- pack implicite = rejet.

## 10.3 Rules/construction

- le rule set minimal peut être résolu ;
- la construction est traçable ;
- guides verticaux/horizontaux produits ;
- zones produites ;
- grille `3 × 3` produite ;
- diagonales produites ;
- intersections produites ;
- chaque objet dérivé a provenance.

## 10.4 Measurements

- deux compositions simples peuvent être mesurées ;
- distances aux guides produites ;
- alignments produits ;
- aires produites ;
- containment produit ;
- overlap produit ;
- coverage produit ;
- warnings structurés produits si nécessaire.

## 10.5 Evaluation/comparison

- deux evaluations peuvent être produites avec le même profile ;
- component scores visibles ;
- confidence séparée ;
- comparison A/B produit `a_closer`, `b_closer`, `tie`, `ambiguous` ou `non_comparable` ;
- comparison impossible si pack/profile/tolérances/context diffèrent ;
- une tentative de beauty score est rejetée.

## 10.6 Explanation

- une explanation structurée peut être produite ;
- elle référence measurements, écarts, tolérances, profile, pack et warnings ;
- elle ne contient pas d’intention supposée ;
- elle ne contient pas de claim esthétique.

## 10.7 Artifacts

- un `StructuredResultArtifact` peut être produit ;
- un `ConstructionSummaryArtifact` peut être produit ;
- un `EvaluationReportArtifact` peut être produit ;
- un `ExplanationArtifact` peut être produit ;
- un `SimpleVisualArtifact` peut être produit comme projection dérivée ;
- aucun artifact ne devient source de vérité ;
- les artifacts exposent provenance et warnings.

## 10.8 Run/replay-readiness

- `Run` visible ;
- `PackLock` visible ;
- `OperationContext` visible ;
- operation/version/input/context/outputRefs visibles ;
- warnings/errors visibles ;
- même input + même pack + même rules + mêmes tolérances + même context + même operation version = même output ;
- mismatch pack/context/operation version produit warning/error ;
- `replayRun` complet non requis.

## 10.9 Demo truth

- la démo **Surface proportionnelle évaluée** fonctionne conceptuellement de bout en bout ;
- elle utilise une seule surface ;
- un seul pack minimal ;
- deux compositions A/B ;
- un profile ;
- des outputs structurés ;
- un visual artifact simple ;
- un cas de rejet ou warning contrôlé ;
- aucune caméra/image/plugin/CAD/cloud/UI complète/marketplace.

---

# 11. Décisions à verrouiller

Décisions copiables dans la spec globale ou le document de roadmap :

1. **La roadmap MVP construit le moteur Norma Core, pas une UI, pas une caméra, pas un plugin, pas une API cloud et pas une marketplace.**
2. **La roadmap MVP suit l’ordre : spec → operation contracts → geometry → pack → rules → construction → measurements → evaluation → comparison → artifacts → Run/replay-readiness → demo harness.**
3. **Les contrats d’opération doivent être stables avant toute interface riche.**
4. **Les données structurées doivent être stables avant tout rendu.**
5. **Le pack minimal doit être stable avant tout pack riche.**
6. **Les rules doivent être résolues avant toute construction.**
7. **Les constructions doivent être produites avant toute measurement.**
8. **Les measurements doivent exister avant toute evaluation, score, decision ou explanation.**
9. **Aucun score ne doit exister sans measurements, profile, pack et tolérances.**
10. **Une comparison A/B est autorisée seulement si A et B partagent le même pack, pack lock, profile, tolérances, surface, coordinate system, metric policy et operation context.**
11. **Les artifacts doivent être produits après les source objects Norma et rester des représentations dérivées.**
12. **Le visual artifact simple est autorisé dans le MVP uniquement comme projection dérivée.**
13. **Aucun SVG, export ou rendu ne doit devenir source de vérité.**
14. **`Run`, `PackLock` et `OperationContext` doivent être visibles dans le MVP.**
15. **Replay-readiness est MVP ; `replayRun` opérationnel complet est V1.5.**
16. **Warnings/errors doivent être structurés dès le début et ne doivent jamais être masqués.**
17. **`generateConstruction` peut être orchestratrice, mais ne doit jamais être opaque.**
18. **La démo MVP recommandée reste “Surface proportionnelle évaluée”.**
19. **La démo MVP doit prouver la reproductibilité avant l’ergonomie.**
20. **Caméra, image, vision, OpenCV, tracking, plugins, CAD natif, cloud, marketplace, UI complète, MCP complet, SDK complet, recommandations créatives, optimisation automatique, beauty score, inférence d’intention, 3D, polygones complexes et formats natifs restent hors roadmap MVP.**