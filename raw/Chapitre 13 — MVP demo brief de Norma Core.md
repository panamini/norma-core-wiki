
## 1. Verdict sur la démo MVP

La démo MVP doit prouver une seule chose :

> **Norma Core peut recevoir une surface géométrique structurée, appliquer un ratio pack versionné, générer une construction proportionnelle, mesurer deux compositions 2D simples, les évaluer selon un profil explicite, comparer leur correspondance au système déclaré, produire des explanations et des artifacts dérivés, le tout de manière déterministe et replay-ready.**

Elle doit prouver le moteur, pas l’emballage.

La démo reprend la chaîne centrale déjà verrouillée :

```txt
structured input
→ ratio pack versionné
→ rule set explicite
→ construction
→ measurements
→ evaluation A/B
→ comparison
→ decision
→ explanation
→ artifacts
→ Run / PackLock / replay-readiness
```

La version collée formule correctement ce principe : la démo doit montrer que Norma applique et évalue un système proportionnel sur une composition structurée simple, sans prétendre comprendre toute composition visuelle.

### Ce que la démo doit prouver

La démo doit prouver que Norma sait :

- accepter des inputs géométriques structurés ;
    
- valider un ratio pack minimal ;
    
- verrouiller un `PackLock` ;
    
- résoudre des ratios, une `RatioSequence` et un `RuleSet` ;
    
- générer guides, zones, grille simple, diagonales et intersections ;
    
- créer ou valider deux compositions 2D simples ;
    
- mesurer distances, positions, alignements, aires, containment, overlap et coverage ;
    
- évaluer chaque composition selon un `EvaluationProfile` ;
    
- comparer A et B dans le même contexte ;
    
- produire une `Decision` limitée ;
    
- produire une `Explanation` traçable ;
    
- produire des artifacts structurés ;
    
- produire un `SimpleVisualArtifact` comme projection dérivée ;
    
- exposer warnings/errors ;
    
- relier le résultat à un `Run`.
    

### Ce que la démo ne doit pas chercher à prouver

Elle ne doit pas prouver que Norma sait :

- analyser une image ;
    
- détecter des objets visuels ;
    
- utiliser une caméra ;
    
- faire du tracking ;
    
- importer Figma, AutoCAD, Rhino, Blender ou Revit ;
    
- produire un plugin ;
    
- produire une UI complète ;
    
- recommander une correction créative ;
    
- choisir automatiquement le “meilleur” système proportionnel ;
    
- juger la beauté ;
    
- inférer l’intention de l’auteur ;
    
- générer une composition finale.
    

Phrase à verrouiller :

> **La démo MVP ne montre pas que Norma comprend toute composition visuelle. Elle montre que Norma applique, mesure, compare et explique un système proportionnel déclaré sur des données géométriques structurées.**

---

## 2. Scénario de démo recommandé

## 2.1 Nom recommandé

> **Démo MVP — Surface proportionnelle évaluée**

C’est la meilleure variante. La version collée recommande aussi cette variante parce qu’elle couvre le cœur V1 tout en restant hors caméra, image, CAD, plugin, UI complète et scoring esthétique.

## 2.2 Scénario court

Norma reçoit :

1. une surface rectangulaire abstraite ;
    
2. un ratio pack minimal ;
    
3. un rule set de construction ;
    
4. deux compositions simples A et B ;
    
5. un evaluation profile ;
    
6. des tolérances explicites ;
    
7. un operation context ;
    
8. une demande d’outputs structurés et d’artifacts.
    

Norma produit :

1. une construction proportionnelle ;
    
2. guides, zones, grille simple, diagonales, intersections ;
    
3. measurements pour A ;
    
4. measurements pour B ;
    
5. evaluation A ;
    
6. evaluation B ;
    
7. comparison A/B ;
    
8. decision ;
    
9. explanation ;
    
10. artifacts structurés ;
    
11. visual artifact simple ;
    
12. run/replay envelope.
    

## 2.3 Surface de démonstration

Surface recommandée :

|Champ|Valeur|
|---|---|
|`spaceType`|`SurfaceSpace`|
|`width`|`1200`|
|`height`|`800`|
|`unit`|`unitless` ou `px`, mais déclaré|
|`coordinateSystem`|Norma canonical|
|`origin`|bottom-left|
|`xAxis`|right|
|`yAxis`|up|
|`normalizedBounds`|`[0,0] → [1,1]`|
|`geometryModelVersion`|V1|

Cette surface est un objet géométrique structuré. Elle n’est pas un canvas UI, pas une image, pas un SVG, pas un écran.

## 2.4 Pack minimal recommandé

Pack conceptuel :

```txt
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

Le pack doit rester petit. Le but est de prouver l’application d’un pack versionné, pas de montrer une bibliothèque de systèmes proportionnels.

Le pack ne doit pas contenir de code, UI, rendu, plugin, modèle IA, scoring esthétique ou claims non qualifiés. La spec consolidée verrouille que les packs contiennent ratios, sequences, rule declarations, rule sets, conventions, provenance et limits, tandis que les rule types et algorithmes vivent dans le core.

## 2.5 Construction proportionnelle

À partir du pack et du rule set, Norma génère :

|Objet|Résultat attendu|
|---|---|
|Guides verticaux|`x = 1/3`, `x = 1/2`, `x = 2/3`|
|Guides horizontaux|`y = 1/3`, `y = 1/2`, `y = 2/3`|
|Grille|`3 × 3`|
|Cellules|9 cellules rectangulaires|
|Diagonales|diagonale principale + diagonale secondaire|
|Intersections|centre, guide-guide, diagonale-diagonale, guide-bord|
|Zones|tiers verticaux, tiers horizontaux, cellules|
|Measurements associées|positions, aires, distances, angles simples|
|Provenance|pack, rule set, operation, input|
|Warnings|zones nulles, incompatibilité rule, tolérance ambiguë si applicable|

Cette construction est la vérité géométrique dérivée. Le visual artifact ne fait que la représenter.

---

## 3. Inputs de la démo

## 3.1 Vue d’ensemble des inputs

|Input|Obligatoire|Rôle|
|---|--:|---|
|`surface`|Oui|Surface rectangulaire structurée|
|`ratioPack`|Oui|Source proportionnelle versionnée|
|`packLock`|Oui|Verrou pack id/version/schema/content identity|
|`ruleSet`|Oui|Rules déclarées à appliquer|
|`tolerancePolicy`|Oui|Tolérances de construction, mesure, évaluation, comparaison|
|`compositionA`|Oui|Candidate proche du système|
|`compositionB`|Oui|Candidate moins proche mais comparable|
|`evaluationProfile`|Oui|Politique de lecture des measurements|
|`operationContext`|Oui|Contexte déterministe|
|`requestedOutputs`|Oui|Construction, measurements, evaluations, comparison, artifacts|

## 3.2 PackLock

Le `PackLock` doit contenir :

|Champ conceptuel|Rôle|
|---|---|
|`packId`|`norma.basic-proportions`|
|`packVersion`|`0.1.0`|
|`packSchemaVersion`|version conceptuelle du format pack|
|`contentIdentity`|identité conceptuelle du contenu|
|`compatibility`|V1|

Le MVP ne doit pas seulement afficher “basic proportions”. Il doit montrer que le pack est verrouillé. Les critères de réussite doivent échouer si le pack est absent, si un ratio demandé est absent, si une rule est absente, ou si le content identity change.

## 3.3 RuleSet

Rule set recommandé :

```txt
surface-basic-third-grid
```

Rules conceptuelles :

|Rule declaration|Rule type core attendu|
|---|---|
|`verticalThirds`|`divideSurfaceVertical`|
|`horizontalThirds`|`divideSurfaceHorizontal`|
|`centerAxes`|`createGuidesFromCandidates`|
|`thirdGrid`|`createSimpleGrid`|
|`surfaceDiagonals`|`createDiagonals`|
|`deriveIntersections`|`deriveIntersections`|

Règle stricte :

> **La rule declaration vit dans le pack ; le rule type et l’exécution vivent dans le core.**

## 3.4 Tolérances

Tolérances conceptuelles recommandées :

|Tolérance|Valeur indicative|Usage|
|---|--:|---|
|`guideDistanceTolerance`|`0.02` normalisé|Distance d’un bord/centre à un guide|
|`alignmentTolerance`|`0.02` normalisé|Alignement bord/centre|
|`areaRatioTolerance`|`0.03`|Écart d’aire relative|
|`overlapTolerance`|`0.00` ou faible|Overlap rectangulaire|
|`coverageTolerance`|`0.03`|Gap ou couverture de zone|
|`tieTolerance`|`0.03` score delta|A/B tie policy|
|`numericEpsilon`|déclaré|Comparaison numérique|

Les valeurs exactes peuvent rester conceptuelles, mais elles doivent être déclarées. Aucun seuil implicite ne doit changer le résultat.

## 3.5 Composition A

Composition A doit être clairement proche du système, sans être une composition créative finale.

Coordonnées normalisées :

|Élément|Type|`x`|`y`|`w`|`h`|Rôle optionnel|
|---|---|--:|--:|--:|--:|---|
|`header`|rect|`0`|`2/3`|`1`|`1/3`|top band|
|`side`|rect|`0`|`1/3`|`1/3`|`1/3`|middle-left cell|
|`main`|rect|`1/3`|`1/3`|`2/3`|`1/3`|middle-right band|
|`footer`|rect|`0`|`0`|`1`|`1/3`|bottom band|

Propriétés attendues :

- bords alignés avec guides ;
    
- zones couvertes proprement ;
    
- pas d’overlap significatif ;
    
- containment clair ;
    
- ratios d’aires lisibles ;
    
- confidence haute ;
    
- warnings faibles ou informatifs.
    

Données interdites :

- texte réel ;
    
- style ;
    
- couleur ;
    
- police ;
    
- layer natif ;
    
- screenshot ;
    
- image.
    

## 3.6 Composition B

Composition B doit être moins proche géométriquement, mais pas caricaturale.

Coordonnées normalisées :

|Élément|Type|`x`|`y`|`w`|`h`|Problème mesurable|
|---|---|--:|--:|--:|--:|---|
|`header`|rect|`0.04`|`0.62`|`0.92`|`0.29`|bords hors guides|
|`side`|rect|`0.03`|`0.29`|`0.31`|`0.34`|proche mais décalé|
|`main`|rect|`0.38`|`0.30`|`0.57`|`0.35`|bord gauche loin de `1/3`|
|`footer`|rect|`0.02`|`0.02`|`0.95`|`0.26`|hauteur loin de `1/3`|

Propriétés attendues :

- écarts aux guides ;
    
- alignements partiels ;
    
- containment moins net ;
    
- gaps ou coverage moins régulier ;
    
- overlap possible mais non obligatoire ;
    
- score inférieur à A ;
    
- explanation basée sur écarts mesurés.
    

La version collée donne déjà une logique solide pour B : elle doit produire des écarts mesurables, une évaluation moins forte, éventuellement des warnings de near match, overlap, gap ou low alignment, sans devenir un cas caricatural.

## 3.7 EvaluationProfile

Profile recommandé :

```txt
basic-grid-alignment
```

Le `EvaluationProfile` est une politique de lecture des measurements. Il ne crée pas de ratios, de rules, de measurements ou de claims esthétiques. La spec consolidée verrouille cette chaîne : `Measurement = fait calculé`, `EvaluationProfile = politique de lecture`, `Evaluation = application du profile`, `Score = résumé dérivé`, `Decision = conclusion structurée`, `Explanation = justification traçable`.

Components recommandés :

|Component|Poids conceptuel|Source|
|---|--:|---|
|`guide_proximity`|30 %|distances aux guides|
|`alignment`|25 %|bords/centres alignés|
|`containment`|15 %|éléments dans zones|
|`overlap_penalty`|15 %|overlaps rectangles|
|`coverage_match`|10 %|couverture des zones|
|`area_ratio_match`|5 %|ratios d’aires simples|

Le profile doit déclarer :

- measurements utilisées ;
    
- weights ;
    
- tolérances ;
    
- status thresholds ;
    
- confidence policy ;
    
- tie policy ;
    
- warnings obligatoires ;
    
- limits.
    

Interdiction :

> **Le profile ne doit pas contenir beauté, intention, style, goût ou préférence créative.**

## 3.8 OperationContext

Input obligatoire :

|Élément|Rôle|
|---|---|
|`coreVersion`|version conceptuelle du comportement core|
|`geometryModelVersion`|V1|
|`operationVersion`|version de chaque opération appelée|
|`coordinatePolicy`|Norma canonical|
|`metricPolicy`|distances, angles, aires, unités|
|`tolerancePolicy`|valeurs déclarées|
|`roundingPolicy`|arrondi déclaré|
|`numericPolicy`|précision, epsilon, irrationnels|
|`orderingPolicy`|tri stable|
|`featureFlags`|tout flag qui change le résultat|

Règle :

> **Tout ce qui peut changer le résultat doit apparaître dans l’input, le context, le pack lock, les rule refs, les tolerances, les policies, les feature flags ou l’operation version.**

---

## 4. Operations utilisées

Ordre conceptuel recommandé, sans code :

|Étape|Operation|But|
|--:|---|---|
|1|`validateRatioPack`|vérifier pack, ratios, sequences, rules, rule sets|
|2|`createSurfaceSpace`|créer/valider la surface rectangulaire|
|3|`resolveRuleSet`|résoudre `surface-basic-third-grid`|
|4|`resolveRatio`|résoudre `1/2`, `1/3`, `2/3`|
|5|`resolveRatioSequence`|résoudre `1:1:1`|
|6|`generateConstruction`|orchestrer la construction proportionnelle|
|7|`generateGuides`|produire guides verticaux/horizontaux|
|8|`generateZones`|produire bandes et zones|
|9|`generateSimpleGrid`|produire grille `3 × 3`|
|10|`generateDiagonals`|produire diagonales|
|11|`deriveIntersections`|produire points d’intersection|
|12|`createComposition`|valider composition A|
|13|`createComposition`|valider composition B|
|14|`measureGeometry`|mesurer positions, distances, alignements, containment|
|15|`measureAreas`|mesurer aires, ratios d’aires, overlap, coverage|
|16|`deriveDirectionalRelations`|relations basiques si utiles|
|17|`deriveSurfaceHierarchy`|hiérarchie surfacique simple si utile|
|18|`evaluateCompositionBasic`|évaluer A|
|19|`evaluateCompositionBasic`|évaluer B|
|20|`compareCompositionsBasic`|comparer A et B selon même contexte|
|21|`createStructuredResultArtifact`|produire résultat structuré|
|22|`createConstructionSummaryArtifact`|produire résumé de construction|
|23|`createEvaluationReportArtifact`|produire rapport d’évaluation|
|24|`createExplanationArtifact`|produire explanation traçable|
|25|`createSimpleVisualArtifact`|produire projection visuelle simple|
|26|`recordRun` conceptuel|relier input, pack, context, outputs, warnings/errors|

La spec consolidée inclut déjà ce type de registry conceptuel d’opérations V1, y compris les opérations d’artifacts, et classe `replayRun`, `verifyRun` et `verifyArtifactFreshness` en V1.5.

Règle importante :

> **`generateConstruction` peut être orchestratrice, mais ne doit jamais être magique. Elle doit retourner quelles rules ont été appliquées et quels objets chaque rule a produits.**

---

## 5. Outputs attendus

## 5.1 Construction

Sortie attendue :

|Objet|Exemple|
|---|---|
|`Construction`|construction issue du rule set|
|`Guide vertical`|`x=1/3`, `x=1/2`, `x=2/3`|
|`Guide horizontal`|`y=1/3`, `y=1/2`, `y=2/3`|
|`Zone`|tiers gauche/centre/droit ; tiers bas/milieu/haut|
|`Grid`|grille `3 × 3`|
|`GridCell`|9 cellules|
|`Segment diagonal`|diagonale principale et secondaire|
|`IntersectionPoint`|centre, intersections guide-guide, guide-bord|
|`AreaMeasurement`|aire de chaque zone/cellule|
|`Provenance`|pack, rule, operation, input source|
|`Warnings`|zones nulles, rule incompatible, tolérance ambiguë si applicable|

## 5.2 Measurements

Pour chaque composition :

|Measurement|Attendu|
|---|---|
|`GuideDistanceMeasurement`|distance des bords/centres aux guides|
|`AlignmentMeasurement`|alignements bord/centre|
|`ContainmentMeasurement`|inside / boundary / outside par zone|
|`OverlapMeasurement`|overlap rectangulaire entre elements|
|`CoverageMeasurement`|couverture des zones/cells par elements|
|`AreaMeasurement`|aire des elements et zones|
|`RatioMeasurement`|ratio d’aire ou de position si applicable|
|`DirectionalRelation`|above/below/left/right si utile|
|`SurfaceHierarchy`|ordre simple par aire si utile|

Une measurement ne dit pas si c’est “beau”. Elle dit ce qui est mesuré.

## 5.3 Evaluation A

Sortie attendue :

|Champ|Attendu|
|---|---|
|`evaluationId`|stable dans le run|
|`profile`|`basic-grid-alignment`|
|`packLock`|`norma.basic-proportions@0.1.0` + content identity|
|`componentScores`|guide proximity, alignment, containment, overlap, coverage, area ratio|
|`overallScore`|autorisé seulement comme résumé|
|`confidence`|séparée du score|
|`status`|`match` ou `near_match`|
|`warnings`|none ou informational|
|`limits`|comparaison relative au profile seulement|
|`explanation`|dérivée des measurements|

## 5.4 Evaluation B

Sortie attendue :

|Champ|Attendu|
|---|---|
|`evaluationId`|stable dans le run|
|`profile`|même profile que A|
|`packLock`|même pack lock que A|
|`componentScores`|plus faibles sur guide proximity/alignment|
|`overallScore`|inférieur à A, si le profile autorise un score global|
|`confidence`|moyenne ou haute selon mesures|
|`status`|`near_match`, `weak_match` ou `ambiguous`|
|`warnings`|offsets hors tolérance, possible overlap/gap|
|`limits`|comparaison relative au profile seulement|
|`explanation`|dérivée des écarts|

Exemple de conclusion valide :

> “Composition B présente plusieurs écarts aux guides : le bord gauche de `main` est éloigné de `x=1/3` au-delà de la tolérance déclarée. La correspondance au système est donc plus faible.”

## 5.5 Comparison

Sortie attendue :

|Champ|Attendu|
|---|---|
|`comparisonId`|stable dans le run|
|`inputs`|evaluation A + evaluation B|
|`samePack`|true|
|`samePackLock`|true|
|`sameProfile`|true|
|`sameTolerances`|true|
|`sameSurface`|true|
|`sameOperationContext`|true|
|`decision`|`a_closer`|
|`scoreDelta`|explicite|
|`tiePolicy`|déclarée|
|`warnings`|none, tie, ambiguous, non-comparable si besoin|
|`explanation`|raisons mesurées|

La comparaison est autorisée uniquement parce que A et B partagent pack, pack lock, profile, tolérances, surface, coordinate system, metric policy et operation context. La spec verrouille que `compareCompositionsBasic` est V1 strict seulement dans ce cadre, sans recommandation créative.

Formulation correcte :

> “Composition A est plus proche que Composition B du pack `norma.basic-proportions`, selon le profile `basic-grid-alignment`, les tolérances déclarées et les measurements calculées.”

Formulations interdites :

> “Composition A est meilleure.”

> “Composition A est plus belle.”

> “L’auteur voulait utiliser les tiers.”

## 5.6 Explanation

L’explication doit être structurée.

Elle doit contenir :

- claim principal ;
    
- measurements sources ;
    
- écarts aux guides ;
    
- tolérances ;
    
- component scores ;
    
- confidence ;
    
- warnings ;
    
- limits ;
    
- decision ;
    
- formulation humaine dérivée.
    

Exemple valide :

> “A est plus proche que B selon `basic-grid-alignment`, car ses bords principaux coïncident avec les guides de tiers, ses zones couvrent la grille sans overlap significatif, et ses écarts moyens aux guides sont inférieurs à la tolérance déclarée.”

Exemple interdit :

> “A est plus beau parce qu’il suit les tiers.”

## 5.7 Warnings

Warnings possibles :

|Warning|Quand|
|---|---|
|`NoAestheticClaim`|rappel si un report contient score/decision|
|`EvaluationProfileMinimal`|profile V1 simple|
|`NearGuideButOutsideTolerance`|élément proche mais hors tolérance|
|`OverlapDetected`|rectangles se chevauchent|
|`CoverageGapDetected`|zone attendue non couverte|
|`AmbiguousRanking`|score delta sous tie tolerance|
|`LowMeasurementCount`|pas assez de mesures|
|`ArtifactIsDerived`|visual artifact produit|
|`PackLockRequired`|content identity absente|
|`ReplayPartial`|dépendance de replay manquante|
|`OperationContextIncomplete`|policy manquante|
|`UnsupportedRuleType`|rule declaration non exécutable en V1|

Les warnings ne sont pas décoratifs. Ils font partie de la sortie. Les warnings critiques et errors ne doivent jamais être masqués par agents, adapters ou interfaces.

## 5.8 Artifacts structurés

Artifacts V1 attendus :

|Artifact|Rôle|
|---|---|
|`StructuredResultArtifact`|résultat machine-readable principal|
|`ConstructionSummaryArtifact`|résumé des guides, zones, grilles, intersections|
|`EvaluationReportArtifact`|scores, components, confidence, warnings|
|`ExplanationArtifact`|claims structurés + mesures sources|
|`SimpleVisualArtifact`|projection visuelle simple de la construction et des compositions|

Les artifacts sont des représentations dérivées. La vérité reste dans les objets structurés du core : input, pack, pack lock, construction, measurements, evaluation, decision, explanation, run et operation context. La spec rappelle qu’un artifact doit déclarer source objects, source run/ref, pack lock, format, options, provenance, warnings, limitations, lossiness, replayability et stale status.

## 5.9 Visual artifact simple

Le visual artifact peut montrer :

- rectangle de surface ;
    
- guides de tiers ;
    
- axes centraux ;
    
- diagonales ;
    
- grille `3 × 3` ;
    
- composition A en overlay ;
    
- composition B en overlay séparé ou côte à côte ;
    
- labels minimaux ;
    
- warnings visibles.
    

Interdictions :

- le SVG ne contient pas de ratios nouveaux ;
    
- le SVG ne devient pas modèle ;
    
- les coordonnées SVG ne remplacent pas les coordonnées Norma ;
    
- les couleurs ne portent pas de vérité core ;
    
- les layers ne deviennent pas objets core.
    

Phrase à afficher dans le brief :

> **Le visual artifact aide à lire le résultat. Il n’est pas la source du résultat.**

## 5.10 Run / replay output

La démo doit produire ou exposer conceptuellement :

|Objet|Contenu|
|---|---|
|`Run`|operation, operation version, input, context, outputs, warnings/errors|
|`PackLock`|pack id, pack version, schema version, content identity|
|`OperationContext`|coordinate policy, tolerance policy, numeric policy, ordering policy|
|`OutputRefs`|construction, measurements, evaluations, decision, artifacts|
|`Status`|success, partial, failed, stale, nonReplayable|
|`Replay readiness`|mêmes dépendances → même résultat|

Règle :

> **Même input + même pack + mêmes rules + mêmes tolérances + même contexte + même version d’opération = même output.**

La version collée intègre déjà ce point dans les critères de replay-readiness : `Run`, `PackLock`, `OperationContext`, mismatches explicites et absence de dépendance à UI, fichier natif, plugin ou SVG.

---

## 6. Critères de réussite

## 6.1 Critères déterministes

La démo réussit si :

|Critère|Test attendu|
|---|---|
|Même input, même output|relancer produit mêmes guides, zones, mesures, scores et artifacts sources|
|Ordre stable|guides, zones, measurements toujours ordonnés pareil|
|Pas d’état caché|aucun résultat ne dépend d’un timestamp, viewport, thème, session ou ordre UI|
|Pack explicite|aucun ratio utilisé hors pack|
|Rule explicite|aucune construction produite sans rule source|
|Tolérances explicites|aucun seuil implicite|
|Context explicite|coordinate, metric, numeric, rounding, ordering policies déclarées|
|Operation version|chaque operation significative porte sa version conceptuelle|

## 6.2 Critères de PackLock

La démo réussit si :

- le résultat référence `packId` ;
    
- le résultat référence `packVersion` ;
    
- le résultat référence `packSchemaVersion` ;
    
- le résultat référence `contentIdentity` ;
    
- changer le contenu du pack change ou invalide le replay ;
    
- pack absent = erreur ;
    
- ratio absent = erreur ;
    
- rule absente = erreur ;
    
- version incompatible = erreur ou warning critique.
    

## 6.3 Critères d’évaluation

La démo réussit si :

- score impossible sans measurements ;
    
- score impossible sans profile ;
    
- score impossible sans pack ;
    
- score impossible sans tolérances ;
    
- component scores visibles ;
    
- confidence séparée du score ;
    
- warnings visibles ;
    
- tie/ambiguous possible ;
    
- comparaison A/B limitée au même contexte ;
    
- aucune phrase ne dit “beau”, “meilleur”, “qualité universelle” ou “intentionnel”.
    

## 6.4 Critères d’artifact

La démo réussit si :

- l’artifact structuré référence ses sources ;
    
- le visual artifact référence la construction/run ;
    
- modifier le SVG ne modifie pas la vérité core ;
    
- un artifact peut être stale ;
    
- un artifact peut être lossy ;
    
- les warnings critiques apparaissent dans les artifacts pertinents.
    

## 6.5 Critères de replay-readiness

La démo réussit si :

- le `Run` contient operation, input, pack, rules, context, tolerances, outputs, warnings/errors ;
    
- le résultat peut être rejoué conceptuellement ;
    
- un mismatch de pack produit erreur/warning ;
    
- un mismatch de coordinate policy produit erreur/warning ;
    
- un mismatch d’operation version produit erreur/warning ;
    
- le replay ne dépend pas d’une UI, d’un fichier natif, d’un plugin, d’une caméra ou d’un SVG.
    

## 6.6 Critères de failure contrôlée

La démo doit aussi montrer au moins un cas de rejet ou warning contrôlé :

|Cas|Résultat attendu|
|---|---|
|ratio absent du pack|erreur structurée|
|rule absente du pack|erreur structurée|
|pack lock incomplet|warning critique ou erreur|
|profile absent|evaluation impossible|
|composition avec overlap|warning ou component penalty|
|comparaison avec tolérances différentes|`non_comparable`|
|tentative beauty score|rejet explicite|

---

## 7. Cas de démonstration concrets

## Variante 1 — Segment divisé en tiers

Description :

Norma reçoit un `SegmentSpace`, un pack minimal et une rule de division.

Il produit :

- points à `t=1/3` et `t=2/3` ;
    
- sous-segments ;
    
- measurements ;
    
- artifact structuré.
    

Avantages :

- très simple ;
    
- excellent pour prouver ratio → position ;
    
- facile à tester.
    

Limites :

- trop faible comme démo MVP principale ;
    
- ne prouve pas composition 2D ;
    
- ne prouve pas zones, grids, évaluation A/B.
    

Statut :

> Bonne démo de test interne, pas démo MVP principale.

## Variante 2 — Surface proportionnelle évaluée

Description :

Norma reçoit une surface rectangulaire, un pack de tiers, deux compositions A/B, puis produit construction, measurements, evaluation, comparison, explanation et artifacts.

Avantages :

- couvre le cœur V1 ;
    
- parle aux designers ;
    
- parle aux architectes ;
    
- parle aux développeurs ;
    
- prouve construction + évaluation ;
    
- reste sans image, sans UI, sans plugin ;
    
- compatible avec replay-readiness.
    

Limites :

- demande une discipline forte sur le score ;
    
- le visual artifact peut distraire si trop mis en avant.
    

Statut :

> **Variante recommandée pour le MVP.**

## Variante 3 — Hiérarchie de surfaces simple

Description :

Norma reçoit trois rectangles et compare leurs aires à une séquence simple comme `1:1:1` ou `1:2`.

Il produit :

- area ratios ;
    
- surface hierarchy ;
    
- match / near_match / no_match ;
    
- explanation.
    

Avantages :

- prouve ratio d’aire ;
    
- montre que Norma n’est pas seulement un moteur de lignes ;
    
- utile pour composition.
    

Limites :

- plus abstrait ;
    
- risque de glisser vers `3:4:5` ou systèmes plus riches V1.5 ;
    
- moins visuel que la variante 2.
    

Statut :

> Bonne variante secondaire, pas démo MVP principale.

## Recommandation finale

La démo MVP doit être :

> **Variante 2 — Surface proportionnelle évaluée.**

Elle est suffisamment complète pour prouver Norma Core V1, mais suffisamment stricte pour ne pas ouvrir caméra, image, CAD, plugin, UI complète, agent autonome, cloud, marketplace ou scoring esthétique.

---

## 8. Anti-démo

Ne pas montrer dans le MVP :

|Anti-démo|Pourquoi|
|---|---|
|Caméra|Hors V1 ; introduit calibration, tracking, device state|
|Image detection|Hors V1 ; détourne vers vision/ML|
|Screenshot import|Risque de transformer image en source|
|OpenCV|Hors core ; dépendance lourde|
|Plugin Figma/AutoCAD|Trop tôt ; interface leakage|
|CAD natif|Hors V1 ; modèle externe trop riche|
|UI riche|Risque de faire croire que Norma est une app|
|Drag-and-drop|Interaction UI, pas preuve core|
|Recommandations créatives|Trop proche de l’optimisation/design assisté|
|“Make it better”|Prompt libre non structuré|
|Beauty score|Explicitement interdit|
|Harmony score absolu|Trop proche de beauty score|
|Multi-pack intelligent|Sélection de système non résolue|
|“Best layout”|Claim non défendable|
|Agent autonome|Risque MCP/agent qui invente rules|
|SVG comme input|Artifact devient source|
|DXF export robuste|CAD trop tôt|
|Cloud demo|Non nécessaire ; introduit état/réseau|
|Marketplace packs|Gouvernance trop tôt|
|User-defined pack riche|Validation et provenance pas encore stabilisées|

Phrase anti-démo :

> **La démo MVP ne doit pas impressionner par l’intégration. Elle doit convaincre par la reproductibilité.**

La version collée liste correctement ces anti-démos et la raison principale : ne pas introduire trop tôt caméra, image detection, plugin, CAD natif, UI riche, recommandations créatives, multi-pack intelligent, beauty score ou SVG comme input.

---

## 9. Message produit de la démo

## 9.1 Pour un designer

Message :

> **Norma permet de vérifier une composition structurée par rapport à un système proportionnel déclaré.**

Ce qu’il doit comprendre :

- il peut fournir un layout simple ;
    
- Norma génère des guides et zones ;
    
- Norma mesure les écarts ;
    
- Norma explique pourquoi un élément est proche ou loin d’un guide ;
    
- Norma ne dit pas “c’est beau” ;
    
- Norma dit “c’est proche de ce système”.
    

Formulation correcte :

> “Cette composition respecte mieux les tiers selon les mesures déclarées.”

Formulation interdite :

> “Cette composition est meilleure.”

## 9.2 Pour un architecte

Message :

> **Norma permet de générer des axes, zones, modules et rapports dans une surface rectangulaire abstraite.**

Ce qu’il doit comprendre :

- la surface peut représenter une façade abstraite, une planche, une élévation simplifiée ;
    
- Norma produit des divisions proportionnelles ;
    
- Norma mesure des rapports d’aires et positions ;
    
- Norma ne remplace pas un CAD ;
    
- Norma peut préparer plus tard des adapters, mais le moteur reste indépendant.
    

Formulation correcte :

> “La surface est divisée en bandes et modules selon un pack déclaré.”

Formulation interdite :

> “Norma importe et comprend un plan CAD.”

## 9.3 Pour un développeur

Message :

> **Norma est un moteur déterministe appelable avec des données structurées et vérifiable par outputs structurés.**

Ce qu’il doit comprendre :

- pas besoin d’image ;
    
- pas besoin de UI ;
    
- pas besoin de plugin ;
    
- input structuré ;
    
- pack versionné ;
    
- operation explicite ;
    
- output structuré ;
    
- warnings/errors ;
    
- run/replay ;
    
- artifact dérivé.
    

Formulation correcte :

> “Même input, même pack, même contexte, même output.”

Formulation interdite :

> “Le rendu SVG est le résultat.”

---

## 10. Risques de démo

|Risque|Symptôme|Protection|
|---|---|---|
|Trop visuel|Tout le monde commente le SVG, pas le moteur.|Montrer d’abord output structuré, puis visual artifact.|
|Trop UI|La démo devient un écran interactif.|Interface minimale, pas de workflow produit.|
|Trop abstrait|Personne ne comprend l’usage.|Utiliser composition A/B lisible avec rectangles.|
|Trop scoring|Le score devient le héros.|Montrer component scores, measurements et explanation.|
|Trop SVG|Le SVG semble être la vérité.|Répéter que SVG est projection dérivée.|
|Trop agent|L’agent semble décider.|Aucun agent autonome dans MVP.|
|Trop large|On ajoute packs, domaines, plugins.|Un seul pack minimal, une seule surface, deux compositions.|
|Trop “design advice”|On demande des corrections.|Pas de recommandation créative.|
|Trop “beauty”|On vend une note esthétique.|Interdire beauté, intention, qualité universelle.|
|Trop “CAD”|Architectes demandent import/export natif.|Dire façade abstraite, pas CAD natif.|
|Trop “image”|Designers demandent screenshot.|Tout est structuré.|
|Trop “multi-pack”|On compare thirds vs golden vs Modulor.|Un seul pack pour MVP.|
|Trop “magic operation”|`generateConstruction` cache tout.|Trace des rules appliquées obligatoire.|
|Warnings masqués|Résultat semble certain alors qu’il est ambigu.|Warnings visibles dans output et reports.|
|Replay oublié|La démo marche mais n’est pas vérifiable.|Run et PackLock dans le brief.|

La version collée exprime déjà ces risques avec une protection claire : montrer d’abord les outputs structurés, limiter le visual artifact, éviter l’agent autonome, refuser le beauty score et garder Run/PackLock visibles.

---

## 11. Décisions à verrouiller

Décisions copiables dans la spec globale :

1. **La démo MVP de Norma Core est une démo vérité du moteur, pas une démo d’interface.**
    
2. **La démo MVP doit utiliser uniquement des données géométriques structurées.**
    
3. **La démo MVP ne doit pas utiliser caméra, image, vision, OpenCV, tracking, plugin, CAD natif, cloud ou marketplace.**
    
4. **La démo MVP doit montrer une surface rectangulaire 2D, un ratio pack minimal, un rule set explicite, une construction, deux compositions simples, des measurements, une évaluation, une comparaison, une explanation et des artifacts.**
    
5. **Le pack de démo recommandé est un pack minimal basé sur `1/2`, `1/3`, `2/3` et `1:1:1`.**
    
6. **La construction de démo recommandée est une grille simple de tiers avec guides verticaux, guides horizontaux, zones, cellules, diagonales et intersections.**
    
7. **Les compositions A et B doivent être des compositions 2D simples composées uniquement de rectangles structurés.**
    
8. **La comparaison A/B doit être relative au même pack, même pack lock, même profile, mêmes tolérances, même surface, même coordinate system, même metric policy et même operation context.**
    
9. **La decision de comparaison doit dire “plus proche du système déclaré”, jamais “meilleure” ou “plus belle”.**
    
10. **La démo doit produire des outputs structurés avant tout visual artifact.**
    
11. **Le visual artifact simple est autorisé, mais uniquement comme projection dérivée.**
    
12. **Aucun SVG, export ou rendu ne doit devenir source de vérité.**
    
13. **La démo doit exposer `Run`, `PackLock`, `OperationContext`, warnings/errors et replay-readiness.**
    
14. **`replayRun` opérationnel complet n’est pas requis pour le MVP strict ; replay-readiness suffit.**
    
15. **Le score est autorisé seulement comme résumé relatif à un pack, un profile, des measurements et des tolérances.**
    
16. **Confidence doit rester séparée du score.**
    
17. **Aucun output, artifact ou message produit ne doit contenir beauty score, intention supposée ou qualité esthétique universelle.**
    
18. **La démo doit inclure au moins un cas de warning ou de rejet contrôlé pour prouver que Norma ne guess pas silencieusement.**
    

---

