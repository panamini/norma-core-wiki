# Norma — Vision produit, UX cible et architecture d’intégration

**Statut : brouillon de cadrage à corriger**  
**Objet : définir l’expérience voulue avant de poursuivre les PR d’implémentation**

---

## 1. Résumé exécutif

Norma doit devenir un **moteur d’intelligence proportionnelle** utilisable depuis plusieurs interfaces :

1. **ChatGPT** pour analyser une image et expliquer ses structures proportionnelles ;
2. **ChatGPT** pour construire une composition géométrique selon un système déclaré, puis la vérifier ;
3. **Norma Camera** pour détecter en direct les lignes, axes, rectangles, alignements et rapports d’une scène ;
4. **AutoCAD** pour évaluer dynamiquement une géométrie dessinée par un architecte ;
5. plus tard, d’autres adapters : Figma, Illustrator, Blender, web, batch QA et outils pédagogiques.

La règle d’architecture centrale est :

> **Norma Core reçoit de la géométrie structurée. Les images, prompts, caméras et formats CAD sont traités par des adapters spécialisés.**

L’utilisateur peut voir un seul produit nommé « Norma », mais l’implémentation reste séparée :

```text
Interface utilisateur
→ adapter de perception ou d’intégration
→ géométrie / intention structurée
→ Norma Core
→ measurements / evaluations / explanations
→ overlay, SVG, image ou UI dérivée
```

Cette séparation permet de conserver un core déterministe, testable et commun à tous les produits.

---

## 2. Ce qui existe et ce qui est visé

### 2.1 État actuel

Le track PR67–PR70 a livré un **viewer local read-only de JSON structuré** et des tests de démonstration synthétiques.

Il ne constitue pas encore :

- une application déployée ;
- une app ChatGPT connectée à Norma ;
- une analyse d’image ;
- une génération géométrique conversationnelle complète ;
- une app caméra ;
- un plugin AutoCAD.

### 2.2 Vision cible

La vision cible est une famille cohérente :

- **Norma Core** : moteur déterministe de construction, mesure et évaluation ;
- **Norma Codex** : bibliothèque versionnée de packs d’harmonies ;
- **Norma Vision** : image → observations géométriques ;
- **Norma ChatGPT App** : orchestration conversationnelle et interface dans ChatGPT ;
- **Norma Camera** : perception live mobile ;
- **Norma CAD** : adapters AutoCAD et autres logiciels de dessin ;
- **Norma Renderer** : overlays, SVG, guides et exports dérivés.

---

## 3. Promesse produit

### 3.1 Ce que Norma dit

Norma peut dire :

- quelles structures géométriques sont détectées ;
- quelles mesures ont été calculées ;
- à quel système proportionnel déclaré la composition est comparée ;
- quels rapports sont proches ou éloignés des rapports du pack ;
- où se trouvent les axes, alignements, divisions et points structurants ;
- avec quelle confiance une géométrie a été extraite d’une image ;
- quelles modifications géométriques explicites rapprocheraient la composition du système choisi.

### 3.2 Ce que Norma ne doit pas dire

Norma ne doit pas prétendre :

- qu’une composition est « belle » ou « la meilleure » ;
- qu’une observation visuelle incertaine est un fait certain ;
- qu’un raster, un SVG ou un overlay est la source de vérité ;
- qu’une règle inventée par le modèle fait partie du Codex ;
- qu’un pack ou une tolérance cachée a été utilisé ;
- qu’une intention artistique a été devinée sans confirmation.

La formulation correcte est :

> « Cette composition est plus ou moins proche du système proportionnel explicitement sélectionné. »

---

## 4. Modèle conceptuel du produit

### 4.1 Norma Core

Responsabilités :

- recevoir une entrée géométrique structurée ;
- résoudre un pack explicite ;
- construire des géométries supportées ;
- calculer des measurements ;
- produire des evaluations ;
- comparer des variantes ;
- générer des explanations ;
- conserver Run, PackLock, OperationContext et provenance.

Norma Core ne doit pas :

- décoder un JPEG ;
- ouvrir une caméra ;
- comprendre un prompt libre directement ;
- dépendre de ChatGPT ;
- dépendre d’AutoCAD ;
- générer une UI ;
- modifier silencieusement un dessin.

### 4.2 Norma Codex

Le « Codex d’harmonies » est une bibliothèque de packs versionnés.

Un pack contient :

- ratios nommés ;
- rule declarations ;
- profils de tolérance explicites ;
- métadonnées, références et version.

Le core contient :

- rule types ;
- algorithmes ;
- validation ;
- mesure ;
- évaluation.

Exemples de packs futurs à valider :

- nombre d’or ;
- rectangles racines ;
- divisions harmoniques ;
- grilles modulaires ;
- systèmes architecturaux historiques ;
- rapports musicaux transposés en proportions visuelles.

Aucun de ces packs ne doit être considéré comme existant tant qu’il n’est pas réellement implémenté et versionné.

### 4.3 Adapters

Les adapters traduisent un environnement externe vers les contrats structurés de Norma.

Exemples :

- `norma-vision-adapter` : JPEG/PNG → GeometryObservation ;
- `norma-chatgpt-app` : conversation → DesignIntent ou AnalysisRequest ;
- `norma-camera-adapter` : frames → observations stabilisées ;
- `norma-autocad-adapter` : entités CAD → StructuredGeometry ;
- `norma-renderer` : résultats → overlay/SVG/image dérivée.

---

## 5. Décision d’architecture pour l’analyse d’image

### 5.1 Question

Qui transforme le JPEG en géométrie ?

- ChatGPT Vision ?
- Norma elle-même ?
- les deux ?

### 5.2 Option A — ChatGPT fait la perception

Pipeline :

```text
Image utilisateur
→ modèle vision OpenAI
→ GeometryObservation JSON
→ Norma Core
→ résultat structuré
→ explication + overlay dans ChatGPT
```

Avantages :

- chemin le plus rapide vers une démo utilisable ;
- pas de pipeline OpenCV à construire immédiatement ;
- expérience entièrement conversationnelle ;
- extraction sémantique possible : sujet, cadre, hiérarchie visuelle.

Risques :

- coordonnées potentiellement imprécises ;
- variation entre exécutions ;
- difficulté à garantir une vectorisation pixel-perfect ;
- nécessité de conserver confidence et provenance ;
- nécessité d’un écran de correction ou de confirmation.

### 5.3 Option B — Norma Vision fait la perception

Pipeline :

```text
Image utilisateur
→ Norma Vision
→ lignes / coins / rectangles / axes / perspective
→ GeometryObservation JSON
→ Norma Core
→ résultat structuré
→ overlay
```

Avantages :

- plus de contrôle sur les coordonnées ;
- reproductibilité supérieure ;
- réutilisable dans Norma Camera ;
- tests géométriques plus précis ;
- possibilité d’exécution locale/on-device.

Risques :

- coût d’implémentation supérieur ;
- calibration, perspective et occlusion complexes ;
- besoin de jeux de tests image annotés ;
- besoin de métriques de précision.

### 5.4 Recommandation — architecture hybride

Commencer par l’option A pour le premier vertical slice, tout en définissant le contrat de sorte que l’option B puisse remplacer ou compléter la perception plus tard.

```text
PerceptionProvider
├── OpenAI Vision provider — premier prototype
├── Norma Vision provider — précision et caméra
└── CAD provider — géométrie exacte, sans vision
```

Norma Core ne connaît pas le provider. Il reçoit toujours une `GeometryObservation` normalisée.

### 5.5 Pas de « nuage de points » par défaut pour une image 2D

Pour une image standard, les primitives utiles sont plutôt :

- coins et intersections ;
- centres ;
- lignes et segments ;
- axes dominants ;
- rectangles et régions ;
- diagonales ;
- points de fuite ;
- alignements ;
- relations proportionnelles ;
- confidence par primitive.

Un vrai nuage de points 3D devient utile pour LiDAR, photogrammétrie ou reconstruction 3D, donc dans une phase ultérieure distincte.

---

## 6. Contrat image → géométrie

Exemple conceptuel :

```json
{
  "kind": "geometry-observation",
  "source": {
    "kind": "image",
    "width": 2048,
    "height": 1536,
    "coordinateSystem": "image-pixels-top-left"
  },
  "primitives": [
    {
      "id": "line:1",
      "kind": "segment-2d",
      "a": { "x": 120, "y": 320 },
      "b": { "x": 1800, "y": 315 },
      "confidence": 0.93
    },
    {
      "id": "rect:1",
      "kind": "rectangle-2d",
      "x": 300,
      "y": 200,
      "width": 987,
      "height": 610,
      "confidence": 0.87
    }
  ],
  "axes": [
    {
      "id": "axis:vertical-main",
      "kind": "vertical-axis",
      "x": 1024,
      "confidence": 0.81
    }
  ],
  "provenance": {
    "provider": "openai-vision",
    "providerVersion": "explicit-version",
    "extractionRunId": "explicit-run-id"
  }
}
```

Ce document est une proposition de contrat, pas un schéma déjà approuvé.

---

## 7. UX globale

### 7.1 Principe

L’utilisateur ne doit pas avoir à comprendre les couches techniques.

Il voit :

> **Analyser avec Norma**

Mais le produit doit toujours rendre visibles :

- la source ;
- le système proportionnel sélectionné ;
- la tolérance ;
- le niveau de confiance ;
- les mesures ;
- les avertissements ;
- la distinction observation / fait calculé / interprétation ;
- le fait que les overlays sont dérivés.

### 7.2 Structure commune des résultats

Tous les produits Norma devraient afficher les mêmes blocs :

1. **Résumé** — résultat en langage humain ;
2. **Système utilisé** — pack et version ;
3. **Géométrie détectée ou fournie** ;
4. **Measurements** — faits calculés ;
5. **Evaluations** — interprétation selon le pack ;
6. **Harmonies détectées** ;
7. **Écarts** — distances aux rapports cibles ;
8. **Confiance** — uniquement pour la perception ;
9. **Explication** ;
10. **Overlay** — dérivé ;
11. **Provenance** — Run, PackLock, OperationContext ;
12. **Actions** — comparer, ajuster, exporter, corriger la détection.

### 7.3 Vocabulaire UX

Préférer :

- « proximité au nombre d’or » ;
- « relation détectée » ;
- « mesure » ;
- « écart » ;
- « confiance de détection » ;
- « système sélectionné » ;
- « proposition d’ajustement ».

Éviter :

- « beauté » ;
- « parfait » ;
- « mauvais design » ;
- « Norma sait ce que l’artiste voulait » ;
- « vérité visuelle ».

---

## 8. Cas d’usage 1 — Analyser une image dans ChatGPT

### 8.1 Intention utilisateur

> « Analyse cette affiche avec Norma. Montre-moi les axes, les rapports et les harmonies. »

### 8.2 Parcours UX

1. L’utilisateur joint une image dans ChatGPT.
2. ChatGPT propose ou reconnaît l’action **Analyser avec Norma**.
3. Une carte de paramètres apparaît :
   - type d’analyse ;
   - pack d’harmonies ;
   - tolérance ;
   - mode perspective ou plan ;
   - niveau de détail.
4. La perception extrait la géométrie avec confidence.
5. L’utilisateur peut corriger les lignes/rectangles détectés.
6. ChatGPT appelle Norma Core avec la géométrie validée.
7. Norma retourne measurements, evaluations et explanations.
8. ChatGPT affiche :
   - résumé ;
   - overlay ;
   - axes ;
   - rapports ;
   - écarts ;
   - confidence ;
   - avertissements.
9. Actions suivantes :
   - comparer avec un autre pack ;
   - ajuster la détection ;
   - exporter le JSON ;
   - exporter un SVG overlay ;
   - proposer une variante corrigée.

### 8.3 Widget ChatGPT cible

Onglets proposés :

- **Vue** ;
- **Structure** ;
- **Rapports** ;
- **Écarts** ;
- **Provenance**.

Contrôles :

- afficher/masquer axes ;
- afficher/masquer rectangles ;
- choisir le pack ;
- ajuster la tolérance ;
- corriger une primitive ;
- relancer l’analyse.

### 8.4 Source de vérité

- Le JPEG est la source asset originale.
- La `GeometryObservation` est une observation dérivée et incertaine.
- Les measurements sont calculées depuis la géométrie structurée.
- Les evaluations interprètent les measurements.
- L’overlay est un artifact dérivé.

---

## 9. Cas d’usage 2 — Créer une image ou une géométrie avec ChatGPT et Norma

### 9.1 Intention utilisateur

> « Crée une composition 16:9 organisée selon le nombre d’or, avec un espace de titre et un sujet principal. »

### 9.2 Parcours recommandé

```text
Prompt utilisateur
→ ChatGPT produit un DesignIntent structuré
→ utilisateur confirme pack, dimensions et contraintes
→ Norma Core construit la géométrie
→ Norma Core mesure et vérifie
→ renderer produit SVG/layout guide
→ moteur d’image applique le style
→ vérification finale par Norma
```

### 9.3 Étapes UX

1. ChatGPT reformule l’intention en paramètres visibles :
   - dimensions ;
   - pack choisi ;
   - ratio principal ;
   - zones ;
   - contraintes ;
   - tolérance.
2. L’utilisateur confirme ou corrige.
3. Norma construit une géométrie exacte.
4. Norma affiche un rapport de vérification.
5. Un SVG ou plan vectoriel est généré depuis cette géométrie.
6. Une image peut être rendue ou stylisée.
7. Une vérification post-rendu compare le résultat final au plan.

### 9.4 Décision importante

Pour garantir des proportions exactes :

- construire d’abord un layout vectoriel déterministe ;
- utiliser le modèle génératif pour le style et le contenu ;
- ne pas utiliser le raster généré comme unique source de vérité ;
- conserver le plan géométrique Norma et le Run associés.

### 9.5 Interface ChatGPT cible

Carte **Plan Norma** :

- Pack : nombre d’or, version explicite ;
- Canvas : largeur × hauteur ;
- Guides : axes et divisions ;
- Contraintes : marges, zones, alignements ;
- Vérification : passed/warning/error ;
- Actions : générer, modifier, comparer, exporter SVG/JSON.

---

## 10. Cas d’usage 3 — Norma Camera

### 10.1 Intention utilisateur

L’utilisateur pointe son téléphone vers :

- une façade ;
- un objet ;
- une affiche ;
- une pièce ;
- une œuvre ;
- un cadrage photo.

Norma affiche en direct les structures détectées.

### 10.2 Pipeline

```text
Flux caméra
→ calibration et correction perspective
→ détection de primitives
→ tracking temporel
→ GeometryObservation stabilisée
→ Norma Core
→ overlay live
```

### 10.3 UX mobile

Écran principal :

- caméra plein écran ;
- overlay axes/lignes/rectangles ;
- pack actif visible ;
- confidence globale ;
- état : stable / incertain / insuffisant ;
- bouton Freeze ;
- bouton Calibrate ;
- bouton Compare ;
- bouton Save Run.

Après Freeze :

- correction manuelle des primitives ;
- measurements ;
- evaluations ;
- explication ;
- export image annotée + JSON.

### 10.4 Architecture

Norma Camera ne doit pas copier la logique métier du core.

Elle contient :

- capture ;
- vision ;
- tracking ;
- calibration ;
- présentation mobile.

Elle appelle le même Norma Core que ChatGPT et AutoCAD.

---

## 11. Cas d’usage 4 — AutoCAD

### 11.1 Intention utilisateur

Pendant que l’architecte dessine, Norma évalue la géométrie sélectionnée ou le viewport.

### 11.2 Pipeline

```text
Entités AutoCAD
→ adapter CAD
→ unités et coordonnées normalisées
→ StructuredGeometry
→ Norma Core
→ résultat
→ panel + guides AutoCAD
```

Ici, aucune vision n’est nécessaire : AutoCAD fournit déjà une géométrie exacte.

### 11.3 UX plugin

Panel latéral **Norma** :

- Scope : sélection / layer / viewport ;
- Pack actif ;
- Tolérance ;
- statut live ;
- rapports détectés ;
- écarts ;
- warnings ;
- explications ;
- guides affichables.

Actions :

- afficher les guides ;
- comparer deux variantes ;
- créer une construction auxiliaire ;
- proposer un ajustement ;
- appliquer explicitement l’ajustement ;
- sauvegarder le Run.

### 11.4 Règle de sécurité UX

Norma ne modifie jamais le dessin automatiquement.

Toute modification proposée doit être :

- visible ;
- réversible ;
- prévisualisée ;
- appliquée par une action explicite de l’utilisateur.

---

## 12. Autres cas d’usage à considérer

### 12.1 Figma / Illustrator / InDesign

- analyser une frame ou une sélection ;
- afficher des guides proportionnels ;
- vérifier marges, grilles et alignements ;
- comparer plusieurs variantes ;
- exporter un rapport de design system.

### 12.2 Web app Norma Studio

- importer une géométrie structurée ;
- éventuellement importer une image via Norma Vision ;
- corriger la détection ;
- analyser plusieurs packs ;
- construire une composition ;
- exporter SVG/JSON/rapport.

### 12.3 API de contrôle qualité

- vérifier des templates en batch ;
- bloquer une CI design si certaines contraintes ne sont pas respectées ;
- générer des rapports de conformité ;
- comparer des versions.

### 12.4 Enseignement

- montrer les divisions et rapports d’une œuvre ;
- permettre à l’étudiant de déplacer une forme ;
- recalculer les measurements en direct ;
- expliquer les systèmes sans produire un jugement esthétique.

### 12.5 Photographie et cadrage

- guides live ;
- comparaison de cadrages ;
- analyse après prise de vue ;
- proposition de crop dérivée et réversible.

### 12.6 Architecture et patrimoine

- analyser des plans structurés ;
- analyser des façades via vision ;
- comparer des systèmes déclarés ;
- conserver provenance et incertitude.

### 12.7 Génération assistée pour développeurs

- produire un layout exact sous forme SVG/CSS/Canvas data ;
- vérifier le layout ;
- intégrer les contraintes dans un pipeline de génération de site ou d’application.

---

## 13. Architecture cible

```text
                         ┌─────────────────────┐
                         │     Norma Codex     │
                         │ packs / ratios /    │
                         │ rule declarations   │
                         └──────────┬──────────┘
                                    │
┌───────────────┐     ┌─────────────▼─────────────┐     ┌─────────────────┐
│ ChatGPT App   │────▶│                           │────▶│ ChatGPT widget  │
├───────────────┤     │        Norma Core         │     ├─────────────────┤
│ Norma Camera  │────▶│ construction/measurement │────▶│ Camera overlay  │
├───────────────┤     │ evaluation/explanation   │     ├─────────────────┤
│ AutoCAD       │────▶│ run/provenance           │────▶│ CAD panel       │
├───────────────┤     │                           │     ├─────────────────┤
│ Web/Figma/etc │────▶│                           │────▶│ SVG/report      │
└───────┬───────┘     └───────────────────────────┘     └─────────────────┘
        │
        ▼
┌─────────────────────┐
│ Adapters            │
│ vision / prompt /   │
│ camera / CAD        │
└─────────────────────┘
```

### 13.1 Modules recommandés

- `@norma/core`
- `@norma/packs`
- `@norma/contracts`
- `@norma/vision-adapter`
- `@norma/chatgpt-app`
- `@norma/camera-adapter`
- `@norma/autocad-adapter`
- `@norma/renderer`

Ces noms sont des propositions, pas des packages actuellement approuvés.

---

## 14. Contrats essentiels

### 14.1 AnalysisRequest

```json
{
  "kind": "norma-analysis-request",
  "geometry": {},
  "packRef": "explicit-pack@version",
  "rules": [],
  "toleranceProfileRef": "explicit-profile@version",
  "operationContext": {},
  "sourceProvenance": {}
}
```

### 14.2 DesignIntent

```json
{
  "kind": "norma-design-intent",
  "canvas": { "width": 1920, "height": 1080 },
  "packRef": "golden-ratio@explicit-version",
  "constraints": [],
  "requiredRegions": [],
  "toleranceProfileRef": "explicit-profile@version"
}
```

### 14.3 AnalysisResult

```json
{
  "kind": "norma-analysis-result",
  "construction": {},
  "measurements": [],
  "evaluation": {},
  "score": {},
  "decision": {},
  "explanation": {},
  "artifacts": [],
  "run": {},
  "packLock": {},
  "operationContext": {}
}
```

Ces exemples servent au cadrage. Les schémas finaux doivent être définis dans des PRs dédiées.

---

## 15. Stratégie ChatGPT

### 15.1 Expérience cible

L’utilisateur reste dans ChatGPT et invoque Norma comme une app/outillage spécialisé.

Outils conceptuels :

- `norma.analyze_image_geometry`
- `norma.evaluate_geometry`
- `norma.construct_composition`
- `norma.compare_compositions`
- `norma.render_overlay`
- `norma.get_pack`
- `norma.list_packs`

Les outils ne doivent pas être exposés tant que leurs contrats, permissions et tests ne sont pas approuvés.

### 15.2 Frontière de responsabilité

ChatGPT :

- conversation ;
- compréhension de la demande ;
- sélection proposée d’un workflow ;
- perception initiale via vision ;
- explication utilisateur ;
- orchestration des outils ;
- génération ou édition d’image.

Norma :

- validation des entrées structurées ;
- résolution explicite du pack ;
- construction géométrique ;
- measurements ;
- evaluation ;
- comparaison ;
- provenance ;
- vérification.

### 15.3 Confirmation obligatoire

Avant une opération significative, la carte ChatGPT doit montrer :

- pack ;
- version ;
- tolérance ;
- dimensions ;
- primitives retenues ;
- confidence ;
- opération prévue.

Cette confirmation peut être allégée pour les analyses read-only, mais les paramètres effectifs doivent rester visibles.

---

## 16. Stratégie de production la plus rapide

### Phase 0 — PR71 : vision et UX freeze

Documentation only :

- vision produit ;
- cas d’usage ;
- architecture ;
- frontières ;
- matrice de capacités ;
- roadmap post-MVP ;
- décisions à confirmer.

### Phase 1 — Vertical slice ChatGPT analyse d’image

Objectif :

```text
image dans ChatGPT
→ extraction structurée simple
→ évaluation Norma
→ réponse + overlay
```

Scope minimal :

- rectangles 2D ;
- segments ;
- axes ;
- un pack explicite ;
- une tolérance explicite ;
- un résultat JSON ;
- un overlay dérivé ;
- images synthétiques de test.

### Phase 2 — Construction conversationnelle

Objectif :

```text
prompt
→ DesignIntent confirmé
→ construction Norma
→ SVG exact
→ vérification
→ rendu visuel optionnel
```

### Phase 3 — Norma Camera prototype

- image fixe d’abord ;
- puis frames ;
- puis tracking ;
- puis optimisation mobile.

### Phase 4 — AutoCAD prototype

- sélection manuelle ;
- extraction exacte ;
- analyse read-only ;
- overlay ;
- propositions non automatiques.

### Phase 5 — Déploiement/publication

- hébergement du MCP/App server ;
- authentification ;
- privacy/security ;
- observabilité ;
- quotas ;
- coûts ;
- evals ;
- soumission de l’app ChatGPT ;
- support et incident response.

---

## 17. Démo de production minimale recommandée

La première démo qui prouve réellement le produit doit permettre :

1. joindre une image synthétique dans ChatGPT ;
2. choisir « nombre d’or » ou un pack réellement disponible ;
3. détecter au moins un rectangle et deux axes ;
4. voir et corriger la détection ;
5. lancer l’analyse Norma ;
6. voir les measurements ;
7. voir l’evaluation ;
8. voir les écarts ;
9. voir confidence et provenance ;
10. voir un overlay ;
11. exporter le JSON et le SVG ;
12. reproduire le même résultat à entrée structurée identique.

Cette démo ne doit pas prétendre faire une analyse universelle d’images.

---

## 18. Tests nécessaires

### 18.1 Core

- déterminisme ;
- pack explicite ;
- tolérance explicite ;
- séparation measurement/evaluation ;
- provenance ;
- artifacts dérivés.

### 18.2 Vision

- précision des coins ;
- précision des lignes ;
- détection de rectangles ;
- perspective ;
- confidence calibrée ;
- images négatives ;
- répétabilité raisonnable ;
- correction utilisateur.

### 18.3 ChatGPT App

- tool selection ;
- arguments structurés ;
- pack non implicite ;
- affichage des paramètres ;
- gestion des erreurs ;
- upload autorisé ;
- permission et confidentialité ;
- réponse sans outil lorsque Norma n’est pas applicable.

### 18.4 Génération

- géométrie avant rendu ;
- contraintes respectées ;
- vérification pré-rendu ;
- vérification post-rendu ;
- dérive entre guide et raster ;
- export du plan source.

### 18.5 Camera

- latence cible à définir ;
- stabilité temporelle ;
- consommation ;
- orientation ;
- changement de lumière ;
- calibration.

### 18.6 CAD

- unités ;
- origine ;
- transformations ;
- sélection ;
- undo/redo ;
- gros dessins ;
- absence de modification silencieuse.

---

## 19. Documentation à créer ou mettre à jour

### 19.1 Documents de vision

- `docs/PRODUCT_VISION.md`
- `docs/USE_CASES.md`
- `docs/UX_FLOWS.md`
- `docs/INTEGRATION_ARCHITECTURE.md`
- `docs/POST_MVP_ROADMAP.md`

### 19.2 Documentation produit

- « Ce qui fonctionne aujourd’hui » ;
- « Ce qui est prévu » ;
- « Ce qui n’est pas implémenté » ;
- quickstart local ;
- premier appel ChatGPT ;
- premier test image ;
- premier test de construction ;
- premier test camera ;
- premier test AutoCAD.

### 19.3 Décision de gouvernance

La documentation doit distinguer :

- les guardrails du MVP Core actuel ;
- la vision post-MVP ;
- les adapters autorisés ;
- les capacités toujours bloquées ;
- les gates avant production.

---

## 20. PR71 recommandée

### Titre

`PR71: product vision, UX flows, and post-MVP integration roadmap`

### Nature

Documentation-only et décisionnelle.

### Objectifs

- figer la vision produit ;
- documenter les quatre parcours principaux ;
- définir l’architecture Core/Adapters ;
- définir la stratégie ChatGPT ;
- choisir l’option hybride pour l’image ;
- formaliser le rôle du Codex ;
- établir la roadmap de production ;
- distinguer clairement current / planned / blocked ;
- autoriser la préparation d’un vertical slice ultérieur sans implémenter ce vertical slice dans PR71.

### Fichiers candidats

- `docs/PRODUCT_VISION.md`
- `docs/USE_CASES.md`
- `docs/UX_FLOWS.md`
- `docs/INTEGRATION_ARCHITECTURE.md`
- `docs/POST_MVP_ROADMAP.md`
- `docs/BUSINESS_READINESS_ROADMAP.md`
- `docs/onboarding/README.md`
- test contractuel documentaire dédié.

### Hors scope PR71

- code vision ;
- intégration OpenAI ;
- app ChatGPT ;
- serveur MCP distant ;
- upload ;
- caméra ;
- plugin AutoCAD ;
- nouveaux packs ;
- déploiement ;
- collecte de données.

---

## 21. Points à valider ou corriger par le product owner

### Positionnement

- [ ] Norma est-elle d’abord un assistant d’analyse, un générateur, ou les deux ?
- [ ] « Norma Codex » est-il le bon nom pour la bibliothèque d’harmonies ?
- [ ] Norma doit-elle expliquer l’histoire/théorie des systèmes ou seulement les appliquer ?

### Analyse d’image

- [ ] Le premier produit doit-il fonctionner uniquement dans ChatGPT ?
- [ ] La correction manuelle des lignes détectées est-elle obligatoire dès V1 ?
- [ ] Les photos en perspective sont-elles supportées dès le premier prototype ?
- [ ] L’analyse porte-t-elle sur toute l’image ou une zone sélectionnée ?

### Génération

- [ ] La sortie primaire doit-elle être SVG, PNG, JSON, ou les trois ?
- [ ] L’utilisateur doit-il toujours confirmer le plan géométrique avant génération ?
- [ ] Le moteur doit-il proposer plusieurs variantes vérifiées ?

### Camera

- [ ] Norma Camera est-elle une app existante ou un projet à créer ?
- [ ] iOS, Android ou les deux ?
- [ ] Analyse on-device obligatoire ou cloud accepté ?
- [ ] Faut-il sauvegarder une session ou seulement analyser en direct ?

### AutoCAD

- [ ] Le plugin doit-il analyser la sélection ou le dessin complet ?
- [ ] Doit-il rester read-only au départ ?
- [ ] Doit-il créer des guides dans le dessin ?
- [ ] Quelles versions d’AutoCAD cibler ?

### Business

- [ ] Produit gratuit, abonnement ou usage professionnel ?
- [ ] Public cible prioritaire : designers, architectes, photographes, artistes ou étudiants ?
- [ ] Quel use case doit être la première démonstration publique ?

---

## 22. Décision proposée

1. **Oui**, les quatre usages décrits appartiennent à la vision cohérente de Norma.
2. **Non**, ils ne doivent pas être implémentés directement dans Norma Core.
3. **Non**, le viewer local actuel ne prouve pas ces usages.
4. **Oui**, la documentation doit être mise à jour pour séparer clairement vision, état actuel et roadmap.
5. **Oui**, le chemin le plus rapide est une app ChatGPT avec perception OpenAI et analyse Norma sur géométrie structurée.
6. **Oui**, Norma Vision propre doit suivre pour Camera et pour une précision contrôlée.
7. **Oui**, AutoCAD est un adapter naturel et probablement le cas d’usage le plus exact techniquement.
8. **Non**, il ne faut pas annoncer l’app en production avant un vertical slice réel, testable et déployé.

