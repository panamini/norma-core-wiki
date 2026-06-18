# 

**Statut : document de brainstorming structuré, à valider avant PR71**  
**Objet : conserver le MVP géométrique actuel, préparer les adapters et documenter les extensions futures sans sur-généraliser trop tôt**

---

## 1. Résumé exécutif

Norma doit être compris comme un système composé de trois couches :

1. **Norma Core actuel** : moteur déterministe de géométrie proportionnelle structurée ;
2. **Adapters et providers** : image, caméra, CAD, Blender, web, musique, QA ;
3. **Packs/Codex** : systèmes proportionnels, règles, tolérances et politiques versionnées.

La promesse centrale :

> Norma transforme une observation ou une intention structurée en mesures, évaluations, explications et artifacts traçables selon un système explicitement sélectionné.

Norma ne doit pas devenir un monolithe qui décode des JPEG, ouvre une caméra, pilote AutoCAD, comprend la musique et applique des normes bâtiment dans le même moteur.

Architecture recommandée :

```text
Interface / logiciel source
→ Provider ou adapter de domaine
→ contrat structuré et versionné
→ moteur Norma approprié
→ measurements / evaluations / decisions / explanations
→ artifacts dérivés
```

---

## 2. État actuel : verdict préliminaire, pas audit final

### Ce qui est prouvé par le track PR67–PR70

- un modèle package-private accepte du JSON structuré explicite ;
- un viewer local read-only transforme ce modèle en affichage ;
- quatre fixtures synthétiques couvrent verification, replay mismatch, artifact stale et prompt unsupported ;
- un readiness test monte le viewer avec un DOM double minimal ;
- les tests locaux rapportés passent ;
- le package reste privé et le viewer n’ajoute pas d’API publique.

### Ce que cela ne prouve pas encore

- que le golden path métier complet du core a été audité de bout en bout ;
- qu’aucun bug numérique ou géométrique majeur n’existe ;
- que CLI, API et MCP sont réellement user-ready ;
- que les tests sont majoritairement comportementaux plutôt que documentaires/guardrails ;
- que le core est production-ready ;
- que l’architecture est déjà prête pour image, camera, CAD, 3D, musique ou normes réglementaires ;
- qu’une CI externe reproduit les validations locales.

### Verdict préliminaire

```text
MVP géométrique actuel : probablement fonctionnel sur les chemins testés.
Absence de bug majeur : non prouvée sans audit dédié.
Production readiness : non.
Readiness pour adapters : conditionnelle à un audit et à des contrats versionnés.
```

---

## 3. Décision majeure : ne pas généraliser trop tôt

Les nouveaux cas d’usage suggèrent deux directions possibles :

### Option 1 — Norma reste un moteur géométrique

```text
@norma/core = géométrie proportionnelle
```

Les domaines musique, réglementation et contrôle qualité utilisent leurs propres moteurs ou services.

### Option 2 — Norma devient une famille construite autour d’un kernel générique

```text
@norma/kernel
├── @norma/geometry
├── @norma/music
├── @norma/standards
└── @norma/quality
```

### Recommandation

Ne pas extraire immédiatement un kernel générique.

Garder `norma-core` comme moteur géométrique tant qu’un deuxième domaine réel n’a pas démontré les abstractions partagées.

Règle :

> Extraire un kernel générique après deux vertical slices de domaines différents, pas avant.

Cela évite de créer une abstraction universelle théorique qui ralentirait la mise en production.

---

## 4. Architecture cible

```text
                               ┌────────────────────────┐
                               │ Norma Registry/Codex   │
                               │ packs versionnés       │
                               └────────────┬───────────┘
                                            │
┌─────────────────────┐   ┌────────────────▼───────────────┐
│ ChatGPT / Web / App │──▶│ Domain Adapter / Provider      │
├─────────────────────┤   │ - perception                   │
│ Norma Camera        │──▶│ - normalization                │
├─────────────────────┤   │ - unités / coordonnées         │
│ AutoCAD / Blender   │──▶│ - confidence / provenance      │
├─────────────────────┤   └────────────────┬───────────────┘
│ Music / QA / CI     │──▶                 │
└─────────────────────┘                    ▼
                               ┌────────────────────────────┐
                               │ Norma Geometry Core actuel │
                               │ ou moteur de domaine futur │
                               └────────────┬───────────────┘
                                            ▼
                               ┌────────────────────────────┐
                               │ Results / Reports / Guides │
                               │ overlays dérivés           │
                               └────────────────────────────┘
```

---

## 5. Analyse d’image : Option A confirmée pour le premier produit

### Oui, un LLM multimodal peut produire une représentation structurée

Le premier prototype peut demander à un modèle vision de produire :

- lignes ;
- segments ;
- rectangles ;
- axes ;
- régions ;
- centres ;
- points de fuite approximatifs ;
- labels sémantiques ;
- confidence déclarée.

### Mais il faut distinguer quatre niveaux

1. **Vectorisation sémantique**  
   Identifier sujet, blocs, hiérarchie et régions.

2. **Approximation géométrique**  
   Proposer lignes, rectangles et coordonnées normalisées.

3. **Vectorisation exacte**  
   Tracer fidèlement des contours et courbes au pixel près.

4. **Reconstruction métrique/3D**  
   Déduire profondeur, échelle et perspective physique.

Le modèle vision est adapté aux niveaux 1–2 pour un prototype. Les niveaux 3–4 nécessitent généralement des algorithmes de vision spécialisés, une correction utilisateur ou des données de calibration.

### Provider recommandé

```text
PerceptionProvider
├── OpenAI Vision Provider — prototype rapide
├── Norma Vision Provider — précision, répétabilité, caméra
├── CAD Provider — géométrie exacte sans perception
├── Scene Provider — Blender/3D
└── Human-corrected Provider — correction manuelle validée
```

### Pipeline V1 image

```text
JPG/PNG
→ OpenAI Vision
→ GeometryObservation candidate
→ validation de schéma
→ correction utilisateur
→ GeometryObservation accepted
→ Norma Core
→ measurements/evaluation
→ overlay dérivé
```

### Règle de vérité

- l’image est l’asset original ;
- la géométrie extraite est une observation dérivée ;
- la géométrie corrigée/acceptée est l’entrée structurée effective ;
- les measurements sont des faits calculés depuis cette entrée ;
- l’overlay reste dérivé.

---

## 6. Produits principaux

### 6.1 Norma Analyze — image dans ChatGPT

Prompt utilisateur :

> Analyse cette image avec Norma et montre les axes, rapports et écarts.

Parcours :

1. image jointe ;
2. choix du pack ;
3. perception ;
4. correction ;
5. analyse ;
6. résultat ;
7. overlay ;
8. export JSON/SVG.

### 6.2 Norma Compose — création assistée

Prompt :

> Crée une composition 16:9 basée sur le nombre d’or.

Pipeline :

```text
prompt
→ DesignIntent structuré
→ confirmation pack/dimensions/tolérance
→ construction exacte
→ vérification
→ SVG/layout source
→ rendu visuel
→ vérification post-rendu
```

### 6.3 Norma Live — Camera

```text
camera
→ calibration
→ perception
→ tracking
→ geometry stabilisée
→ core
→ overlay live
```

### 6.4 Norma CAD

- AutoCAD ;
- Revit à étudier séparément ;
- Rhino ;
- SketchUp ;
- FreeCAD.

Le CAD fournit une géométrie exacte ; l’adapter doit principalement normaliser unités, transformations et sélection.

### 6.5 Norma Scene — Blender et 3D

Usages :

- analyser proportions d’un objet 3D ;
- générer un squelette paramétrique ;
- vérifier bounding boxes et relations ;
- créer guides et empties ;
- comparer variantes ;
- produire mobilier simple : table, chaise, bibliothèque.

Attention : le core actuel est 2D. La 3D doit être un module futur ou un moteur spécialisé, pas une extension silencieuse du MVP.

### 6.6 Norma QA

Contrôle qualité automatisé :

- templates print ;
- layouts web ;
- catalogues e-commerce ;
- design systems ;
- packaging ;
- assets de marque ;
- géométries CAD ;
- séries industrielles ;
- rapports de conformité.

---

## 7. Musique

La musique est pertinente, mais ce n’est pas simplement de la géométrie.

### Données structurées possibles

```text
MusicObservation
- tempo
- meter
- beat grid
- note events
- durations
- pitch classes
- chords
- sections
- motifs
- confidence
```

### Cas d’usage

- proportions temporelles entre sections ;
- rythme et subdivision ;
- rapports de durées ;
- intervalles et systèmes d’accordage ;
- structures A/B/A, cycles et symétries ;
- analyse harmonique ;
- génération contrainte ;
- vérification d’une composition par rapport à un pack déclaré.

### Architecture recommandée

```text
DAW / MIDI / Audio Analysis
→ Music Adapter
→ MusicObservation
→ futur Norma Music Engine
→ Music Evaluation
```

Ne pas forcer les notes et accords dans les objets géométriques du core actuel.

### Adapters futurs

- Ableton Live ;
- Logic Pro ;
- Pro Tools ;
- Cubase ;
- Reaper ;
- MuseScore ;
- MIDI générique.

---

## 8. Graphisme, print et web

### Graphisme

- grilles ;
- marges ;
- alignements ;
- rapports de blocs ;
- hiérarchie visuelle ;
- rythme d’espacement ;
- proportions d’images ;
- zones de texte ;
- variantes vérifiées.

### Typographie

- échelle typographique ;
- rapport heading/body ;
- line-height ;
- longueur de ligne ;
- rythme vertical ;
- espacement ;
- alignement de baseline.

### CSS/Web

- design tokens ;
- spacing scale ;
- modular scale ;
- responsive grids ;
- aspect ratios ;
- container queries ;
- contrôle de régression ;
- lint CI de layout.

### Print

- bleed ;
- safe area ;
- crop ;
- marges ;
- imposition ;
- formats ;
- conformité d’un template.

Adapters : Figma, Illustrator, InDesign, navigateur, Storybook, CI.

---

## 9. Architecture, ingénierie et normes techniques

### Bonne idée, mais nouvelle catégorie de produit

Les règles de bâtiment, mobilier, bateau ou avion ne sont pas seulement des ratios esthétiques. Elles peuvent inclure :

- unités ;
- min/max ;
- plages ;
- charges ;
- matériaux ;
- dépendances ;
- contexte ;
- juridiction ;
- date d’effet ;
- exceptions ;
- tolérances ;
- exigences documentaires.

### Trois niveaux à distinguer

#### A. Proportion et ergonomie

Exemples : hauteur de table, chaise, espacement, reach envelope.

C’est le plus proche de Norma et peut être testé tôt en mode advisory.

#### B. Conformité dimensionnelle

Exemples : passage minimal, garde-corps, épaisseur nominale, distances.

Possible avec packs spécialisés, unités et contextes explicites.

#### C. Sécurité structurelle ou réglementaire critique

Exemples : calcul structurel, aéronautique, naval, incendie.

Cela exige des moteurs spécialisés, validation professionnelle et gouvernance forte. Norma ne doit pas prétendre certifier ces domaines sur la seule base du core géométrique.

### Produit proposé

```text
Norma Standards
```

Mode initial :

- read-only ;
- advisory ;
- citations des sources ;
- version/juridiction ;
- aucune certification automatique ;
- signature humaine requise pour décision critique.

---

## 10. Archéologie, patrimoine et sciences

Cas d’usage :

- analyse des proportions d’un artefact ;
- comparaison de typologies ;
- façades et plans historiques ;
- poteries, monnaies, sculptures ;
- reconstruction hypothétique ;
- photogrammétrie ;
- provenance de chaque mesure ;
- niveaux d’incertitude.

Norma peut être utile ici parce que la séparation observation/measurement/evaluation est particulièrement importante.

---

## 11. Packaging et industrie

### Packaging graphique

- grille ;
- placement logo ;
- zones réglementaires ;
- marges ;
- lisibilité ;
- cohérence de gamme.

### Packaging structurel

- dimensions ;
- ratios ;
- tolérances ;
- volume ;
- emboîtement ;
- découpe ;
- contrôle CAD.

### Fabrication

- comparaison nominal/mesuré ;
- contrôle de tolérance ;
- inspection par vision ;
- rapport batch ;
- traçabilité ;
- calibration appareil.

---

## 12. Packs professionnels et privés d’entreprise

L’idée est forte et cohérente avec la modularité, à condition d’imposer une gouvernance stricte.

### Catégories

1. **Public Harmony Packs**  
   Systèmes proportionnels publics.

2. **Professional Domain Packs**  
   Typographie, architecture, mobilier, packaging, QA.

3. **Enterprise Private Packs**  
   Standards internes, design systems, tolérances, règles propriétaires.

4. **Regulatory Reference Packs**  
   Règles versionnées par juridiction et date, sous réserve de licence.

5. **Calibration Packs**  
   Tolérances de machine, appareil ou processus.

### Contraintes obligatoires

- namespace ;
- propriétaire ;
- version immuable ;
- effective date ;
- status draft/approved/deprecated ;
- sources/références ;
- unités ;
- juridiction ;
- rule types supportés ;
- tests contractuels ;
- signature ou checksum ;
- access control ;
- audit log ;
- PackLock dans chaque run ;
- aucune exécution de code arbitraire ;
- aucune règle créée silencieusement par un agent.

### UX entreprise

- importer un pack ;
- valider ;
- voir les erreurs ;
- exécuter une suite de tests ;
- publier en interne ;
- déprécier ;
- comparer versions ;
- revenir à une version ;
- contrôler qui peut créer/approuver/utiliser.

### Marketplace

Possible à long terme, mais seulement après :

- format stable ;
- signature ;
- sécurité ;
- licensing ;
- réputation ;
- validation automatique ;
- gouvernance des mises à jour.

---

## 13. Codex vs Standards Registry

Le terme `Norma Codex` est adapté aux systèmes d’harmonie et de proportion.

Pour éviter la confusion, proposer :

```text
Norma Registry
├── Codex Packs       — proportion/harmonie/composition
├── Standards Packs   — règles techniques/compliance
├── Enterprise Packs  — politiques privées
└── Calibration Packs — tolérances de mesure/processus
```

Tous peuvent partager versioning et provenance, mais pas nécessairement les mêmes rule types ou le même moteur.

---

## 14. Modes d’évaluation

Il faut séparer trois modes produits.

### Descriptive

> Qu’est-ce qui est présent et mesurable ?

### Comparative

> Quelle variante est plus proche du système sélectionné ?

### Compliance

> Quelles règles explicites sont satisfaites, violées ou non évaluables ?

### Generative guidance

> Quelles modifications explicites réduisent l’écart ?

Le mode generative guidance ne doit jamais masquer le système, les contraintes ou les hypothèses.

---

## 15. Score, confidence et conformité

Ne jamais fusionner :

- confidence de perception ;
- score de proximité ;
- statut de conformité ;
- qualité esthétique ;
- criticité métier.

Exemple :

```text
Perception confidence: 0.72
Proportional deviation: 1.8%
Compliance status: warning
Criticality: advisory
```

---

## 16. Niveaux de risque produit

### Niveau 1 — Créatif/advisory

- graphisme ;
- photographie ;
- enseignement ;
- composition musicale ;
- mobilier conceptuel.

### Niveau 2 — Professionnel non critique

- design systems ;
- packaging ;
- QA de templates ;
- architecture conceptuelle ;
- fabrication non critique.

### Niveau 3 — Réglementaire/sécurité critique

- bâtiment réglementaire ;
- structure ;
- médical ;
- aéronautique ;
- naval ;
- sécurité industrielle.

Le niveau 3 exige des moteurs validés, des sources officielles, des professionnels responsables et des limites juridiques explicites.

---

## 17. Business model potentiel

### Free / Community

- core local ;
- packs de base ;
- viewer ;
- JSON/SVG ;
- quotas limités éventuels.

### Pro

- ChatGPT app ;
- analyse image ;
- packs professionnels ;
- comparaison ;
- export ;
- historique.

### Studio/Team

- packs partagés ;
- design systems ;
- QA batch ;
- collaboration ;
- CI ;
- permissions.

### Enterprise

- private packs ;
- SSO ;
- audit ;
- on-prem/VPC éventuel ;
- connectors CAD ;
- gouvernance ;
- support ;
- custom evals.

### Domain add-ons

- Norma Music ;
- Norma CAD ;
- Norma Camera ;
- Norma Standards ;
- Norma QA.

---

## 18. Roadmap recommandée

### Gate A — Audit du MVP actuel

Avant d’élargir l’architecture :

- audit métier ;
- edge cases ;
- golden path ;
- tests comportementaux ;
- CLI/MCP/API status ;
- performance ;
- CI ;
- adapter readiness.

### PR71 — Vision et architecture freeze

Après audit :

- current state ;
- product vision ;
- use cases ;
- provider architecture ;
- registry/pack governance ;
- risk tiers ;
- roadmap ;
- first vertical slice.

### Vertical Slice 1 — ChatGPT Analyze

Scope minimal :

- image synthétique ;
- rectangles/segments/axes ;
- OpenAI Vision provider ;
- structured output ;
- correction minimale ;
- pack existant explicite ;
- analyse core ;
- overlay ;
- evals.

### Vertical Slice 2 — ChatGPT Compose

- DesignIntent ;
- confirmation ;
- construction ;
- SVG ;
- vérification ;
- rendu optionnel.

### Vertical Slice 3 — Norma Vision

- dataset synthétique annoté ;
- lignes/rectangles ;
- calibration ;
- comparaison à OpenAI Vision.

### Vertical Slice 4 — CAD read-only

- une sélection ;
- unités ;
- extraction ;
- analyse ;
- panel ;
- aucune modification automatique.

### Vertical Slice 5 — Enterprise Packs

- format privé ;
- validation ;
- version ;
- access control ;
- tests ;
- PackLock.

### Domain experiments ultérieurs

- Blender/3D ;
- Music ;
- packaging QA ;
- archaeology ;
- engineering standards advisory.

---

## 19. Premier produit testable recommandé

### Norma Analyze for ChatGPT

User story :

> Je joins une image simple et je demande à Norma d’identifier un rectangle principal, deux axes et leur proximité avec un pack proportionnel explicite.

Critères :

- image synthétique ;
- extraction structurée ;
- affichage des coordonnées ;
- correction ;
- validation ;
- mesure ;
- évaluation ;
- confidence ;
- provenance ;
- overlay ;
- reproductibilité après freeze de la géométrie.

Cette démo est plus utile commercialement que le viewer JSON seul, tout en restant assez limitée pour être testable.

---

## 20. Questions à valider avant PR71

### Produit

- Norma est-il présenté comme une plateforme, un moteur ou une suite ?
- `Norma Codex` reste-t-il le nom public pour les harmonies ?
- `Norma Registry` est-il acceptable pour l’ensemble des packs ?

### Première cible

- ChatGPT Analyze est-il le premier vertical slice ?
- Le premier public est-il designer, architecte ou photographe ?
- La correction manuelle est-elle obligatoire ?

### Packs

- Les entreprises peuvent-elles créer leurs packs dès la première version Pro ?
- Qui peut approuver un private pack ?
- Faut-il permettre seulement des rule types déjà supportés ? Recommandation : oui.

### Données

- Les images restent-elles temporaires ?
- Les runs sont-ils sauvegardés ?
- Un mode local/privacy-first est-il prioritaire ?

### Domaines

- Music est-il une exploration ou une roadmap produit ?
- Blender/3D arrive-t-il avant ou après CAD 2D ?
- Standards techniques restent-ils advisory au départ ? Recommandation : oui.

---

## 21. Décisions recommandées

1. Auditer le core avant PR71.
2. Conserver le core actuel comme moteur géométrique.
3. Choisir OpenAI Vision comme provider de perception du premier prototype.
4. Toujours valider/corriger la géométrie avant analyse core.
5. Construire le produit autour de providers et adapters.
6. Introduire `Norma Registry` comme couche commune de gouvernance des packs.
7. Garder `Norma Codex` pour les harmonies/proportions.
8. Autoriser à terme des private packs d’entreprise, déclaratifs et versionnés.
9. Séparer descriptive/comparative/compliance/generative guidance.
10. Ne généraliser vers un kernel multi-domaine qu’après un deuxième domaine réel.
11. Mettre ChatGPT Analyze en premier vertical slice public.
12. Garder camera, CAD, Blender, music, standards et QA comme modules ordonnés, pas comme scope d’un seul PR.
