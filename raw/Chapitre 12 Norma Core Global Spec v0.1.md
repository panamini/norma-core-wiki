
# 0. Document control

## 0.1 Nom

**Norma Core Global Spec v0.1**

## 0.2 Statut

**Normative draft consolidé.**

Cette spec est destinée à stabiliser les décisions conceptuelles avant toute descente d’implémentation.

## 0.3 But du document

Cette spec définit :

- ce qu’est Norma Core ;
- ce que V1 strict inclut ;
- ce que V1 strict exclut ;
- les objets conceptuels canoniques ;
- les frontières core / packs / artifacts / interfaces / adapters / agents ;
- les contrats conceptuels d’opération ;
- les règles de déterminisme, idempotence et replay-readiness ;
- les décisions d’architecture à préserver.

## 0.4 Langage normatif

Dans ce document :

- **doit** = obligation normative ;
- **ne doit pas** = interdiction normative ;
- **peut** = capacité autorisée mais non obligatoire ;
- **V1 strict** = appartient au cœur minimal ;
- **V1.5** = peut venir après stabilisation V1 ;
- **futur** = hors MVP initial ;
- **hors core** = ne doit pas entrer dans le modèle canonique du core.

---

# 1. Définition canonique

## 1.1 Définition courte

> **Norma Core est un moteur déterministe de géométrie proportionnelle appliquée à des espaces structurés.**

## 1.2 Définition complète

> **Norma Core est un moteur déterministe qui applique des systèmes de proportions explicites et versionnés à des espaces géométriques structurés pour produire des divisions, constructions, guides, zones, mesures, comparaisons, évaluations, décisions, explanations et artifacts reproductibles.**

Cette définition reprend la définition canonique déjà verrouillée : Norma Core reçoit des espaces, éléments géométriques et systèmes de proportions en entrée, puis produit constructions, guides, mesures, évaluations, décisions et artifacts reproductibles en sortie.

## 1.3 Chaîne conceptuelle principale

```
structured input→ proportional system→ rule resolution→ construction→ measurement→ evaluation→ decision→ explanation→ artifact→ run / replay-readiness
```

## 1.4 Ce que Norma Core est

Norma Core est :

- un moteur ;
- déterministe ;
- géométrique ;
- proportionnel ;
- structuré ;
- versionné ;
- explicable ;
- replay-ready ;
- indépendant des interfaces.

Norma Core sait :

- diviser un segment ;
- diviser une surface rectangulaire ;
- générer guides, zones, grilles simples, diagonales et intersections ;
- mesurer distances, positions, angles, aires, overlap, coverage et relations simples ;
- évaluer une composition simple selon un pack et un profile ;
- comparer deux compositions dans un cadre strict ;
- produire des résultats structurés ;
- produire des artifacts dérivés ;
- relier chaque résultat à un `Run`.

## 1.5 Ce que Norma Core n’est pas

Norma Core n’est pas :

- une UI ;
- une app caméra ;
- un plugin ;
- un serveur MCP ;
- une API cloud ;
- un moteur CAD ;
- un moteur image/vision ;
- un moteur 3D ;
- un générateur d’œuvres finales ;
- un simple catalogue de ratios ;
- un générateur SVG ;
- un beauty score ;
- un système d’inférence d’intention.

Règle :

> **Tout ce qui affiche, capture, appelle, exporte, héberge ou connecte Norma est une interface, un client ou un adapter. Tout ce qui divise, construit, mesure, compare et évalue selon des systèmes proportionnels appartient au core.**

---

# 2. Définition V1

## 2.1 Définition V1 verrouillée

> **Norma Core V1 est un moteur déterministe qui applique des systèmes de proportions versionnés à des segments 1D, surfaces rectangulaires 2D et compositions 2D simples, afin de générer des divisions, guides, zones, grilles simples, diagonales, intersections, mesures, évaluations explicables, décisions structurées et artifacts dérivés.**

## 2.2 Objectif V1

V1 doit prouver :

> **Espace structuré → pack versionné → rules → construction → measurements → evaluation → decision → artifacts → run/replay-readiness.**

V1 ne doit pas prouver que Norma sait tout faire.

## 2.3 Inclus V1 strict

Norma Core V1 strict inclut :

- segments 1D ;
- surfaces rectangulaires 2D axis-aligned ;
- compositions 2D simples ;
- points ;
- segments ;
- lignes limitées ;
- rectangles ;
- guides ;
- zones rectangulaires ;
- grilles simples ;
- cellules de grille ;
- diagonales ;
- intersections ponctuelles ;
- données géométriques structurées ;
- ratio packs versionnés ;
- ratios ;
- ratio families ;
- ratio sequences simples ;
- partition patterns simples ;
- rule declarations dans packs ;
- rule types supportés par le core ;
- rule sets ;
- constructions ;
- measurements ;
- evaluation profiles simples ;
- scoring minimal par components ;
- decisions ;
- explanations traçables ;
- structured artifacts ;
- simple visual artifacts limités ;
- `Run` conceptuel ;
- `PackLock` conceptuel ;
- `OperationContext` conceptuel ;
- warnings/errors structurés ;
- idempotence ;
- replay-readiness.

## 2.4 Exclusions V1 strict

Norma Core V1 strict exclut :

- caméra ;
- image brute ;
- vidéo ;
- vision ;
- OpenCV ;
- tracking ;
- 3D ;
- CAD natif ;
- plugins natifs ;
- UI complète ;
- cloud ;
- marketplace ;
- comptes utilisateurs ;
- polygones complexes ;
- courbes ;
- splines ;
- meshes ;
- CAD constraints avancées ;
- formats natifs ;
- inference d’intention ;
- beauty score ;
- scoring esthétique universel ;
- recommandations créatives avancées ;
- optimisation automatique ;
- choix automatique du “meilleur système” ;
- prompt libre comme source de vérité ;
- objet natif externe comme input core.

## 2.5 V1.5 possible

V1.5 peut inclure :

- CLI minimale ;
- SDK minimal ;
- API locale/process ;
- MCP minimal ;
- agent playbooks ;
- `replayRun` ;
- `verifyRun` ;
- `verifyArtifactFreshness` ;
- CSV measurements ;
- design tool adapter prototype ;
- CAD adapter prototype non-core ;
- validation plus stricte des schemas ;
- operation registry plus formalisé.

## 2.6 Futur

Futur :

- plugins natifs complets ;
- camera app ;
- image/vision pipeline ;
- CAD robuste ;
- design tool plugin complet ;
- API cloud ;
- marketplace ;
- pack registry public ;
- signatures de packs ;
- 3D ;
- imports natifs ;
- advanced recommendations ;
- user-defined pack governance.

---

# 3. Décisions transversales fondamentales

Ces décisions doivent apparaître en tête de toute version future de la spec.

1. **Norma Core est un moteur déterministe de géométrie proportionnelle.**
2. **Norma Core applique des systèmes de proportions versionnés à des espaces structurés.**
3. **Norma Core V1 travaille sur segments 1D, surfaces rectangulaires 2D et compositions 2D simples.**
4. **Norma Core V1 reçoit des données géométriques structurées, pas des images, vidéos, caméras ou fichiers natifs.**
5. **Les ratios vivent dans les packs.**
6. **Les rule declarations vivent dans les packs.**
7. **Les rule types et algorithmes d’exécution vivent dans le core.**
8. **Le pack déclare quoi appliquer ; le core sait comment l’exécuter si le rule type est supporté.**
9. **Les calculs vivent dans le core.**
10. **Les interfaces appellent.**
11. **Les adapters traduisent.**
12. **Les artifacts représentent.**
13. **Les constructions sont des résultats géométriques sources.**
14. **Les measurements sont des faits calculés.**
15. **Les evaluations interprètent des measurements selon un système déclaré.**
16. **Les scores sont relatifs à un pack, un profile, des measurements et des tolérances.**
17. **Norma ne produit pas de beauty score.**
18. **Norma ne déduit pas l’intention d’un auteur.**
19. **Un `Run` est l’enveloppe centrale de reproductibilité.**
20. **Un `PackLock` verrouille pack id, pack version, schema version et content identity.**
21. **Même input + même pack + mêmes rules + mêmes tolérances + même contexte + même version d’opération = même output.**
22. **Les warnings sont obligatoires quand une donnée, une mesure, une conversion ou une conclusion est ambiguë.**
23. **Aucune interface, adapter, function, tool ou agent ne doit inventer de ratio, rule, score, explanation ou résultat.**
24. **Tout default qui change un résultat doit être explicite, versionné ou rejeté.**

---

# 4. Frontières d’architecture

## 4.1 Core

Le core contient :

- modèle géométrique ;
- opérations ;
- rule execution ;
- construction ;
- measurements ;
- evaluation ;
- decision ;
- explanation structurée ;
- artifact generation conceptuelle ;
- errors/warnings ;
- identity/replay-readiness.

Le core ne contient pas :

- UI ;
- caméra ;
- plugin natif ;
- server transport ;
- stockage cloud ;
- marketplace ;
- format natif tiers ;
- rendu interactif ;
- modèle IA ;
- données utilisateur non structurées.

## 4.2 Ratio packs

Les packs contiennent :

- ratios ;
- ratio families ;
- ratio sequences ;
- partition patterns ;
- rule declarations ;
- rule sets ;
- conventions ;
- metadata ;
- provenance ;
- confidence/status ;
- compatibility ;
- limits.

Les packs ne contiennent pas :

- code exécutable client ;
- UI ;
- rendu ;
- export ;
- caméra ;
- plugin ;
- modèle IA ;
- scoring esthétique universel ;
- claims non qualifiés.

## 4.3 Rule declarations vs rule types

Décision normative :

> **Les rule declarations vivent dans les packs. Les rule types et algorithmes d’exécution vivent dans le core.**

Conséquences :

- un pack ne contient pas de code ;
- le core ne hardcode pas des systèmes proportionnels complets ;
- une interface ne crée pas de rule ad hoc ;
- un agent ne crée pas une rule par prompt ;
- si un pack déclare un rule type non supporté, le core retourne erreur ou warning de compatibilité.

## 4.4 Interfaces

Les interfaces :

- appellent le core ;
- affichent les résultats ;
- transportent inputs/outputs ;
- fournissent une expérience utilisateur ;
- peuvent produire ou afficher des artifacts.

Elles ne doivent pas :

- définir les ratios ;
- définir les rules ;
- choisir silencieusement un pack ;
- changer les tolérances sans déclaration ;
- masquer warnings/errors ;
- transformer un export en source de vérité.

## 4.5 Adapters

Un adapter traduit.

Chaîne autorisée :

```
external data→ Norma structured input→ core operation→ Norma result→ artifact→ external target format
```

Cette direction est déjà verrouillée dans les chapitres d’interface : un adapter traduit external data vers input Norma, appelle le core, puis traduit result/artifact vers le format cible, sans redéfinir la logique core.

Un adapter ne doit pas :

- calculer à la place du core ;
- définir des ratios ;
- redéfinir des rules ;
- choisir un pack implicite ;
- produire une évaluation sans measurements ;
- produire une explanation sans sources ;
- transformer SVG, DXF, layer, screenshot ou plugin payload en vérité core.

## 4.6 Artifacts

Un artifact est une représentation dérivée.

La vérité Norma est dans :

- input structuré ;
- pack ;
- pack lock ;
- rules ;
- construction ;
- measurements ;
- evaluation ;
- decision ;
- run ;
- operation context.

Un artifact ne doit jamais devenir source de vérité.

Les artifacts doivent référencer leurs source objects, déclarer leur format, leurs options, leur provenance, leurs warnings et leurs limitations. Le fichier d’artifacts verrouille notamment que `StructuredResultArtifact` est V1 strict, que `SimpleVisualArtifact` peut exister en V1 limité, et que SVG simple ne doit jamais devenir modèle interne.

## 4.7 Agents

Les agents peuvent appeler Norma.

Ils ne peuvent pas inventer Norma.

Un agent doit :

- utiliser une opération explicite ;
- fournir un input structuré ;
- référencer pack/rules/profile/tolérances ;
- lire les outputs structurés ;
- respecter warnings/errors ;
- ne pas inventer de ratio ;
- ne pas inventer de rule ;
- ne pas produire de beauty claim ;
- ne pas masquer les limitations.

---

# 5. Glossaire canonique

## 5.1 Objets de système proportionnel

|Objet|Définition|Source de vérité|
|---|---|---|
|`RatioPack`|Système proportionnel déclaratif, versionné et validable.|Pack|
|`Ratio`|Relation proportionnelle nommée.|Pack|
|`RatioFamily`|Groupe de ratios ou sequences liés.|Pack|
|`RatioSequence`|Suite de parts proportionnelles.|Pack|
|`PartitionPattern`|Pattern déclaratif de partition d’une surface.|Pack|
|`Rule`|Déclaration d’une logique applicable.|Pack declaration|
|`RuleSet`|Groupe ordonné ou déclaré de rules.|Pack|
|`EvaluationProfile`|Politique de lecture des measurements.|Input/profile/pack reference|

## 5.2 Objets géométriques

|Objet|Définition|V1|
|---|---|---|
|`Space`|Support géométrique de travail.|Oui|
|`SegmentSpace`|Espace 1D borné.|Oui|
|`SurfaceSpace`|Surface rectangulaire 2D axis-aligned.|Oui|
|`Composition2D`|Surface + elements + anchors.|Oui|
|`CoordinateSystem`|Convention de coordonnées.|Oui|
|`MetricPolicy`|Convention de distances, angles, aires et unités.|Oui|
|`Point`|Position 1D/2D.|Oui|
|`Segment`|Ligne bornée entre deux points.|Oui|
|`Line`|Ligne non bornée, usage limité.|Oui limité|
|`Rect`|Rectangle axis-aligned.|Oui|
|`Anchor`|Point, bord, centre ou géométrie significative.|Oui|
|`Element`|Objet structuré d’une composition.|Oui|

## 5.3 Objets de construction

|Objet|Définition|
|---|---|
|`Construction`|Résultat géométrique produit par rules appliquées à un espace.|
|`Guide`|Géométrie générée pour construire ou mesurer.|
|`Zone`|Région rectangulaire produite ou déclarée.|
|`Grid`|Structure de guides et cellules.|
|`GridCell`|Cellule rectangulaire d’une grille.|
|`IntersectionPoint`|Point dérivé d’une intersection avec provenance.|
|`DominantSegment`|Segment dominant selon critère déclaré.|
|`DirectionalRelation`|Relation spatiale ou angulaire calculée.|
|`SurfaceMassRelation`|Distribution d’aires/positions dans une surface.|
|`IntersectionPattern`|Pattern simple issu d’intersections.|
|`SegmentPattern`|Pattern simple de segments/lignes.|

## 5.4 Objets de measurement

|Objet|Définition|
|---|---|
|`Measurement`|Fait calculé.|
|`DistanceMeasurement`|Distance entre géométries.|
|`PositionMeasurement`|Position `t`, `(x,y)` ou locale.|
|`RatioMeasurement`|Ratio mesuré et écart à cible.|
|`AngleMeasurement`|Angle selon convention.|
|`AreaMeasurement`|Aire absolue ou relative.|
|`ContainmentMeasurement`|Inside / boundary / outside.|
|`OverlapMeasurement`|Overlap entre rectangles.|
|`CoverageMeasurement`|Couverture d’une zone par elements.|

## 5.5 Objets d’évaluation

|Objet|Définition|
|---|---|
|`Evaluation`|Application d’un profile à des measurements.|
|`Score`|Résumé dérivé d’une evaluation.|
|`ComponentScore`|Score partiel par dimension mesurée.|
|`Confidence`|Fiabilité du résultat.|
|`Decision`|Conclusion structurée.|
|`Explanation`|Justification traçable dérivée des mesures.|
|`CandidateSet`|Ensemble de candidates comparées.|
|`CandidateRanking`|Classement contextuel.|
|`Tie`|Égalité dans tolérance.|
|`AmbiguousRanking`|Ranking indécidable.|
|`SelectionPolicy`|Politique minimale de choix.|

## 5.6 Objets d’artifact

|Objet|Définition|Statut|
|---|---|---|
|`Artifact`|Représentation dérivée.|V1 concept|
|`StructuredResultArtifact`|Représentation structurée principale.|V1 strict|
|`ConstructionSummaryArtifact`|Résumé de construction.|V1 strict|
|`EvaluationReportArtifact`|Rapport structuré d’évaluation.|V1 strict|
|`ExplanationArtifact`|Explication structurée exportable.|V1 strict|
|`SimpleVisualArtifact`|Projection visuelle simple.|V1 strict limité|
|`ExportArtifact`|Projection dans format externe.|V1.5/futur selon format|
|`PluginPayload`|Payload futur pour plugin/adapter.|Futur|

## 5.7 Objets d’exécution/replay

|Objet|Définition|
|---|---|
|`Run`|Enveloppe d’exécution reproductible.|
|`RunInput`|Entrée structurée d’un run.|
|`RunOutput`|Références vers résultats d’un run.|
|`OperationContext`|Contexte computationnel explicite.|
|`PackLock`|Verrou de pack : id, version, schema version, content identity.|
|`SourceReference`|Référence à une source externe non-core.|
|`Provenance`|Chaîne d’origine/dérivation.|

---

# 6. Dictionnaire des variables canoniques

La spec v0.1 ne verrouille pas les champs JSON finaux. Elle verrouille les **variables conceptuelles qui affectent le résultat**.

Règle :

> **Les formats exacts peuvent rester ouverts, mais les variables conceptuelles qui affectent le résultat ne doivent pas rester implicites.**

## 6.1 Variables canoniques

|Variable canonique|Sens|
|---|---|
|`coreVersion`|Version du core.|
|`geometryModelVersion`|Version du modèle géométrique.|
|`operation`|Opération demandée.|
|`operationVersion`|Version du comportement opérationnel.|
|`input`|Données Norma structurées.|
|`operationContext`|Contexte computationnel explicite.|
|`space`|Espace de travail.|
|`segmentSpace`|Espace 1D.|
|`surfaceSpace`|Surface rectangulaire 2D.|
|`composition`|Surface + elements + anchors.|
|`packRef`|Référence déclarative à un pack.|
|`packLock`|Pack verrouillé pour reproductibilité.|
|`ruleRef`|Rule déclarée.|
|`ruleSetRef`|Groupe de rules.|
|`constructionRef`|Construction source ou résultat.|
|`measurementRefs`|Measurements utilisées ou produites.|
|`evaluationProfileRef`|Profil d’évaluation.|
|`evaluationRef`|Évaluation produite.|
|`scoreRef`|Score dérivé.|
|`decisionRef`|Decision produite.|
|`explanationRef`|Explanation dérivée.|
|`artifactRef`|Artifact dérivé.|
|`runRef`|Run source.|
|`coordinateSystem`|Repère utilisé.|
|`metricPolicy`|Convention de distance, angle, aire et unité.|
|`tolerancePolicy`|Politique de tolérance.|
|`roundingPolicy`|Politique d’arrondi.|
|`orderingPolicy`|Politique de tri stable.|
|`numericPolicy`|Précision, epsilon, irrationnels.|
|`featureFlags`|Options qui changent le résultat.|
|`requestedOutputs`|Sorties demandées.|
|`requestedArtifacts`|Artifacts demandés.|
|`sourceReferences`|Références externes non-core.|
|`warnings`|Warnings structurés.|
|`errors`|Erreurs structurées.|
|`status`|Statut du résultat.|
|`provenance`|Origine et chaîne de dérivation.|

## 6.2 Variables ou noms dangereux

À éviter comme noms principaux :

- `data` ;
- `config` ;
- `params` ;
- `result` sans type ;
- `score` sans profile ;
- `geometry` sans espace ;
- `ratio` comme float nu ;
- `rules` sans pack/rule refs ;
- `context` sans contenu explicite ;
- `artifact` sans source.

Règle :

> **Un nom vague peut exister localement dans une implémentation future, mais la spec doit nommer clairement les concepts qui affectent le résultat.**

---

# 7. Modèle géométrique V1

## 7.1 Verdict

> **Norma Core V1 utilise une géométrie rectangulaire normalisée avec métrique explicite.**

Les positions sont normalisées. Les distances, angles et aires déclarent leur espace de référence et leur metric policy.

## 7.2 Segment 1D

Un `SegmentSpace` est un espace 1D borné.

Il doit avoir :

- start ;
- end ;
- longueur ;
- unité ou `unitless` ;
- position paramétrique `t`.

Convention :

- `t = 0` start ;
- `t = 1` end ;
- `t = 1/2` milieu ;
- `t = 1/3` tiers depuis start.

Hors V1 :

- polyline ;
- spline ;
- courbe ;
- segment 3D.

## 7.3 Surface rectangulaire 2D

Une `SurfaceSpace` V1 est :

- rectangulaire ;
- axis-aligned ;
- bornée ;
- munie d’une largeur ;
- munie d’une hauteur ;
- munie d’une unité ;
- munie d’un coordinate system ;
- munie d’un metric policy.

Hors V1 :

- surface tournée ;
- polygone ;
- masque ;
- forme libre ;
- surface 3D ;
- région image détectée.

## 7.4 Composition 2D simple

Une `Composition2D` est :

```
SurfaceSpace + Elements + Anchors optionnels
```

Elle peut contenir :

- rectangles ;
- points ;
- segments ;
- anchors ;
- elements rectangulaires ;
- guides générés ;
- zones générées.

Elle ne contient pas :

- image brute ;
- layer Figma natif ;
- objet CAD natif ;
- style ;
- contenu sémantique riche non structuré.

## 7.5 Repère Norma

Repère canonique :

- origine : bas-gauche ;
- `x` vers la droite ;
- `y` vers le haut ;
- angles positifs : antihoraire ;
- positions normalisées dans `[0,1]`.

Règle :

> **Les clients peuvent convertir leurs coordonnées vers Norma. Norma ne doit pas adopter la convention d’un client comme vérité interne.**

## 7.6 Coordonnées normalisées vs métriques

Position normalisée :

```
x = 0.5, y = 0.5
```

signifie centre de la surface.

Distance métrique :

- dépend de largeur ;
- dépend de hauteur ;
- dépend de l’unité ;
- dépend de `metricPolicy`.

Règle :

> **Norma ne doit jamais confondre coordonnées normalisées et coordonnées métriques.**

## 7.7 Primitives V1

|Primitive|V1|Notes|
|---|---|---|
|`Point`|Oui|Position 1D/2D.|
|`Segment`|Oui|Ligne bornée.|
|`Line`|Oui limité|Non bornée, calculs.|
|`Rect`|Oui|Axis-aligned.|
|`Guide`|Oui|Dérivé.|
|`Zone`|Oui|Rectangulaire.|
|`Grid`|Oui simple|Guides + cells.|
|`GridCell`|Oui|Rectangulaire.|
|`Anchor`|Oui|Centre, bord, coin, etc.|
|`Element`|Oui|Objet structuré.|
|`IntersectionPoint`|Oui|Dérivé avec provenance.|

---

# 8. Ratio packs et systèmes proportionnels

## 8.1 Verdict

> **Un `RatioPack` est un système proportionnel déclaratif, versionné et validable.**

Il contient la connaissance proportionnelle. Le core l’applique.

## 8.2 Ce qu’un pack peut contenir

Un pack peut contenir :

- `Ratio` ;
- `RatioFamily` ;
- `RatioSequence` ;
- `PartitionPattern` ;
- positions candidates ;
- conventions ratio → position ;
- rule declarations ;
- rule sets ;
- metadata ;
- provenance ;
- confidence/status ;
- compatibility ;
- limits.

## 8.3 Ce qu’un pack ne doit pas contenir

Un pack ne doit pas contenir :

- UI ;
- couleurs ;
- rendu ;
- caméra ;
- plugin ;
- données utilisateur ;
- code client ;
- logique d’export ;
- modèle IA ;
- scoring esthétique universel ;
- claims “ce ratio rend beau”.

## 8.4 Ratio

Un `Ratio` est une relation proportionnelle nommée.

Il peut être :

- rationnel ;
- décimal ;
- irrationnel ;
- expression mathématique ;
- valeur approchée ;
- ratio de longueur ;
- ratio de surface ;
- ratio de position ;
- complément ;
- réciproque.

Règle :

> **Un ratio ne doit pas être réduit à un float nu.**

## 8.5 Convention ratio → position

Un ratio relationnel ne devient pas automatiquement position.

Exemple :

```
a:b → a/(a+b)
```

`1:2` devient `1/3` seulement si cette convention est déclarée.

Règle :

> **Norma ne doit pas deviner la convention ratio → position.**

## 8.6 RatioSequence

Une `RatioSequence` représente une relation entre plusieurs parts.

Exemples :

- `1:1:1` ;
- `1:2` ;
- `2:3` ;
- `3:4:5`.

V1 strict :

- concept supporté ;
- sequences simples ;
- pas de bibliothèque massive.

Règle :

> **`3:4:5` ne doit pas être représenté comme trois ratios indépendants.**

## 8.7 PartitionPattern

Un `PartitionPattern` décrit comment appliquer une sequence à une surface.

Il doit déclarer :

- sequence ;
- orientation ;
- ordre ;
- mesure contrôlée ;
- tolérance ;
- compatibility V1/V1.5/futur.

## 8.8 PackLock

Un `PackLock` verrouille :

- pack id ;
- pack version ;
- pack schema version ;
- content identity.

Règle :

> **Un pack id/version sans content identity ne suffit pas au replay strict.**

---

# 9. Rules et constructions

## 9.1 Verdict

> **Une `Rule` décrit une transformation ou dérivation possible. Une `Construction` est le résultat structuré produit quand Norma applique une ou plusieurs rules à un espace.**

## 9.2 Rule

Une rule declaration doit décrire :

- id ;
- type ;
- inputs attendus ;
- parameters ;
- ratios/sequences utilisés ;
- conventions ;
- constraints ;
- expected outputs ;
- errors ;
- warnings ;
- provenance ;
- compatibility.

Une rule ne doit pas contenir :

- code client ;
- rendu ;
- UI ;
- caméra ;
- plugin ;
- score esthétique ;
- recommandation créative opaque.

## 9.3 Rule type

Un rule type est une capacité d’exécution supportée par le core.

Exemples :

- `divideSegmentByPosition` ;
- `divideSegmentByRatio` ;
- `divideSurfaceVertical` ;
- `createSimpleGrid` ;
- `deriveIntersections`.

Règle :

> **Si le pack déclare une rule dont le type n’est pas supporté par le core, l’opération échoue ou retourne un warning de compatibilité.**

## 9.4 RuleSet

Un `RuleSet` est un groupe explicite de rules.

Il doit avoir :

- id ;
- rules référencées ;
- ordre ou politique d’ordre ;
- compatibility ;
- provenance.

Un `RuleSet` n’est pas un preset UI.

## 9.5 Construction

Une `Construction` peut contenir :

- source space ;
- pack source ;
- rules appliquées ;
- guides ;
- zones ;
- grids ;
- grid cells ;
- partitions ;
- diagonales ;
- intersections ;
- measurements associées ;
- directional relations ;
- dominant segments ;
- surface mass relations ;
- basic patterns ;
- provenance ;
- warnings.

Une construction ne doit pas contenir :

- SVG comme vérité ;
- style graphique ;
- calques UI ;
- objet CAD natif ;
- plugin natif ;
- caméra ;
- score esthétique ;
- intention supposée.

## 9.6 Rules V1 strictes

|Rule type|Statut|
|---|---|
|`divideSegmentByPosition`|V1 strict|
|`divideSegmentByRatio`|V1 strict|
|`divideSegmentByRatioSequence`|V1 strict minimal|
|`divideSurfaceVertical`|V1 strict|
|`divideSurfaceHorizontal`|V1 strict|
|`partitionSurfaceByRatioSequence`|V1 strict minimal|
|`createZonesFromDivisions`|V1 strict|
|`createMarginsSimple`|V1 strict minimal|
|`createGuidesFromCandidates`|V1 strict|
|`createSimpleGrid`|V1 strict|
|`createDiagonals`|V1 strict|
|`deriveIntersections`|V1 strict|
|`measureAreasFromZones`|V1 strict|
|`deriveDominantSegmentByLength`|V1 strict minimal|
|`deriveSegmentOrientation`|V1 strict|
|`deriveDirectionalRelationBasic`|V1 strict minimal|
|`deriveSurfaceMassCenter`|V1 strict minimal|
|`deriveBasicIntersectionPattern`|V1 strict minimal|
|`deriveBasicSegmentPattern`|V1 strict minimal|

---

# 10. Operations du core

## 10.1 Verdict

> **Une opération core est une action déterministe qui reçoit des objets structurés Norma, applique une logique explicite, puis retourne un résultat structuré avec status, errors, warnings, provenance et sorties traçables.**

Les opérations sont la surface exécutable de Norma Core.

Elles ne sont pas :

- des domain objects ;
- des rules ;
- des constructions ;
- des measurements ;
- des exports ;
- des écrans ;
- des plugins ;
- des tools MCP.

## 10.2 Catégories d’opérations

|Type|Définition|
|---|---|
|Atomique|Fait une seule chose déterministe.|
|Dérivée|Calcule une mesure/relation/pattern depuis des objets.|
|Orchestratrice|Enchaîne plusieurs opérations atomiques ou dérivées.|
|Publique|Exposable plus tard par CLI/SDK/API/MCP.|
|Interne|Support du core, non exposée directement.|

Règle :

> **Une opération orchestratrice peut exister, mais elle ne doit jamais être opaque.**

## 10.3 Registry conceptuel des opérations V1

Le registry conceptuel suivant est normatif pour v0.1. Il intègre les opérations d’artifacts explicitement demandées dans l’observation.

|Opération|Statut|Rôle|
|---|---|---|
|`validateRatioPack`|V1 strict|Vérifier qu’un pack est utilisable.|
|`resolveRatio`|V1 strict|Résoudre un ratio déclaré.|
|`resolveRatioSequence`|V1 strict|Résoudre une sequence déclarée.|
|`resolveRuleSet`|V1 strict|Résoudre un rule set.|
|`createSegmentSpace`|V1 strict|Créer/valider un espace 1D.|
|`createSurfaceSpace`|V1 strict|Créer/valider une surface 2D.|
|`createComposition`|V1 strict|Créer une composition 2D simple.|
|`generateConstruction`|V1 strict|Produire une construction traçable.|
|`generateGuides`|V1 strict|Produire des guides.|
|`generateZones`|V1 strict|Produire des zones rectangulaires.|
|`generateSimpleGrid`|V1 strict|Produire une grille simple.|
|`generateDiagonals`|V1 strict|Produire les diagonales d’une surface.|
|`deriveIntersections`|V1 strict|Dériver les points d’intersection.|
|`measureGeometry`|V1 strict|Mesurer distances, positions, angles, containment.|
|`measureAreas`|V1 strict|Mesurer aires, ratios d’aires, overlap, coverage.|
|`deriveSurfaceHierarchy`|V1 strict minimal|Classer surfaces/zones par aire.|
|`deriveDominantSegments`|V1 strict minimal|Identifier segments dominants simples.|
|`deriveDirectionalRelations`|V1 strict minimal|Relations above/below/left/right/parallel/perpendicular.|
|`deriveSurfaceMassRelations`|V1 strict minimal|Centre surfacique pondéré et distribution simple.|
|`deriveBasicPatterns`|V1 strict minimal|Patterns simples : X, grid, parallel, orthogonal.|
|`evaluateCompositionBasic`|V1 strict|Évaluer une composition simple.|
|`compareCompositionsBasic`|V1 strict limité|Comparer deux compositions selon même contexte.|
|`createStructuredResultArtifact`|V1 strict|Produire l’artifact structuré principal.|
|`createConstructionSummaryArtifact`|V1 strict|Produire un résumé de construction.|
|`createEvaluationReportArtifact`|V1 strict|Produire un rapport d’évaluation.|
|`createExplanationArtifact`|V1 strict|Produire une explanation structurée.|
|`createSimpleVisualArtifact`|V1 strict limité|Produire une projection visuelle simple.|

## 10.4 Opérations V1.5 possibles

|Opération|Statut|
|---|---|
|`replayRun`|V1.5|
|`verifyRun`|V1.5|
|`verifyArtifactFreshness`|V1.5|
|`exportMeasurementsCsv`|V1.5|
|`createAdapterImportReport`|V1.5|

Règle :

> **V1 strict doit être replay-ready. `replayRun` opérationnel complet peut rester V1.5.**

## 10.5 Interdictions opérationnelles

Une opération core ne doit pas :

- lire une caméra ;
- analyser une image brute ;
- dépendre d’une UI ;
- dépendre d’un plugin ;
- dépendre d’un logiciel externe ;
- dépendre d’un état global caché ;
- choisir implicitement un pack ;
- choisir implicitement une tolérance si elle change le résultat ;
- générer un jugement esthétique universel ;
- optimiser automatiquement une composition ;
- produire une recommandation créative opaque ;
- masquer warnings/errors.

## 10.6 Operation Call Contract

Une opération Norma doit être appelable de manière structurée par un core client, une CLI future, un SDK futur, une API future ou un serveur MCP futur.

Un appel d’opération n’est pas un prompt libre.

Un appel d’opération doit contenir conceptuellement :

|Variable|Obligatoire ?|Rôle|
|---|---|---|
|`operation`|Oui|Nom de l’opération demandée.|
|`operationVersion`|Oui|Version du comportement opérationnel.|
|`input`|Oui|Données Norma structurées.|
|`operationContext`|Oui|Contexte computationnel explicite.|
|`packLock`|Si pack utilisé|Pack id, version, schema version, content identity.|
|`ruleRefs` / `ruleSetRef`|Si construction/rule|Rules ou rule set appliqués.|
|`evaluationProfileRef`|Si évaluation|Profil d’évaluation utilisé.|
|`tolerances`|Oui si calcul comparatif|Tolérances effectives.|
|`coordinateSystem`|Oui si géométrie|Convention de coordonnées.|
|`metricPolicy`|Oui si mesures métriques|Distance, angle, aire, unité.|
|`requestedOutputs`|Optionnel|Construction, measurements, evaluation, artifacts demandés.|
|`requestedArtifacts`|Optionnel|Artifacts à produire.|
|`sourceReferences`|Si adapter/import|Sources externes et provenance.|
|`featureFlags`|Si effet sur résultat|Toute option qui change le comportement.|

Interdictions :

- pas de pack implicite ;
- pas de rule implicite ;
- pas de tolérance implicite si elle change le résultat ;
- pas de prompt libre comme source de vérité ;
- pas d’image brute ;
- pas d’objet natif externe comme input core ;
- pas d’état UI, session, viewport ou caméra comme donnée cachée.

Phrase à verrouiller :

> **Tout ce qui peut changer le résultat doit apparaître dans l’input, le context, le pack lock, les rule refs, les tolerances ou l’operation version.**

## 10.7 Operation Result Contract

Une opération Norma doit retourner un résultat structuré.

Un résultat d’opération doit contenir conceptuellement :

|Variable|Obligatoire ?|Rôle|
|---|---|---|
|`status`|Oui|État global du résultat.|
|`runRef` ou `run`|Oui pour opération significative|Enveloppe de reproductibilité.|
|`result`|Si succès ou partiel|Objet principal produit.|
|`outputRefs`|Si plusieurs sorties|Références vers construction, measurements, evaluation, decision, artifacts.|
|`warnings`|Oui, même vide|Ambiguïtés, pertes, limites.|
|`errors`|Oui, même vide|Erreurs bloquantes ou partielles.|
|`provenance`|Oui|Sources des objets dérivés.|
|`packLock`|Si pack utilisé|Pack effectivement utilisé.|
|`operationContext`|Oui|Contexte effectif.|
|`artifactRefs`|Si artifacts produits|Artifacts dérivés.|
|`explanationRefs`|Si explanation produite|Explanations traçables.|

Statuts génériques :

|Status|Sens|
|---|---|
|`success`|Résultat complet produit.|
|`partial`|Résultat partiel avec warnings/errors non bloquants.|
|`failed`|Aucun résultat fiable produit.|
|`ambiguous`|Résultat exploitable seulement comme ambigu.|
|`non_comparable`|Comparaison impossible ou invalide.|
|`non_replayable`|Résultat non rejouable strictement.|
|`stale`|Résultat ou artifact obsolète par rapport à ses sources.|

Règle :

> **Une opération ne doit jamais échouer silencieusement. Elle retourne un résultat structuré, un statut ou une erreur explicite.**

---

# 11. Measurements

## 11.1 Verdict

> **Une `Measurement` est un fait calculé. Elle ne dit pas encore si ce fait est bon, beau ou souhaitable.**

## 11.2 Une measurement doit contenir

- id local stable ;
- type ;
- inputs ;
- source geometry ;
- valeur ;
- unité ou normalisation ;
- coordinate system ;
- metric policy ;
- tolerance ;
- status ;
- provenance ;
- warnings ;
- limitations.

## 11.3 Une measurement ne doit pas contenir

- jugement esthétique ;
- score global ;
- recommandation ;
- intention ;
- interprétation psychologique ;
- texte libre non traçable.

## 11.4 Measurements V1

|Measurement|V1|
|---|---|
|Distance aux guides|Oui|
|Alignement|Oui|
|Position proportionnelle|Oui|
|Ratio de longueurs|Oui|
|Ratio d’aires|Oui|
|Angle|Oui|
|Containment|Oui|
|Overlap rectangulaire|Oui|
|Coverage simple|Oui|
|Surface hierarchy simple|Oui|
|Dominant segment simple|Oui minimal|
|Directional relation basique|Oui minimal|
|Surface mass center|Oui minimal|
|Basic patterns|Oui minimal|

## 11.5 Relations directionnelles

Relations V1 strictes :

- above ;
- below ;
- left ;
- right ;
- centered ;
- ascending ;
- descending ;
- parallel ;
- perpendicular.

Règle :

> **Montant/descendant est une classification directionnelle, pas une interprétation émotionnelle.**

## 11.6 Surface mass

`SurfaceMassRelation` V1 est une approximation géométrique :

- aire ;
- aire relative ;
- centre surfacique pondéré ;
- distribution haute/basse/gauche/droite.

Elle n’est pas un modèle complet de perception humaine.

## 11.7 Patterns simples

V1 strict minimal :

- X-crossing simple ;
- diagonal crossing ;
- grid intersection ;
- perpendicular crossing ;
- parallel pattern ;
- orthogonal network simple.

V1.5 :

- reconnaissance riche ;
- T/V/Y ;
- convergence/divergence plus robuste ;
- pattern matching de partitions.

---

# 12. Evaluation, scoring, decision, explanation

## 12.1 Verdict

> **Norma Core V1 peut évaluer une cohérence géométrique mesurable par rapport à un système proportionnel déclaré. Norma Core V1 ne doit jamais prétendre évaluer la beauté, l’intention, la qualité artistique universelle ou la valeur esthétique absolue d’une composition.**

Les observations confirment que le score doit rester relatif au pack/profile, que confidence est séparée, et qu’il ne faut ni beauté ni intention.

## 12.2 Chaîne d’évaluation

```
Measurement = fait calculéEvaluationProfile = politique de lectureEvaluation = application du profile aux measurementsScore = résumé dérivéDecision = conclusion structuréeExplanation = justification traçable
```

## 12.3 EvaluationProfile

Un `EvaluationProfile` définit comment lire des measurements.

Il peut être :

- fourni comme input structuré ;
- référencé par un pack ;
- versionné séparément plus tard.

Il ne doit pas :

- créer de ratios ;
- créer de rules ;
- créer de measurements ;
- porter des claims esthétiques ;
- contenir une UI ;
- contenir un modèle IA ;
- inférer une intention.

Cette clarification est explicitement recommandée dans les observations : `EvaluationProfile` est une configuration d’interprétation, pas une source de connaissance proportionnelle.

## 12.4 EvaluationProfile contient

- id ;
- version ou ref ;
- pack compatible ;
- rule set compatible ;
- measurements utilisées ;
- component scores ;
- poids ;
- tolérances ;
- seuils de statut ;
- confidence policy ;
- tie policy ;
- ranking policy ;
- warnings obligatoires ;
- provenance ;
- limitations ;
- statut : stable / experimental / user-defined.

## 12.5 Evaluation

Une `Evaluation` dépend de :

- pack ;
- pack lock ;
- rule set ;
- construction ;
- measurements ;
- evaluation profile ;
- tolerances ;
- operation context.

Elle produit :

- component scores ;
- score global si autorisé ;
- confidence ;
- status ;
- warnings ;
- explanation refs ;
- decision éventuelle.

## 12.6 Score

Un `Score` est un résumé.

Règles :

- pas de score sans evaluation ;
- pas de score sans measurements ;
- pas de score sans profile ;
- pas de score sans pack/context ;
- pas de score esthétique universel ;
- confidence séparée du score.

Phrase :

> **Le score mesure la correspondance ; la confidence mesure la fiabilité de cette correspondance.**

## 12.7 Decision

Une `Decision` est une conclusion structurée.

Exemples :

- `a_closer` ;
- `b_closer` ;
- `tie` ;
- `ambiguous` ;
- `non_comparable` ;
- `duplicate` ;
- `quasi_duplicate`.

Elle doit référencer :

- scores ;
- measurements ;
- profile ;
- pack ;
- warnings ;
- alternatives ;
- raisons.

## 12.8 Explanation

Une `Explanation` est une projection lisible de mesures, scores et decisions.

Elle ne crée pas de vérité nouvelle.

Elle doit contenir :

- claim principal ;
- measurements sources ;
- écarts ;
- tolérances ;
- status ;
- warnings ;
- limitations ;
- provenance.

Elle ne doit pas contenir :

- hallucination ;
- texte décoratif non traçable ;
- intention supposée ;
- esthétique universelle.

## 12.9 Comparaison V1

`compareCompositionsBasic` est V1 strict seulement si :

- deux compositions ;
- même pack ;
- même pack lock ;
- même profile ;
- mêmes tolérances ;
- même coordinate system ;
- même metric policy ;
- même operation context ;
- pas de recommandation créative.

---

# 13. Artifacts et exports

## 13.1 Verdict

> **Un `Artifact` est une représentation dérivée d’un résultat Norma. Il ne doit jamais devenir source de vérité.**

## 13.2 Source de vérité

Source de vérité :

- `Run` ;
- `PackLock` ;
- structured input ;
- `Construction` ;
- `Measurement` ;
- `Evaluation` ;
- `Decision` ;
- `Explanation` structurée ;
- operation context.

Pas source de vérité :

- SVG ;
- CSV ;
- DXF ;
- PNG ;
- PDF ;
- plugin payload ;
- screenshot ;
- canvas ;
- UI layer.

## 13.3 Types d’artifacts

|Artifact|Statut|Rôle|
|---|---|---|
|`StructuredResultArtifact`|V1 strict|Représentation structurée principale.|
|`ConstructionSummaryArtifact`|V1 strict|Résumé de construction.|
|`EvaluationReportArtifact`|V1 strict|Rapport d’évaluation.|
|`ExplanationArtifact`|V1 strict|Explication structurée.|
|`SimpleVisualArtifact`|V1 strict limité|Projection visuelle simple.|
|CSV measurements|V1.5|Tabulaire, lossy.|
|DXF|Futur|CAD projection.|
|PDF report|Futur|Rapport humain.|
|PNG overlay|Futur|Visual overlay.|
|Plugin payload|Futur|Adapter-specific.|

## 13.4 Artifact contract

Un artifact doit déclarer :

- artifact type ;
- source objects ;
- source run/ref ;
- pack lock ;
- format ;
- audience ;
- options ;
- provenance ;
- warnings ;
- limitations ;
- lossy/lossless ;
- replayability ;
- stale status.

## 13.5 Interdictions

Un artifact ne doit pas contenir :

- ratio absent du pack ;
- rule nouvelle ;
- measurement inventée ;
- score sans evaluation ;
- explanation non traçable ;
- correction manuelle non déclarée ;
- export options cachées ;
- vérité non sourcée.

## 13.6 Opérations d’artifact V1

Les artifacts V1 doivent être produits par des opérations déclarées ou par un artifact layer strictement dérivé des source objects Norma. L’observation souligne qu’il faut nommer ces opérations pour éviter que chaque client produise ses artifacts “à sa façon”.

Opérations V1 :

- `createStructuredResultArtifact` ;
- `createConstructionSummaryArtifact` ;
- `createEvaluationReportArtifact` ;
- `createExplanationArtifact` ;
- `createSimpleVisualArtifact`.

## 13.7 SimpleVisualArtifact

`SimpleVisualArtifact` peut exister en V1 strict limité.

Il peut représenter :

- surface ;
- guides ;
- zones ;
- grille simple ;
- diagonales ;
- intersections ;
- labels minimaux ;
- warnings visibles.

Il ne doit pas :

- devenir modèle interne ;
- masquer warnings critiques ;
- contenir rules nouvelles ;
- servir de replay source unique.

---

# 14. Identity, idempotence et replay

## 14.1 Verdict

> **Norma doit pouvoir prouver pourquoi un résultat existe, avec quelles entrées, quelles versions, quelles règles, quelles tolérances et quelles sources.**

## 14.2 Idempotence

Règle complète :

```
same structured input+ same pack identity+ same pack content identity+ same rule identity+ same operation version+ same geometry model version+ same tolerance policy+ same rounding policy+ same coordinate policy+ same metric policy+ same feature flags= same construction / measurement / evaluation / artifact source result
```

## 14.3 Identités

|Objet|Identité V1|
|---|---|
|`RatioPack`|semantic identity + version + content identity|
|`Ratio`|semantic identity dans pack|
|`RatioSequence`|semantic identity dans pack|
|`Rule`|semantic identity dans pack + rule type|
|`RuleSet`|semantic identity dans pack|
|`Space`|local identity + optional content identity|
|`Construction`|run-derived identity|
|`Guide`|local deterministic identity|
|`Zone`|local deterministic identity|
|`Measurement`|local deterministic identity|
|`Evaluation`|run-derived identity|
|`Score`|local identity dans evaluation|
|`Decision`|run-derived identity|
|`Explanation`|local identity|
|`Artifact`|artifact identity|
|`Run`|run identity|

## 14.4 Run

Un `Run` doit contenir conceptuellement :

- run identity ;
- operation ;
- operation version ;
- input ou input ref ;
- operation context ;
- core version ;
- geometry model version ;
- pack refs ;
- pack locks ;
- rule refs ;
- rule set refs ;
- evaluation profile ref si applicable ;
- tolerances ;
- coordinate system ;
- metric policy ;
- numeric policy ;
- rounding policy ;
- ordering policy ;
- feature flags ;
- output refs ;
- warnings ;
- errors ;
- status ;
- provenance.

## 14.5 Run ne doit pas dépendre de

- état UI ;
- état caméra ;
- timestamp comme identité principale ;
- chemin fichier non stable ;
- random caché ;
- ordre d’insertion accidentel ;
- objet natif externe non normalisé ;
- artifact comme seule source.

## 14.6 PackLock

`PackLock` contient :

- pack id ;
- pack version ;
- pack schema version ;
- content identity ;
- compatibility info.

## 14.7 Replay-readiness vs replay opérationnel

|Élément|Statut|
|---|---|
|`Run` conceptuel|V1 strict|
|`PackLock` conceptuel|V1 strict|
|`OperationContext` conceptuel|V1 strict|
|idempotence|V1 strict|
|deterministic ordering|V1 strict|
|canonicalization conceptuelle|V1 strict|
|hashing conceptuel|V1 strict|
|`replayRun` opération complète|V1.5|
|`verifyRun`|V1.5|
|`verifyArtifactFreshness`|V1.5|

Règle :

> **V1 strict doit préparer le replay sans promettre trop tôt un replay opérationnel complet.**

## 14.8 Mismatches

Doivent être explicites :

- pack version mismatch ;
- pack content identity mismatch ;
- operation version mismatch ;
- geometry model version mismatch ;
- tolerance policy mismatch ;
- coordinate policy mismatch ;
- metric policy mismatch ;
- feature flags mismatch ;
- artifact stale ;
- missing source ;
- non-replayable external reference.

---

# 15. Interfaces, adapters, agents et function/tool readiness

## 15.1 Verdict

> **Interfaces et adapters sont des clients du core. Ils exposent, traduisent, affichent, importent ou exportent Norma Core ; ils ne définissent pas Norma Core.**

Cette frontière est explicitement verrouillée dans les fichiers : interfaces et adapters appellent ou traduisent, mais ne déterminent pas la logique Norma.

## 15.2 Types d’interfaces

|Interface|Statut|Rôle|
|---|---|---|
|CLI|V1.5|Appel local.|
|SDK|V1.5|Surface développeur.|
|API locale/process|V1.5|Transport.|
|MCP server minimal|V1.5|Interface agent.|
|Agent playbooks|V1.5|Orchestration encadrée.|
|Plugins natifs|Futur|Intégration logicielle.|
|Camera app|Futur|Capture/overlay.|
|CAD adapters|Futur ou V1.5 non-core|Traduction géométrique.|
|Design tool adapters|V1.5/futur|Traduction frames/bounds.|
|Cloud API|Futur|Exécution distante.|

## 15.3 Adapter contract

Un adapter doit :

- identifier la source externe ;
- extraire/recevoir des données géométriques ;
- convertir vers repère Norma ;
- produire des objets Norma structurés ;
- déclarer pertes et hypothèses ;
- préserver provenance ;
- appeler des opérations core explicites ;
- transmettre pack, rules, tolerances, context ;
- retourner warnings/errors sans les masquer ;
- produire ou transformer des artifacts ;
- marquer exports lossy/stale/non-replayable si nécessaire.

Un adapter ne doit pas :

- contenir des ratios cachés ;
- créer des rules ;
- choisir un pack implicite ;
- choisir une tolérance implicite ;
- faire entrer un objet natif externe dans le modèle core ;
- supprimer warnings ;
- produire une evaluation sans measurements ;
- produire une explanation sans sources ;
- utiliser l’ordre de sélection UI comme sémantique sauf déclaration explicite.

## 15.4 Agent-readiness

Norma doit offrir aux agents :

- opérations explicites ;
- structured inputs ;
- structured outputs ;
- warnings/errors ;
- run/runRef ;
- artifacts ;
- explanations traçables ;
- pack lock ;
- operation context ;
- no hallucinated ratios ;
- no hallucinated rules ;
- no beauty score.

## 15.5 Interdictions agent

Un agent ne doit pas :

- inventer un ratio ;
- inventer une rule ;
- inventer un pack ;
- inventer un score ;
- inventer une explanation ;
- ignorer warnings critiques ;
- convertir prompt libre en source de vérité ;
- faire une claim esthétique universelle ;
- inférer l’intention d’un auteur.

## 15.6 Function/tool readiness

Norma Core doit être exposable plus tard sous forme de functions, tools ou méthodes SDK, mais ces functions ne deviennent pas le core.

Chaque function/tool future doit correspondre à une opération Norma déclarée.

Un tool doit déclarer :

|Élément|Rôle|
|---|---|
|`operation`|Opération core appelée.|
|`inputContract`|Input structuré attendu.|
|`outputContract`|Output structuré retourné.|
|`requiredPackLock`|Pack requis si applicable.|
|`requiredProfile`|Profile requis si evaluation.|
|`warningsPolicy`|Warnings retournés sans suppression.|
|`errorPolicy`|Erreurs retournées sans transformation opaque.|
|`artifactPolicy`|Artifacts dérivés, jamais source.|
|`replayPolicy`|Run ou runRef retourné si applicable.|

Interdictions :

- un tool MCP ne crée pas une rule ;
- une function SDK ne hardcode pas un ratio ;
- une API ne choisit pas silencieusement un pack ;
- une CLI ne transforme pas un SVG en modèle ;
- un agent ne transforme pas une préférence utilisateur en résultat Norma.

Phrase à verrouiller :

> **Aucune function exposée à un agent ou client ne doit accepter un prompt libre comme substitut à l’input Norma structuré.**

---

# 16. Status, errors, warnings et validation

## 16.1 Verdict

> **Warnings, errors, statuses et ambiguity states sont des sorties de premier niveau.**

Norma ne doit pas deviner silencieusement.

## 16.2 Status taxonomy par domaine

Les statuts doivent être typés par domaine.

Règle :

> **Un status ne doit pas être réutilisé de manière floue entre run, evaluation, comparison, artifact et adapter.**

## 16.3 Run status

|Status|Sens|
|---|---|
|`success`|Run terminé avec résultat complet.|
|`partial`|Run terminé avec résultat partiel.|
|`failed`|Run échoué.|
|`nonReplayable`|Run non rejouable strictement.|
|`stale`|Run ou output obsolète par rapport aux sources.|

## 16.4 Evaluation status

|Status|Sens|
|---|---|
|`match`|Correspondance forte.|
|`near_match`|Correspondance proche.|
|`weak_match`|Correspondance faible.|
|`no_match`|Pas de correspondance suffisante.|
|`ambiguous`|Données ou résultats trop ambigus.|

## 16.5 Comparison status

|Status|Sens|
|---|---|
|`a_closer`|A est plus proche selon le profile.|
|`b_closer`|B est plus proche selon le profile.|
|`tie`|Différence sous tolérance.|
|`duplicate`|Candidates équivalentes.|
|`quasi_duplicate`|Candidates quasi équivalentes.|
|`mirror_equivalent`|Équivalence miroir si autorisée.|
|`ambiguous`|Ranking indécidable.|
|`non_comparable`|Comparaison invalide.|

`mirror_equivalent` est futur ou V1.5 si la policy n’est pas définie.

## 16.6 Artifact status

|Status|Sens|
|---|---|
|`current`|Artifact cohérent avec ses sources.|
|`lossy`|Artifact perd une partie de la sémantique.|
|`stale`|Artifact obsolète.|
|`non_replayable`|Artifact ne suffit pas au replay.|

## 16.7 Adapter import status

|Status|Sens|
|---|---|
|`imported`|Donnée externe traduite correctement.|
|`partial`|Traduction partielle.|
|`rejected`|Donnée non traduisible vers V1.|
|`ambiguous`|Mapping incertain.|
|`lossy`|Conversion avec perte.|

## 16.8 Error and warning shape

Un `Error` ou `Warning` doit contenir conceptuellement :

|Champ|Rôle|
|---|---|
|`code`|Identifiant stable du problème.|
|`severity`|Niveau de gravité.|
|`message`|Explication lisible.|
|`targetRef`|Objet concerné.|
|`source`|Core, pack, adapter, agent, artifact.|
|`blocking`|Indique si le résultat est bloqué.|
|`provenance`|Source du diagnostic si applicable.|

Severities :

|Severity|Sens|
|---|---|
|`info`|Information non problématique.|
|`warning`|Problème non bloquant.|
|`critical_warning`|Résultat possible mais fortement limité.|
|`error`|Résultat demandé impossible.|
|`fatal`|Run invalide ou non produit.|

Règle :

> **Un agent, adapter ou client ne doit jamais supprimer un `critical_warning` ou un `error`.**

## 16.9 Validation levels

|Niveau|Question posée|
|---|---|
|`structural`|L’objet a-t-il la forme attendue ?|
|`semantic`|Les références et significations sont-elles cohérentes ?|
|`compatibility`|Pack, rule, profile, operation et geometry model sont-ils compatibles ?|
|`numeric`|Les nombres, tolérances et approximations sont-ils exploitables ?|
|`provenance`|Les sources sont-elles déclarées ?|
|`replay`|Les informations nécessaires au replay sont-elles présentes ?|
|`artifact`|L’artifact représente-t-il correctement ses sources ?|
|`adapter`|La conversion externe → Norma est-elle complète ou lossy ?|

Règle :

> **Un objet peut être structurellement valide mais sémantiquement invalide.**

Exemple :

- `3:4:5` peut être bien formé ;
- mais invalide pour une rule qui attend une position scalaire ;
- ou incompatible V1 si son `kind` n’est pas déclaré.

---

# 17. Exemples canoniques V1

## 17.1 Segment divisé en tiers

Input :

- `SegmentSpace` ;
- pack contenant `1:1:1` ou thirds ;
- rule `divideSegmentByRatioSequence`.

Output :

- points à `t = 1/3` et `t = 2/3` ;
- trois sous-segments ;
- measurements de longueur ;
- provenance pack/rule ;
- status `success`.

## 17.2 Surface divisée verticalement

Input :

- `SurfaceSpace` rectangulaire ;
- position `x = 1/3` ;
- rule `divideSurfaceVertical`.

Output :

- guide vertical ;
- deux zones ;
- widths relatives ;
- area measurements ;
- provenance ;
- warnings si zone trop petite.

## 17.3 Surface divisée horizontalement

Input :

- `SurfaceSpace` ;
- position `y = 2/3` ;
- rule `divideSurfaceHorizontal`.

Output :

- guide horizontal ;
- zones ;
- heights relatives ;
- area measurements.

## 17.4 Grille simple 3×3

Input :

- surface ;
- divisions `1:1:1` verticales et horizontales ;
- rule `createSimpleGrid`.

Output :

- guides ;
- 9 cells ;
- intersections ;
- zones ;
- measurements.

## 17.5 Diagonales et X-crossing

Input :

- surface rectangulaire ;
- rule `createDiagonals`.

Output :

- deux diagonales ;
- intersection centrale ;
- angle measurements ;
- pattern `X-crossing simple`.

## 17.6 Évaluation d’une composition simple

Input :

- surface ;
- construction ;
- composition avec elements rectangulaires ;
- measurements ;
- evaluation profile.

Output :

- distances aux guides ;
- containment ;
- overlap ;
- component scores ;
- global score si autorisé ;
- confidence ;
- warnings ;
- explanation.

## 17.7 Comparaison A/B

Input :

- composition A ;
- composition B ;
- même pack lock ;
- même profile ;
- mêmes tolerances ;
- même context.

Output :

- evaluation A ;
- evaluation B ;
- comparison decision ;
- status `a_closer`, `b_closer`, `tie`, `ambiguous` ou `non_comparable`.

## 17.8 Artifact structuré

Input :

- run ;
- construction ;
- measurements ;
- evaluation ;
- decision ;
- explanation.

Output :

- `StructuredResultArtifact` ;
- source refs ;
- warnings ;
- provenance ;
- status `current`.

## 17.9 Visual artifact

Input :

- construction ;
- visual options explicites.

Output :

- `SimpleVisualArtifact` ;
- guides/zones visibles ;
- labels minimaux ;
- warnings visibles ;
- status `current` ou `lossy`.

Règle :

> **Le visual artifact n’est pas la construction.**

---

# 18. ADR index

## 18.1 ADRs acceptés v0.1

|ADR|Titre|Statut|
|---|---|---|
|ADR-001|Core is interface-independent|Accepté|
|ADR-002|V1 uses structured 1D/2D geometry|Accepté|
|ADR-003|Explicit coordinate and metric policies|Accepté|
|ADR-004|Ratio packs are versioned sources of proportional knowledge|Accepté|
|ADR-005|RatioSequence and PartitionPattern are first-class concepts|Accepté|
|ADR-006|Rules describe, operations execute, constructions result|Accepté|
|ADR-007|V1 operations are deterministic and structured|Accepté|
|ADR-008|Constructions are source results, artifacts are derived|Accepté|
|ADR-009|Evaluation is system-relative, not beauty scoring|Accepté|
|ADR-010|Runs provide replayability|Accepté|
|ADR-011|PackLock locks pack identity and content|Accepté|
|ADR-012|Adapters translate but do not redefine core logic|Accepté|
|ADR-013|Agents may call Norma but must not invent Norma|Accepté|
|ADR-014|V1 excludes camera, image, native plugins, CAD native, cloud and marketplace|Accepté|
|ADR-015|Warnings and ambiguity are first-class outputs|Accepté|
|ADR-016|Operation contracts are stable before interface contracts|Accepté|
|ADR-017|EvaluationProfile is interpretation configuration, not proportional knowledge|Accepté|

Les observations recommandent explicitement d’ajouter ADR-016 et ADR-017 pour stabiliser les contrats d’opération avant les interfaces et clarifier `EvaluationProfile`.

## 18.2 ADR-016 — Operation contracts are stable before interface contracts

**Contexte**  
Norma sera exposé plus tard par CLI, SDK, API, MCP ou adapters. Le risque est que chaque interface invente sa propre forme d’appel.

**Décision**  
Les contrats conceptuels d’opération doivent être stabilisés avant les contrats d’interface. Une interface ne peut exposer qu’une opération déclarée.

**Conséquences**

- chaque appel porte operation, operationVersion, input, context, packLock si applicable ;
- aucun pack implicite ;
- aucune tolérance cachée ;
- outputs structurés avec status, warnings, errors, provenance ;
- MCP/SDK/API/CLI restent wrappers autour des opérations.

**Statut**  
Accepté pour v0.1.

## 18.3 ADR-017 — EvaluationProfile is interpretation configuration, not proportional knowledge

**Contexte**  
Norma doit scorer et expliquer, mais ne doit pas confondre measurements, profiles, packs et vérité esthétique.

**Décision**  
Un `EvaluationProfile` définit comment lire des measurements. Il ne définit pas les ratios, ne crée pas les rules, ne produit pas de measurements et ne porte pas de claims esthétiques universels.

**Conséquences**

- score sans profile interdit ;
- profile versionné ou référencé explicitement ;
- profile compatible avec pack/rule set ;
- weights/tolerances/status thresholds déclarés ;
- explanations dérivées des measurements ;
- pas de beauty score.

**Statut**  
Accepté pour v0.1.

## 18.4 ADRs futurs

|ADR futur|Statut|
|---|---|
|Pack registry and signatures|Futur|
|User-defined pack governance|Futur|
|Native plugin governance|Futur|
|CAD adapter fidelity levels|Futur|
|Image/vision evidence pipeline|Futur|
|3D geometry model|Futur|
|Cloud execution model|Futur|
|Advanced recommendation policy|Futur|
|Multi-pack comparison policy|Futur|

---

# 19. Matrice de traçabilité courte

|Source conceptuelle|Décision verrouillée|Section spec|ADR|
|---|---|---|---|
|Définition canonique|Norma est un moteur de géométrie proportionnelle, pas une app.|1|ADR-001|
|Scope V1|Segments, surfaces rectangulaires, compositions simples.|2, 7|ADR-002, ADR-014|
|Géométrie|Coordonnées, métrique, unités et tolérances explicites.|7|ADR-003|
|Glossaire|Ratio, Rule, Operation, Construction, Measurement, Evaluation, Artifact sont distincts.|5|ADR-006|
|Packs|Ratios et rule declarations vivent dans packs.|8, 9|ADR-004, ADR-011|
|Addenda sequences|RatioSequence, PartitionPattern, SurfaceHierarchy distincts.|8, 11|ADR-005|
|Rules/constructions|Construction = source result géométrique.|9|ADR-006, ADR-008|
|Operations|Operations déterministes, structurées, traçables.|10|ADR-007, ADR-016|
|Evaluation|Évaluation relative au système, pas beauté.|12|ADR-009, ADR-017|
|Artifacts|Artifacts dérivés, jamais source.|13|ADR-008|
|Replay|Run et PackLock fondent reproductibilité.|14|ADR-010, ADR-011|
|Interfaces/adapters|Interfaces/adapters clients du core.|15|ADR-001, ADR-012|
|Agents/tools|Agents/tools n’inventent pas Norma.|15|ADR-013, ADR-016|
|Errors/warnings|Warnings/status/errors first-class.|16|ADR-015|

---

# 20. Questions ouvertes non bloquantes pour v0.1

Ces sujets peuvent rester ouverts sans bloquer la spec v0.1 :

## 20.1 Formats exacts

- JSON exact des packs ;
- JSON exact des operations ;
- JSON exact des runs ;
- JSON exact des artifacts ;
- schémas de validation ;
- noms finaux des champs.

## 20.2 Numérique

- algorithme exact de hash ;
- canonicalisation exacte ;
- précision des floats ;
- représentation des irrationnels ;
- rounding détaillé ;
- epsilon exact ;
- signatures.

## 20.3 Evaluation

- formule exacte du score global ;
- pondérations par défaut ;
- seuils exacts ;
- confidence formula ;
- tie policy détaillée ;
- duplicate policy détaillée.

## 20.4 Interfaces

- syntaxe CLI ;
- surface SDK ;
- transport API ;
- schemas MCP ;
- noms finaux des tools ;
- versioning des interfaces.

## 20.5 Adapters

- mapping Figma/design tool ;
- mapping CAD ;
- mapping SVG ;
- mapping DXF ;
- traitement des unités CAD ;
- traitement des rotations ;
- traitement des masks/clips.

## 20.6 Artifacts avancés

- CSV columns ;
- PDF ;
- PNG overlay ;
- DXF minimal ;
- plugin payload ;
- visual style defaults.

## 20.7 Futur produit

- camera app ;
- image/vision ;
- cloud ;
- marketplace ;
- pack registry ;
- plugins natifs ;
- 3D ;
- recommandations avancées.

Règle :

> **Une question ouverte ne doit jamais être utilisée comme décision implicite.**

---

# 21. Critères de qualité de la spec v0.1

La spec v0.1 est prête si elle est :

## 21.1 Lisible

Elle doit être lisible entièrement sans relire tous les chapitres.

## 21.2 Stricte

Elle doit permettre de savoir :

- ce qui appartient au core ;
- ce qui appartient aux packs ;
- ce qui est artifact ;
- ce qui est interface ;
- ce qui est adapter ;
- ce qui est agent/tool ;
- ce qui est V1 strict ;
- ce qui est V1.5 ;
- ce qui est futur.

## 21.3 Anti-dérive

Elle doit empêcher :

- caméra trop tôt ;
- plugin trop tôt ;
- CAD natif trop tôt ;
- UI-driven architecture ;
- SVG comme modèle ;
- beauty score ;
- prompt comme input ;
- MCP qui invente rules ;
- adapter qui hardcode ratios ;
- pack implicite ;
- tolérance cachée ;
- score sans profile ;
- artifact sans source.

## 21.4 Testable conceptuellement

La spec doit permettre de formuler des tests comme :

- même input/context → même output ;
- pack content mismatch → erreur ;
- score sans profile → erreur ;
- SVG stale → warning ;
- agent invente ratio → rejet ;
- adapter conversion lossy → warning ;
- operation sans operationVersion → erreur ;
- result sans warnings/errors arrays → invalide ;
- comparison avec profiles différents → non_comparable.

---

# 22. Maintenance de la spec

## 22.1 Décisions verrouillées

Une décision verrouillée doit être dans la spec normative.

Elle ne change que via ADR.

## 22.2 Décisions ouvertes

Une décision ouverte doit rester dans `Open questions`.

Elle ne doit pas être appliquée silencieusement.

## 22.3 Versioning

Versioning recommandé :

- `v0.1` : consolidation normative conceptuelle ;
- `v0.2` : contrats d’objets plus précis ;
- `v0.3` : formats structurés plus proches implémentation ;
- `v1.0` : spec stable MVP.

## 22.4 Changement via ADR

Un ADR est requis si un changement :

- modifie la frontière core/interface ;
- ajoute un objet au core ;
- change le scope V1 ;
- change la source de vérité ;
- change identity/replay ;
- autorise une capacité précédemment exclue ;
- modifie le sens d’un score ;
- modifie le contrat d’opération ;
- modifie le status model ;
- transforme V1.5/futur en V1 strict.

## 22.5 Éviter les doublons

Règle :

> **Une décision normative apparaît une fois, puis les autres sections la référencent.**

## 22.6 Éviter l’archive morte

La spec doit rester :

- courte ;
- normative ;
- versionnée ;
- reliée aux ADRs ;
- reliée aux exemples ;
- débarrassée des doublons ;
- séparée des notes longues.

---

# 23. Décisions finales à verrouiller

Liste courte à copier dans la spec globale :

1. **Norma Core est un moteur déterministe de géométrie proportionnelle appliquée à des espaces structurés.**
2. **Norma Core V1 travaille sur segments 1D, surfaces rectangulaires 2D et compositions 2D simples.**
3. **V1 strict exclut caméra, image, vision, OpenCV, tracking, 3D, CAD natif, plugins natifs, UI complète, cloud et marketplace.**
4. **Les ratios vivent dans les packs.**
5. **Les rule declarations vivent dans les packs ; les rule types et algorithmes d’exécution vivent dans le core.**
6. **Le pack déclare quoi appliquer ; le core exécute seulement les rule types supportés.**
7. **Les operations sont la surface exécutable du core.**
8. **Les operations acceptent uniquement des inputs Norma structurés.**
9. **Un appel d’opération doit porter operation, operationVersion, input, operationContext, et les refs nécessaires aux packs, rules, profiles, tolérances et policies.**
10. **Tout ce qui peut changer le résultat doit apparaître dans l’input, context, packLock, ruleRefs, tolerances, policies, featureFlags ou operationVersion.**
11. **Un résultat d’opération doit contenir status, run/runRef, result/outputRefs, warnings, errors, provenance et context effectif.**
12. **La spec v0.1 ne verrouille pas les schémas JSON finaux, mais elle verrouille les variables conceptuelles obligatoires qui affectent les résultats.**
13. **Un `EvaluationProfile` définit comment lire des measurements ; il ne crée pas ratios, rules, measurements ou claims esthétiques.**
14. **Score = résumé dérivé ; Evaluation = analyse complète ; Confidence = fiabilité ; Decision = conclusion structurée ; Explanation = justification traçable.**
15. **Norma ne produit pas de beauty score et n’infère pas l’intention.**
16. **Les artifacts sont des représentations dérivées, jamais source de vérité.**
17. **Les artifacts V1 doivent être produits depuis des source objects Norma avec provenance, options explicites, warnings et référence au run/source.**
18. **`StructuredResultArtifact`, `ConstructionSummaryArtifact`, `EvaluationReportArtifact`, `ExplanationArtifact` et `SimpleVisualArtifact` limité sont V1 strict.**
19. **SVG simple est acceptable comme visual artifact limité, jamais comme modèle interne.**
20. **Un `Run` est l’enveloppe centrale de reproductibilité.**
21. **Un `PackLock` verrouille pack id, pack version, schema version et content identity.**
22. **Replay-readiness est V1 strict ; `replayRun`, `verifyRun` et `verifyArtifactFreshness` sont V1.5.**
23. **Warnings, errors, statuses et ambiguity states sont des sorties de premier niveau.**
24. **Les statuts doivent être typés par domaine : run, evaluation, comparison, artifact, adapter.**
25. **Un `Error` ou `Warning` doit contenir code, severity, message, targetRef, source, blocking et provenance.**
26. **Un agent, adapter ou client ne doit jamais masquer un `critical_warning` ou un `error`.**
27. **Un objet peut être structurellement valide mais sémantiquement invalide.**
28. **Une interface, function, tool, SDK method, CLI command ou MCP tool ne doit exposer que des opérations Norma déclarées.**
29. **Aucune function exposée à un agent ou client ne doit accepter un prompt libre comme substitut à l’input Norma structuré.**
30. **Interfaces et adapters sont des clients du core, pas le core.**
31. **Un adapter traduit external data → Norma structured input → core operation → Norma result → artifact → external target format.**
32. **Un external target format ne doit jamais devenir source de vérité du core.**
33. **Les objets natifs externes ne doivent pas entrer dans le modèle canonique Norma Core V1.**
34. **Les agents doivent utiliser operations explicites, structured inputs, structured outputs, warnings/errors, replay, artifacts et explanations traçables.**
35. **Un agent ne doit jamais halluciner ratio, rule, pack, score, explanation ou claim esthétique.**

---

# 24. Verdict final de consolidation

La spec v0.1 consolidée est maintenant suffisamment stricte pour empêcher les dérives principales :

- interface qui devient core ;
- pack implicite ;
- rule inventée ;
- score sans profile ;
- beauty score ;
- SVG comme source ;
- MCP/tool qui invente une capacité ;
- adapter qui redéfinit la logique ;
- replay promis trop tôt ;
- variables cachées dans les appels ;
- warnings critiques masqués.

Le changement majeur par rapport à la version précédente n’est pas une réorientation du produit. C’est un durcissement normatif : **les contrats conceptuels d’opération, les variables canoniques, les statuts, les warnings/errors et la readiness function/tool sont maintenant explicitement verrouillés.**