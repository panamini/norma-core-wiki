Base utilisée : plan PR du Chapitre 15 après verrouillage de la spec Norma Core.

# PR0 — Spec freeze / project guardrails

## 1. Scope exact de PR0

PR0 est un PR **documentation-only**.

Il verrouille les règles d’exécution du MVP avant tout code métier.

PR0 doit produire :

1. une définition stricte du MVP Norma Core ;
    
2. une liste claire des capacités V1 autorisées ;
    
3. une liste explicite des capacités hors MVP ;
    
4. une section normative `Blocked capabilities for MVP` ;
    
5. une checklist de review applicable à tous les PRs suivants ;
    
6. une définition de “PR terminé” ;
    
7. un glossaire court des objets critiques ;
    
8. un rappel des décisions verrouillées ;
    
9. une définition de la démo cible : **Surface proportionnelle évaluée** ;
    
10. une règle explicite : **aucun PR suivant ne peut contourner les guardrails de PR0**.
    

PR0 ne doit pas produire :

- code ;
    
- squelette core ;
    
- structure complète de repo ;
    
- CLI ;
    
- SDK ;
    
- API ;
    
- MCP ;
    
- UI ;
    
- caméra ;
    
- image ;
    
- vision ;
    
- plugin ;
    
- CAD ;
    
- cloud ;
    
- marketplace ;
    
- algorithmes ;
    
- schémas JSON finaux ;
    
- tickets détaillés PR1–PR12 ;
    
- nouvelle spec fonctionnelle.
    

Phrase normative à inclure telle quelle :

> PR0 verrouille les guardrails du moteur Norma Core MVP. Il ne construit ni interface, ni adapter, ni écosystème, ni logique métier.

---

## 2. Fichiers docs probables à créer ou modifier

Rester minimal. PR0 ne doit pas créer une documentation tentaculaire.

### Option recommandée : 4 fichiers

#### `docs/SPEC_FREEZE.md`

Créer.

Rôle : document source de vérité PR0.

Contenu attendu :

- statut de la spec : Chapitres 1 à 15 gelés ;
    
- rappel des décisions verrouillées ;
    
- périmètre V1 ;
    
- hors scope MVP ;
    
- règle de non-réouverture de spec sauf contradiction majeure ;
    
- définition de la démo cible ;
    
- relation entre spec, roadmap et PR plan.
    

Ce document doit dire clairement :

> La spec gelée guide l’exécution. Les PRs suivants implémentent le moteur, ils ne redéfinissent pas Norma Core.

---

#### `docs/MVP_GUARDRAILS.md`

Créer.

Rôle : document bloquant de gouvernance MVP.

Contenu attendu :

- section `Allowed in MVP` ;
    
- section `Blocked capabilities for MVP` ;
    
- règles anti-dérive ;
    
- règles anti-UI ;
    
- règles anti-image/caméra/vision ;
    
- règles anti-plugin/CAD/cloud/marketplace ;
    
- règles anti-beauty score ;
    
- règles anti-SVG-source ;
    
- règles anti-pack-implicit ;
    
- règles anti-prompt libre comme source ;
    
- règles de provenance ;
    
- règle “artifacts dérivés seulement” ;
    
- règle “ratios dans packs uniquement” ;
    
- règle “rules declarations dans packs, rule types dans core”.
    

Ce document est le plus important de PR0.

---

#### `docs/PR_REVIEW_CHECKLIST.md`

Créer.

Rôle : checklist obligatoire pour tous les PRs suivants.

Contenu attendu :

- checklist générale applicable à PR1–PR12 ;
    
- gates bloquants ;
    
- questions de review ;
    
- conditions de rejet automatique ;
    
- définition de “PR acceptable” ;
    
- rappel que chaque PR doit déclarer :
    
    - scope ;
        
    - hors scope ;
        
    - critères d’acceptation ;
        
    - tests conceptuels ;
        
    - risques ;
        
    - erreurs à éviter ;
        
    - gate.
        

Ce fichier doit être utilisable directement par reviewer.

---

#### `docs/GLOSSARY_CORE.md`

Créer ou modifier si existant.

Rôle : glossaire court, pas dictionnaire complet.

Contenu attendu minimal :

- `Core`;
    
- `Pack`;
    
- `Ratio`;
    
- `RuleDeclaration`;
    
- `RuleType`;
    
- `Construction`;
    
- `Measurement`;
    
- `Evaluation`;
    
- `Score`;
    
- `Decision`;
    
- `Explanation`;
    
- `Artifact`;
    
- `Run`;
    
- `PackLock`;
    
- `OperationContext`;
    
- `Replay-readiness`;
    
- `Source of truth`.
    

Chaque définition doit être normative et courte.

Exemple attendu :

> Artifact : projection dérivée d’objets sources Norma. Un artifact ne peut jamais devenir source de vérité.

---

### Option acceptable : 5e fichier si ADRs déjà présents

#### `docs/ADR_INDEX.md` ou `docs/adr/README.md`

Modifier seulement si le projet a déjà une zone ADR.

Rôle : index des décisions fondatrices.

Contenu attendu :

- lien ou référence vers décisions verrouillées ;
    
- statut : accepted / locked ;
    
- pas de nouvel ADR spéculatif ;
    
- pas de débat rouvert.
    

Ne pas créer tout un système ADR si rien n’existe.

---

## 3. Contenu attendu de chaque document

## `docs/SPEC_FREEZE.md`

Structure recommandée :

```txt
# Norma Core — Spec Freeze

## Status
Spec locked after Chapter 15.

## Locked decisions
- Norma Core is deterministic proportional geometry core.
- V1 supports 1D segments, 2D rectangular surfaces, simple 2D compositions.
- Ratios live in packs.
- Rule declarations live in packs.
- Rule types and algorithms live in core.
- Constructions are geometric source results.
- Measurements are calculated facts.
- Evaluations interpret measurements.
- Artifacts are derived.
- Run, PackLock, OperationContext ensure replay-readiness.

## MVP target
Surface proportionnelle évaluée.

## V1 allowed scope
...

## Explicitly out of MVP
...

## Spec change policy
No reopening unless major contradiction is found.

## PR execution rule
Every PR must comply with MVP guardrails.
```

---

## `docs/MVP_GUARDRAILS.md`

Structure recommandée :

```txt
# Norma Core MVP Guardrails

## Purpose
Prevent MVP scope drift.

## Allowed in MVP
- deterministic core;
- structured geometry input;
- segments 1D;
- rectangular 2D surfaces;
- simple 2D compositions;
- minimal ratio pack;
- rule resolution;
- construction;
- measurements;
- evaluation;
- A/B comparison;
- derived artifacts;
- Run / PackLock / OperationContext visibility;
- demo harness.

## Blocked capabilities for MVP
...

## Core truth rules
...

## Pack rules
...

## Rule rules
...

## Measurement / evaluation rules
...

## Artifact rules
...

## Replay-readiness rules
...

## Review rejection rules
...
```

La section `Blocked capabilities for MVP` doit contenir les mots exacts suivants :

```txt
UI complète
écran
canvas interactif
drag-and-drop
caméra
image
vision
OpenCV
tracking
plugin
CAD natif
cloud
marketplace
prompt libre comme source
beauty score
SVG comme modèle
export comme source de vérité
adapter comme source de logique Norma
agent-created rules
pack implicite
ratio implicite
tolérance cachée
recommendation créative
optimisation automatique
inférence d’intention
3D
polygones complexes
formats natifs
```

---

## `docs/PR_REVIEW_CHECKLIST.md`

Structure recommandée :

```txt
# Norma Core PR Review Checklist

## Required PR sections
- Scope
- Out of scope
- Deliverables
- Acceptance criteria
- Conceptual tests / reviews
- Risks
- Errors to avoid
- Gate

## Universal guardrail checks
...

## Automatic rejection checks
...

## MVP PR sequence
PR0 → PR1 → ... → PR12

## Done definition for any PR
...
```

Ce fichier doit aussi inclure la phrase :

> Un PR qui introduit une capacité explicitement bloquée par PR0 doit être refusé, même si les tests passent.

---

## `docs/GLOSSARY_CORE.md`

Structure recommandée :

```txt
# Norma Core Glossary

## Core
...

## Pack
...

## Ratio
...

## RuleDeclaration
...

## RuleType
...

## Construction
...

## Measurement
...

## Evaluation
...

## Artifact
...

## Run
...

## PackLock
...

## OperationContext
...
```

Définitions clés à verrouiller :

- `Construction` : résultat géométrique source produit par le core.
    
- `Measurement` : fait calculé à partir de géométrie/construction/composition.
    
- `Evaluation` : interprétation structurée de measurements selon pack/profile/tolérances.
    
- `Score` : résumé dérivé d’une evaluation, jamais vérité seule.
    
- `Artifact` : projection dérivée, jamais source de vérité.
    
- `PackLock` : identité effective du pack utilisé pour reproductibilité.
    
- `OperationContext` : contexte effectif qui influence le résultat.
    
- `Run` : enveloppe traçable d’une opération significative.
    

---

## 4. Checklist de guardrails MVP

Cette checklist doit être utilisée pour PR0 lui-même puis pour tous les PRs suivants.

### Scope V1 autorisé

-  Le PR reste dans Norma Core.
    
-  Le PR concerne le moteur, pas l’écosystème.
    
-  Le PR utilise uniquement des données structurées.
    
-  Le PR respecte les segments 1D, surfaces rectangulaires 2D, compositions 2D simples.
    
-  Le PR ne dépend pas d’une UI.
    
-  Le PR ne dépend pas d’un rendu.
    
-  Le PR ne dépend pas d’un fichier image.
    
-  Le PR ne dépend pas d’un outil externe comme source de vérité.
    

### Packs et ratios

-  Aucun ratio n’est hardcodé dans le core.
    
-  Aucun ratio n’est inventé par un client.
    
-  Aucun pack implicite n’est autorisé.
    
-  Aucun ratio implicite n’est autorisé.
    
-  Les ratios vivent dans les packs.
    
-  Le pack MVP reste `norma.basic-proportions@0.1.0`.
    
-  Aucun pack riche n’est introduit en MVP.
    

### Rules

-  Les rule declarations vivent dans les packs.
    
-  Les rule types vivent dans le core.
    
-  Aucune rule n’est créée par prompt.
    
-  Aucune rule n’est créée par UI, adapter ou agent.
    
-  Une rule non supportée doit produire error ou warning critique.
    

### Measurements / evaluation

-  Aucun score avant measurements.
    
-  Une measurement reste un fait calculé.
    
-  Une evaluation interprète des measurements.
    
-  Un score ne remplace pas l’evaluation.
    
-  Confidence reste séparée du score.
    
-  Beauty score interdit.
    
-  Inférence d’intention interdite.
    
-  Recommandation créative interdite en MVP.
    

### Artifacts

-  Un artifact est dérivé.
    
-  Un artifact ne devient jamais source de vérité.
    
-  SVG, export ou rendu ne peuvent pas devenir modèle core.
    
-  Les source objects gagnent toujours contre les artifacts.
    
-  Les warnings/errors critiques restent visibles.
    

### Runtime / replay-readiness

-  `Run` doit rester visible dans les résultats significatifs.
    
-  `PackLock` doit rester visible quand un pack est utilisé.
    
-  `OperationContext` doit rester visible quand il influence l’output.
    
-  Aucun default qui change l’output n’est caché.
    
-  Même input + même pack + mêmes rules + mêmes tolérances + même context + même operation version = même output.
    
-  `replayRun` complet reste hors MVP.
    

### Capacités bloquées

-  Pas de UI complète.
    
-  Pas d’écran produit.
    
-  Pas de canvas interactif.
    
-  Pas de drag-and-drop.
    
-  Pas de caméra.
    
-  Pas d’image.
    
-  Pas de vision.
    
-  Pas d’OpenCV.
    
-  Pas de tracking.
    
-  Pas de plugin.
    
-  Pas de CAD natif.
    
-  Pas de cloud.
    
-  Pas de marketplace.
    
-  Pas de prompt libre comme source.
    
-  Pas de beauty score.
    
-  Pas de SVG comme modèle.
    
-  Pas d’export comme source de vérité.
    
-  Pas d’adapter comme source de logique Norma.
    
-  Pas d’agent-created rules.
    
-  Pas de pack implicite.
    
-  Pas de ratio implicite.
    
-  Pas de tolérance cachée.
    
-  Pas d’optimisation automatique.
    
-  Pas d’inférence d’intention.
    

---

## 5. Critères d’acceptation PR0

PR0 est acceptable seulement si :

1. Le scope MVP est lisible en moins de deux minutes.
    
2. Le hors scope MVP est explicite et non ambigu.
    
3. La section `Blocked capabilities for MVP` existe.
    
4. Les mots bloquants sont présents textuellement.
    
5. La démo cible **Surface proportionnelle évaluée** est nommée.
    
6. PR0 indique que le MVP construit le moteur, pas les interfaces.
    
7. PR0 interdit explicitement UI, caméra, image, vision, plugin, CAD natif, cloud et marketplace.
    
8. PR0 interdit explicitement beauty score, inférence d’intention et recommandations créatives.
    
9. PR0 interdit explicitement SVG/export/artifact comme source de vérité.
    
10. PR0 interdit explicitement pack implicite, ratio implicite et tolérance cachée.
    
11. PR0 rappelle que ratios et rule declarations vivent dans les packs.
    
12. PR0 rappelle que rule types et algorithmes vivent dans le core.
    
13. PR0 rappelle que constructions, measurements, evaluations et artifacts sont séparés.
    
14. PR0 rappelle que `Run`, `PackLock` et `OperationContext` servent la replay-readiness.
    
15. PR0 ne crée aucun code.
    
16. PR0 ne crée aucune structure complète de repo.
    
17. PR0 ne crée aucun format final d’API.
    
18. PR0 ne crée aucun algorithme.
    
19. PR0 ne rouvre pas la spec.
    
20. PR0 donne une checklist de review réutilisable par PR1–PR12.
    

---

## 6. Tests / reviews conceptuels

PR0 n’a pas besoin de tests runtime.

Il doit avoir des **review tests**.

### Review test 1 — UI

Question :

> Est-ce qu’un PR suivant peut introduire une UI complète ?

Réponse attendue :

> Non. UI complète, écran, canvas interactif et drag-and-drop sont hors MVP.

---

### Review test 2 — image / caméra

Question :

> Est-ce qu’un PR suivant peut accepter une image, une caméra ou OpenCV comme input MVP ?

Réponse attendue :

> Non. Le MVP utilise uniquement des données géométriques structurées.

---

### Review test 3 — SVG comme source

Question :

> Est-ce qu’un SVG ou un visual artifact peut devenir le modèle source ?

Réponse attendue :

> Non. Les artifacts sont dérivés. Les source objects structurés gagnent toujours.

---

### Review test 4 — pack implicite

Question :

> Est-ce qu’une opération peut utiliser un ratio ou un pack implicite ?

Réponse attendue :

> Non. Pack absent, ratio absent ou ratio implicite doivent être rejetés.

---

### Review test 5 — beauty score

Question :

> Est-ce que Norma peut produire un score de beauté ?

Réponse attendue :

> Non. Norma peut évaluer la proximité à un système déclaré, pas juger la beauté.

---

### Review test 6 — rules créées par agent

Question :

> Est-ce qu’un agent, une UI ou un adapter peut créer une rule ad hoc ?

Réponse attendue :

> Non. Les rule declarations vivent dans les packs. Les rule types supportés vivent dans le core.

---

### Review test 7 — artifacts

Question :

> Est-ce qu’un artifact peut contenir une measurement ou une evaluation absente des source objects ?

Réponse attendue :

> Non. Un artifact ne peut pas inventer de vérité.

---

### Review test 8 — replay-readiness

Question :

> Est-ce que PR0 exige un `replayRun` complet ?

Réponse attendue :

> Non. PR0 exige replay-readiness, pas replay complet.

---

## 7. Risques PR0

### Risque 1 — PR0 devient une réécriture de spec

Protection :

- limiter PR0 aux guardrails ;
    
- ne pas redéfinir les algorithmes ;
    
- ne pas ajouter de nouvelles capacités.
    

---

### Risque 2 — Guardrails trop vagues

Protection :

- utiliser les mots exacts des capacités bloquées ;
    
- ajouter des questions de review binaires ;
    
- définir des conditions de rejet automatique.
    

---

### Risque 3 — Confusion entre MVP et V1.5

Protection :

- marquer CLI, SDK, MCP, replay complet, adapters et packs riches comme post-MVP ;
    
- ne pas les préparer dans PR0 sauf comme exclusions.
    

---

### Risque 4 — PR0 devient un plan PR détaillé complet

Protection :

- référencer la séquence PR0–PR12 ;
    
- ne pas détailler PR1–PR12 au-delà des gates généraux.
    

---

### Risque 5 — Le développeur commence à coder

Protection :

- mettre en haut des docs : `Documentation only. No runtime implementation.`
    
- refuser tout fichier source ajouté dans PR0.
    

---

### Risque 6 — Des décisions ouvertes deviennent implicites

Protection :

- toute décision non verrouillée reste hors PR0 ;
    
- pas de choix de framework ;
    
- pas de choix de transport ;
    
- pas de choix de format final.
    

---

## 8. Erreurs à éviter

Ne pas faire dans PR0 :

- ajouter un dossier `src/` ;
    
- ajouter un package ;
    
- ajouter une CLI ;
    
- ajouter un SDK ;
    
- ajouter un serveur ;
    
- ajouter un schéma JSON final ;
    
- ajouter un exemple SVG comme vérité ;
    
- ajouter une image de démo ;
    
- ajouter un canvas ;
    
- ajouter une intégration CAD ;
    
- ajouter un plugin ;
    
- ajouter un pack riche ;
    
- ajouter une liste de ratios hors pack MVP ;
    
- ajouter une règle exécutable ;
    
- ajouter un scoring ;
    
- ajouter un “beauty score” ;
    
- ajouter une recommandation ;
    
- ajouter une optimisation automatique ;
    
- introduire un langage de rules ;
    
- introduire des agents ;
    
- promettre `replayRun` complet ;
    
- rouvrir les Chapitres 1 à 15 ;
    
- reformuler les décisions verrouillées en options.
    

Erreur de formulation à éviter :

```txt
Norma dit quelle composition est meilleure.
```

Formulation correcte :

```txt
Norma indique quelle composition est plus proche du système proportionnel déclaré.
```

Erreur de formulation à éviter :

```txt
Le SVG montre le résultat Norma.
```

Formulation correcte :

```txt
Le SVG éventuel est une projection dérivée des source objects Norma.
```

Erreur de formulation à éviter :

```txt
Le pack par défaut est utilisé si aucun pack n’est fourni.
```

Formulation correcte :

```txt
Pack absent = erreur. Aucun pack implicite.
```

---

## 9. Définition de done PR0

PR0 est done quand :

1. les documents PR0 existent ;
    
2. chaque document a un rôle clair ;
    
3. le PR est documentation-only ;
    
4. aucun fichier runtime n’est ajouté ;
    
5. aucun code métier n’est ajouté ;
    
6. aucun choix technique prématuré n’est ajouté ;
    
7. les décisions verrouillées sont reprises sans modification ;
    
8. les capacités bloquées sont listées explicitement ;
    
9. la checklist MVP est utilisable en review ;
    
10. les critères de rejet automatique sont écrits ;
    
11. la démo cible est nommée ;
    
12. les artifacts sont définis comme dérivés ;
    
13. le beauty score est explicitement interdit ;
    
14. le pack implicite est explicitement interdit ;
    
15. le SVG comme source est explicitement interdit ;
    
16. `Run`, `PackLock`, `OperationContext` sont mentionnés comme exigences de replay-readiness ;
    
17. PR0 ne crée pas PR1 ;
    
18. PR0 ne crée pas la structure complète du repo ;
    
19. un reviewer peut répondre oui/non à chaque guardrail ;
    
20. un PR suivant qui viole PR0 peut être refusé sans débat.
    

Gate final :

> PR0 passe seulement si aucun PR suivant ne peut raisonnablement prétendre que UI, caméra, image, plugin, CAD natif, cloud, marketplace, beauty score, pack implicite ou SVG comme modèle sont autorisés dans le MVP.

---

## 10. Prompt court pour le développeur

```txt
Implémente PR0 uniquement.

Objectif : créer les documents de spec freeze et guardrails MVP pour Norma Core après Chapitre 15.

Contraintes strictes :
- documentation only ;
- aucun code ;
- aucun squelette core ;
- aucune structure complète de repo ;
- aucune UI, caméra, image, vision, plugin, CAD, cloud, marketplace ;
- ne pas rouvrir la spec ;
- ne pas créer PR1.

À produire :
1. docs/SPEC_FREEZE.md
2. docs/MVP_GUARDRAILS.md
3. docs/PR_REVIEW_CHECKLIST.md
4. docs/GLOSSARY_CORE.md
5. optionnel : docs/ADR_INDEX.md seulement si une zone ADR existe déjà.

Les docs doivent verrouiller :
- scope V1 ;
- hors MVP ;
- Blocked capabilities for MVP ;
- règles anti-dérive ;
- artifacts dérivés, jamais source de vérité ;
- ratios dans packs ;
- rule declarations dans packs ;
- rule types/algorithmes dans core ;
- measurements avant evaluation ;
- aucun beauty score ;
- aucun pack/ratio/tolérance implicite ;
- Run, PackLock, OperationContext pour replay-readiness ;
- démo cible : “Surface proportionnelle évaluée”.

Critère de done :
PR0 doit permettre à un reviewer de refuser tout PR suivant qui introduit UI, caméra, image, plugin, CAD natif, cloud, marketplace, prompt libre comme source, beauty score, SVG comme modèle, pack implicite, ratio implicite ou tolérance cachée.
```