# Norma — Bible complète des ratios et règles harmoniques

Document cible :

```txt
docs/harmonic-ratio-bible.md
```

Type de PR recommandé :

```txt
docs: add harmonic ratio bible
```

Scope de cette première PR :

```txt
Documentation only.
No runtime behavior change.
No preset modification.
No solver modification.
No scoring modification.
```

---

# 0. Objectif du document

Ce document est la Bible de travail des ratios et règles harmoniques utilisés, observés ou pressentis pour Norma.

Il ne faut pas lire cette Bible comme une simple liste de nombres.

Il faut la lire comme une taxonomie de règles.

Norma ne doit jamais mélanger :

- les ratios de format global ;
    
- les ratios de surface ;
    
- les positions de points ;
    
- les angles ;
    
- les règles d’intersection ;
    
- les règles de construction ;
    
- les règles de scoring ;
    
- les ratios observés dans des objets externes ;
    
- les collisions numériques entre constantes proches.
    

Le rôle du développeur junior est de transformer cette Bible en documentation claire, puis plus tard, seulement après validation produit et architecture, en données structurées ou en ratio packs.

---

# 1. Résumé produit

Norma est un système de géométrie proportionnelle.

Dans l’app actuelle `panamini/norma`, Norma travaille principalement sur :

- un carré canonique `100×100` ;
    
- trois surfaces `A`, `B`, `C` ;
    
- des polygones réels ;
    
- des ratios cibles `A:B:C` ;
    
- des familles de construction géométrique ;
    
- des positions harmoniques ;
    
- des angles harmoniques ;
    
- des règles d’intersection ;
    
- des règles de snapping ;
    
- des règles de scoring.
    

Le moteur compare les aires réelles des polygones à des pourcentages cibles dérivés du ratio `A:B:C`.

Exemple :

```txt
ratio cible = 3:4:5
somme = 12

A = 3 / 12 = 25%
B = 4 / 12 = 33.333%
C = 5 / 12 = 41.667%
```

Norma ne doit pas confondre cette logique de surface avec les formats largeur/hauteur Poussin.

---

# 2. Scope exact du travail

## 2.1 Ce qu’il faut faire

Créer une Bible claire des ratios et règles harmoniques de Norma.

Cette Bible doit :

1. lister toutes les familles de ratios connues ;
    
2. distinguer les ratios déjà codés dans l’app actuelle ;
    
3. distinguer les ratios seulement observés dans les captures ;
    
4. distinguer les ratios de format, surface, position, angle, intersection, construction et scoring ;
    
5. expliquer quelles règles sont sûres ;
    
6. expliquer quelles règles sont candidates ;
    
7. expliquer quelles règles sont ambiguës ;
    
8. éviter de forcer des correspondances douteuses ;
    
9. préserver les collisions numériques ;
    
10. préserver les suffixes de mesure comme `_r` et `_d` ;
    
11. préparer une future structuration en ratio packs.
    

## 2.2 Ce qu’il ne faut pas faire

Ne pas injecter tous ces ratios directement dans l’app.

Ne pas remplacer les presets existants.

Ne pas modifier le solver.

Ne pas modifier le scoring.

Ne pas modifier les fichiers runtime.

Ne pas mélanger les formats Poussin avec les surfaces `A:B:C`.

Ne pas mélanger les ratios de vaisseau avec les presets de surface Norma.

Ne pas transformer une observation externe en règle moteur sans validation.

Ne pas forcer un match mathématique douteux.

---

# 3. Principe central : les niveaux de règles

Norma doit classer chaque ratio ou règle selon son niveau.

|Niveau|Ce que ça contrôle|Exemple|Statut général|
|---|---|---|---|
|Format / cadre|Ratio largeur/hauteur global|Poussin : `1.236`, `1.618`, `1.707`|à documenter|
|Surface|Répartition `A:B:C`|`3:4:5`, `1:φ:φ²`|déjà codé en partie|
|Position|Placement d’une coupe ou d’un point|`1/3`, `1/2`, `1/φ`|déjà codé|
|Angle|Orientation ou angle de croisement|`30°`, `36°`, `45°`, `60°`, `90°`|déjà codé|
|Intersection|Relation entre point, angle et segments|Golden cross, Musical 60°|déjà codé|
|Construction|Famille géométrique|`parallel`, `crossed`, `radiant`|déjà codé|
|Snapping|Aide UI ou manuelle|soft snap, hard snap|déjà codé|
|Scoring|Classement des candidats|exactness, alignment, directionality|déjà codé|
|Observation externe|Ratios lus dans des captures|`(√6/2)^n`, `πφ`, `φ³`|à documenter|
|Collision|Constantes proches|`(√6/2)^8 ≈ πφ`|à gérer explicitement|

Règle importante :

> Un même nombre peut apparaître dans plusieurs niveaux, mais il ne signifie pas la même chose partout.

Exemple :

- `1.618` peut être un format largeur/hauteur ;
    
- `φ` peut être un ratio de surface ;
    
- `1/φ` peut être une position ;
    
- `φ³` peut être un ratio observé entre deux features d’objet ;
    
- `90°` est un angle, pas une surface.
    

Le contexte est obligatoire.

---

# 4. Statuts, confiance et décision moteur

## 4.1 Statuts source

Chaque ratio doit avoir un statut source.

|Statut|Signification|
|---|---|
|`coded_currently`|Déjà présent dans l’app Norma actuelle|
|`observed_external`|Vu dans une capture ou analyse externe|
|`candidate_to_add`|Bon candidat pour un futur ratio pack|
|`derived_known`|Dérivé d’une constante connue|
|`ambiguous`|Plusieurs lectures possibles|
|`speculative`|Match faible ou à vérifier|
|`do_not_use_yet`|Ne pas utiliser dans le moteur tant que non validé|

## 4.2 Niveaux de confiance

La Bible doit aussi séparer le statut source du niveau de confiance.

|Confiance|Critère|
|---|---|
|`exact`|Égalité mathématique exacte|
|`strong`|Écart très faible, formule claire|
|`approximate`|Plausible mais pas parfait|
|`speculative`|Intuition seulement|
|`unknown`|Pas de match connu|

## 4.3 Règle junior

Si tu n’es pas sûr, marque :

```txt
ambiguous
```

ou :

```txt
speculative
```

Ne force jamais un ratio pour faire joli.

Une entrée `speculative` ne doit jamais devenir une contrainte automatique du moteur.

---

# 5. Constantes fondamentales

Cette section liste les constantes principales de la Bible.

|Constante|Valeur approx.|Famille|Usage principal|
|---|--:|---|---|
|`1`|`1.000`|identité|carré, égalité, pivot|
|`1/4`|`0.250`|division simple|position|
|`1/3`|`0.333`|tertian|position, intersection|
|`1/2`|`0.500`|midpoint|position, segment|
|`2/3`|`0.667`|tertian étendu|position|
|`3/4`|`0.750`|quart complémentaire|position|
|`φ`|`1.618`|doré|surface, format, croissance|
|`1/φ`|`0.618`|doré|position, format vertical|
|`φ⁻²`|`0.382`|doré complémentaire|position|
|`φ²`|`2.618`|doré|surface, expansion|
|`φ³`|`4.236`|doré|observation externe|
|`φ⁴`|`6.854`|doré|observation externe|
|`φ⁵`|`11.090`|doré|observation externe|
|`√2`|`1.414`|racine 2|format, surface|
|`1/√2`|`0.707`|racine 2|position, format|
|`√3`|`1.732`|racine 3|triangle, angle|
|`1/√3`|`0.577`|racine 3|position|
|`√3/2`|`0.866`|triangle équilatéral|format vertical|
|`δ = 1 + √2`|`2.414`|argent|surface|
|`1/δ`|`0.414`|argent|position|
|`α = √6/2`|`1.225`|semi-harmonique|famille observée|
|`π`|`3.142`|circulaire|rayon, diamètre, courbe|
|`2π`|`6.283`|circulaire|circonférence/rayon|
|`π/φ`|`1.942`|cercle-or|observé|
|`π/φ²`|`1.200`|cercle-or|observé|
|`πφ`|`5.083`|cercle-or|observé|
|`πφ²`|`8.225`|cercle-or|observé|

---

# 6. Famille Poussin : formats largeur/hauteur

## 6.1 Définition

Le ratio Poussin est un ratio de format global.

Formule :

```txt
r = largeur / hauteur
```

Ce n’est pas un ratio de surface interne.

Ce n’est pas un ratio `A:B:C`.

Il décrit le cadre complet de l’image.

## 6.2 Liste complète Poussin relevée

Cette liste doit être conservée exactement.

```txt
0.353
0.618
0.707
0.764
0.796
0.809
0.828
1
1.236
1.309
1.325
1.353
1.382
1.414
1.5
1.618
1.707
2
```

## 6.3 Table d’interprétation Poussin

|Valeur observée|Lecture harmonique possible|Famille|Statut source|Confiance|Décision|
|--:|---|---|---|---|---|
|`0.353`|`≈ 1 / (2√2) = 0.3536`|racine 2 / demi-diagonale|`observed_external`|`strong`|garder|
|`0.618`|`≈ 1/φ = 0.6180`|doré|`observed_external`|`strong`|garder|
|`0.707`|`≈ 1/√2 = 0.7071`|racine 2|`observed_external`|`strong`|garder|
|`0.764`|`≈ 2/φ² = 0.7639`|doré carré|`observed_external`|`strong`|garder|
|`0.796`|`proche de √(2/π) = 0.7979`|possible hybride racine / cercle|`observed_external`|`approximate`|à vérifier|
|`0.809`|`≈ φ/2 = 0.8090`|doré demi|`observed_external`|`strong`|garder|
|`0.828`|`≈ 2/(1+√2) = 0.8284`|argent / racine 2|`observed_external`|`strong`|garder|
|`1.000`|`1`|identité / carré|`observed_external`|`exact`|garder|
|`1.236`|`≈ 2/φ = 1.2361`|doré|`observed_external`|`strong`|garder|
|`1.309`|`≈ φ²/2 = 1.3090`|doré carré demi|`observed_external`|`strong`|garder|
|`1.325`|pas de match canonique évident|observé non classé|`observed_external`|`unknown`|ne pas forcer|
|`1.353`|`≈ 1 + 1/(2√2) = 1.3536`|racine 2 composée|`observed_external`|`strong`|garder|
|`1.382`|`≈ 1 + φ⁻² = 1.3820`|doré composé|`observed_external`|`strong`|garder|
|`1.414`|`≈ √2 = 1.4142`|racine 2|`observed_external`|`strong`|garder|
|`1.500`|`3/2`|harmonique musical / quinte juste|`observed_external`|`exact`|garder|
|`1.618`|`φ`|nombre d’or|`observed_external`|`strong`|garder|
|`1.707`|`≈ 1 + 1/√2 = 1.7071`|racine 2 composée|`observed_external`|`strong`|garder|
|`2.000`|`2`|double / octave / `2:1`|`observed_external`|`exact`|garder|

## 6.4 Règles statistiques Poussin

|Règle|Valeur|
|---|--:|
|Formats verticaux|`r < 1`|
|Format carré / pivot|`r = 1`|
|Formats horizontaux|`r > 1`|
|Répartition observée|`72% horizontaux / 28% verticaux`|
|Zone verticale dense|`0.70 ≤ r ≤ 0.87`|
|Zone horizontale dense|`1.236 ≤ r ≤ 1.707`|
|Densité verticale|`80% des verticaux entre 0.70 et 0.87`|
|Densité horizontale|`86% des horizontaux entre 1.236 et 1.707`|

La liste contient 7 formats verticaux, 1 format carré/pivot et 10 formats horizontaux.
Ce comptage est distinct de la statistique de corpus 72% horizontaux / 28% verticaux.
## 6.5 Paires réciproques importantes

|Vertical|Horizontal associé|Relation|
|--:|--:|---|
|`0.618`|`1.618`|`1/φ ↔ φ`|
|`0.707`|`1.414`|`1/√2 ↔ √2`|
|`0.764`|`1.309`|`2/φ² ↔ φ²/2`|
|`0.809`|`1.236`|`φ/2 ↔ 2/φ`|

Règle Norma :

> Un format peut être lu en ratio direct largeur/hauteur, mais aussi comme paire verticale/horizontale. Norma doit conserver les deux lectures : orientation réelle et famille harmonique associée.

## 6.6 Règle stricte Poussin

Poussin doit être classé comme :

```txt
aspectRatioRules
```

et non comme :

```txt
surfaceRatioPresets
```

Pourquoi ?

Parce que Poussin décrit le cadre complet de l’image.

Les presets `A:B:C` décrivent des surfaces internes.

---

# 7. Ratios de surfaces A:B:C actuellement présents dans Norma

## 7.1 Définition

Les ratios `A:B:C` contrôlent la répartition de trois surfaces.

Ils sont déjà présents dans l’app actuelle.

Ils ne doivent pas être remplacés dans cette PR.

Ils doivent être documentés comme :

```txt
coded_currently
```

Important :

> Tous ces presets ne sont pas “harmoniques classiques” au sens musical strict. Certains sont arithmétiques, expérimentaux, géométriques ou compositionnels.

## 7.2 Familles existantes

|Famille|Ratios|Type de logique|Statut|
|---|---|---|---|
|équilibrés|`1:1:1`, `2:3:3`, `3:4:4`, `4:5:6`|équilibre / légère asymétrie|`coded_currently`|
|arithmétiques|`1:2:3`, `2:3:4`, `3:4:5`, `4:5:6`|progression linéaire|`coded_currently`|
|fibonacci|`2:3:5`, `3:5:8`, `5:8:13`, `8:13:21`|croissance naturelle / rythme Fibonacci|`coded_currently`|
|doré|`1:φ:φ²`, `φ:φ²:φ³`, `1:φ²:φ³`|puissances du nombre d’or|`coded_currently`|
|doré carré|`1:φ²:φ⁴`, `φ²:φ³:φ⁴`, `1:(1+φ):(1+φ)²`|amplification dorée|`coded_currently`|
|racine 2|`1:√2:2`, `1:2:2√2`, `√2:2:2√2`|progression racine-deux / architecture|`coded_currently`|
|argent|`1:δ:δ²`, `δ:δ²:δ³`, `1:2:δ²`|nombre d’argent, `δ = 1 + √2`|`coded_currently`|
|géométriques|`1:2:4`, `1:3:9`, `2:4:8`, `3:6:9`|multiplication / puissance|`coded_currently`|
|musicales|`2:3:4`, `3:4:5`, `4:5:6`, `8:9:12`|intervalles harmoniques / consonance|`coded_currently`|
|expérimentales|`1:4:7`, `2:5:11`, `5:7:12`, `7:11:18`|tension volontaire / art direction|`coded_currently`|

## 7.3 Règle de conversion surface

Pour un ratio `A:B:C` :

```txt
A% = A / (A + B + C) × 100
B% = B / (A + B + C) × 100
C% = C / (A + B + C) × 100
```

Le moteur doit comparer les aires réelles des polygones à ces pourcentages cibles.

## 7.4 Règle de cadre actuel

Dans l’app actuelle, le cadre de travail est :

```txt
100 × 100
```

L’aire totale de référence est donc :

```txt
10 000
```

Mais la Bible doit rester conceptuelle.

Ne pas coder de dépendance rigide au `100×100` si Norma Core évolue vers des espaces normalisés ou arbitraires.

---

# 8. Familles de construction géométrique

## 8.1 Vue d’ensemble

|Famille|Règle|Paramètres|Exactitude|
|---|---|---|---|
|`parallel`|Deux coupes parallèles divisent le carré en trois bandes|`orientation`, `cuts[0]`, `cuts[1]`|exact en continu|
|`perpendicular`|Une coupe principale crée un bloc, puis une coupe secondaire divise une partie|`orientation`, `side`, `main`, `secondary`|exact analytique|
|`crossed`|Une coupe verticale et une coupe horizontale se croisent ; un côté est fusionné|`merge`, `x`, `y`|exact analytique|
|`harmonic crossed`|Deux lignes obliques se croisent à un point intérieur, puis deux régions sont fusionnées|`intersection`, `primaryAngle`, `crossingAngle`, `merge`|harmonique par contrainte, évalué par aire|
|`v`|Deux segments partent d’un coin vers deux points du bord|`originCorner`, `anchor1`, `anchor2`|échantillonné, pas garanti exact|
|`radiant`|Un point d’origine sur le bord envoie deux segments vers deux ancres|`origin`, `anchor1`, `anchor2`|échantillonné, pas garanti exact|

## 8.2 Notes d’implémentation à documenter

Pour `parallel` :

```txt
les coupes sont les pourcentages cumulés du ratio
```

Pour `perpendicular` :

```txt
main et secondary sont calculés depuis les slots de surface
selon l’orientation et le côté choisi
```

Pour `crossed` :

```txt
x et y dépendent du côté fusionné :
top
bottom
left
right
```

Pour `harmonic crossed` :

```txt
le système coupe le carré avec deux lignes
calcule les segments clippés au carré
divise le carré en quatre polygones
fusionne deux régions adjacentes
revient à trois surfaces A/B/C
```

---

# 9. Positions harmoniques actuellement présentes dans Norma

## 9.1 Définition

Ces positions servent à placer :

- une coupe ;
    
- un point d’intersection ;
    
- une ancre sur le périmètre ;
    
- un point sur un segment.
    

Elles doivent être classées comme :

```txt
positionTokens
```

## 9.2 Liste des tokens

|Token|Valeur exacte|Valeur approx.|Famille|Statut|
|---|--:|--:|---|---|
|`quarter`|`1/4`|`0.250`|quart|`coded_currently`|
|`third`|`1/3`|`0.333`|tiers|`coded_currently`|
|`phi-left`|`φ⁻²`|`0.382`|doré complémentaire|`coded_currently`|
|`silver-left`|`δ⁻¹`|`0.414`|argent|`coded_currently`|
|`half`|`1/2`|`0.500`|milieu|`coded_currently`|
|`sqrt3`|`1/√3`|`0.577`|racine 3|`coded_currently`|
|`phi`|`1/φ`|`0.618`|doré|`coded_currently`|
|`two-thirds`|`2/3`|`0.667`|deux tiers|`coded_currently`|
|`sqrt2`|`1/√2`|`0.707`|racine 2|`coded_currently`|
|`three-quarters`|`3/4`|`0.750`|trois quarts|`coded_currently`|

## 9.3 Usage cartésien

Pour les positions `x/y` :

```txt
x = token × 100
y = token × 100
```

Exemple :

```txt
1/φ ≈ 0.618
x = 61.8%
```

## 9.4 Usage sur le bord du carré

Pour les familles `V` et `Radiant`, le token est utilisé comme paramètre de périmètre.

Le bord du carré est parcouru comme ceci :

1. haut ;
    
2. droite ;
    
3. bas ;
    
4. gauche.
    

Le token `0.25` ne veut donc pas seulement dire :

```txt
25% d’un axe
```

Il peut aussi vouloir dire :

```txt
point situé à 25% du périmètre normalisé
```

Règle :

> Le même token peut avoir un usage cartésien ou un usage périmétrique. Il faut conserver le contexte.

---

# 10. Angles harmoniques

## 10.1 Angles de croisement

Norma contient actuellement :

```txt
30°
36°
45°
54°
60°
72°
73°
90°
```

## 10.2 Angles de rotation rapide dans l’UI

```txt
0°
30°
36°
45°
60°
73°
90°
```

## 10.3 Angles de scoring directionnel

Le scoring favorise les segments proches de :

```txt
0°
30°
45°
60°
90°
120°
135°
150°
```

## 10.4 Lecture harmonique possible

|Angle|Lecture possible|
|--:|---|
|`30°`|triangle `30-60-90`|
|`36°`|pentagone / doré|
|`45°`|diagonale / racine 2|
|`54°`|complément de `36°`|
|`60°`|triangle équilatéral / consonance|
|`72°`|pentagone / doré|
|`73°`|angle quasi-doré ou angle empirique UI|
|`90°`|orthogonalité|

## 10.5 Rotation snap

La rotation de vue peut snapper vers :

- les angles harmoniques ;
    
- leurs compléments ;
    
- leurs négatifs ;
    
- `0°` ;
    
- `180°`.
    

Règle importante :

> Les angles ne sont pas des ratios de surface. Ce sont des contraintes d’orientation.

---

# 11. Règles d’intersection harmonique

## 11.1 Définition

Les règles d’intersection combinent :

- un point ;
    
- un ou deux segments ;
    
- un angle ;
    
- une règle de merge ;
    
- parfois une recherche échantillonnée.
    

Elles doivent être classées comme :

```txt
intersectionPresets
```

## 11.2 Mode side-relative

Le point d’intersection est fixé par rapport aux côtés du carré.

Exemple :

```txt
x = 1/φ
y = φ⁻²
angle = 90°
```

Ce mode est déterministe.

Paramètres typiques :

```txt
xTokenId
yTokenId
angleDeg
merge
```

## 11.3 Mode segment-relative

Le point d’intersection est contraint par sa position le long de deux segments.

Exemple :

```txt
segment1 = 1/φ
segment2 = 1/2
angle = 36°
```

Ce mode n’est pas complètement déterminé par la règle seule.

Il nécessite une recherche échantillonnée.

Paramètres typiques :

```txt
segment1TokenId
segment2TokenId
angleDeg
merge
```

## 11.4 Merge side

Après deux lignes croisées, le carré est divisé en quatre régions.

Norma fusionne deux régions adjacentes pour revenir à trois surfaces `A/B/C`.

Options :

```txt
top
bottom
left
right
```

Règle importante :

> Le merge est une règle géométrique. Il ne doit pas être confondu avec un ratio.

## 11.5 Type `HarmonicCrossedConfig`

Le type contient exactement ou presque les champs suivants, à vérifier dans `src/types.ts` :

```txt
intersection
primaryAngle
crossingAngle
presetId
constraintMode
normalizedMatch
```

Note :

```txt
normalizedMatch
```

est utilisé pour les positions segmentaires quand le mode est `segment-relative`.

## 11.6 Presets d’intersection harmonique

|Preset|Mode|Position|Angle|Merge|Statut|
|---|---|---|--:|---|---|
|`Tertian right angle`|`side-relative`|`x = 1/3`, `y = 1/3`|`90°`|`top`|`coded_currently`|
|`Golden cross`|`side-relative`|`x = 1/φ`, `y = φ⁻²`|`90°`|`right`|`coded_currently`|
|`Root-two tilt`|`side-relative`|`x = 1/√2`, `y = 1/2`|`45°`|`left`|`coded_currently`|
|`Pentagonal 36°`|`segment-relative`|`segment1 = 1/φ`, `segment2 = 1/2`|`36°`|`top`|`coded_currently`|
|`Musical 60°`|`segment-relative`|`segment1 = 1/3`, `segment2 = 1/2`|`60°`|`bottom`|`coded_currently`|

Ces cinq presets sont définis dans l’app actuelle comme presets harmoniques.

---

# 12. Recherche automatique harmonique

## 12.1 Définition

La recherche automatique harmonique teste des candidats selon une densité.

Plus la densité est élevée, plus le système teste :

- de positions ;
    
- d’angles ;
    
- de combinaisons ;
    
- de matches segmentaires.
    

Cette logique existe dans l’app actuelle et doit être documentée, mais pas modifiée dans cette PR.

## 12.2 Densités

| Densité | Valeurs testées                            | Tolérance | Angles primaires                                              |
| ------: | ------------------------------------------ | --------: | ------------------------------------------------------------- |
|     `1` | `1/3`, `1/2`, `2/3`                        |    `0.08` | `0`, `30`, `45`, `60`, `90`, `135`                            |
|     `2` | `1/4`, `1/3`, `1/2`, `1/φ`, `2/3`, `3/4`   |   `0.055` | ajoute `15`, `36`, `72`, `120`, `150`                         |
|     `3` | tous les tokens harmoniques                |   `0.038` | ajoute `12`, `24`, `54`, `84`, `108`, `165`, etc.             |
|     `4` | tous les tokens harmoniques + `0.2`, `0.8` |   `0.026` | 24 angles par pas de 7.5° : 0°, 7.5°, 15°, 22.5°, ..., 172.5° |

## 12.3 Règle segment-relative

En mode `segment-relative`, le système :

1. teste des positions candidates ;
    
2. construit les lignes ;
    
3. calcule les positions normalisées sur les deux segments ;
    
4. compare l’erreur à la tolérance ;
    
5. garde seulement les candidats sous la tolérance.
    

Règle :

> Cette recherche est échantillonnée. Elle ne doit pas être décrite comme analytique exacte.

---

# 13. Règles de snapping et magnétisme

## 13.1 Définition

Norma possède une assistance manuelle.

Elle peut aider l’utilisateur à placer des éléments près de positions harmoniques.

Cette assistance n’est pas une vérité du core.

Elle doit être classée séparément de la géométrie pure.

## 13.2 Deux types de snap

|Type|Usage|
|---|---|
|`Cartesian snap`|positions `x/y` pour coupes et intersections|
|`Boundary snap`|points sur le périmètre pour `V` et `Radiant`|

## 13.3 Cibles

Les cibles sont les mêmes tokens harmoniques :

```txt
1/4
1/3
φ⁻²
δ⁻¹
1/2
1/√3
1/φ
2/3
1/√2
3/4
```

## 13.4 Seuils

|Règle|Où elle agit|Paramètres|
|---|---|---|
|`Harmonic cartesian snap`|positions `x/y` des coupes et intersections|tokens harmoniques × `100`|
|`Harmonic boundary snap`|points sur le périmètre pour `V` et `Radiant`|tokens harmoniques normalisés|
|`Soft snap`|attraction douce avant verrouillage|`4.8` unités cartésiennes ou `0.06` en périmètre|
|`Hard snap`|verrouillage exact si très proche|`1.1` unités cartésiennes ou `0.016` en périmètre|
|`Guides sans magnet`|les guides s’allument même sans snap dur|feedback visuel uniquement|

## 13.5 Règle junior

Documenter ces valeurs.

Ne pas les modifier.

Ne pas faire de refactor du snapping dans cette PR.

Ne pas transformer cette aide UI en vérité du core.

---

# 14. Scoring actuellement présent dans Norma

## 14.1 Définition

Le scoring sert à classer les candidats.

Il ne définit pas des règles géométriques dures.

C’est une heuristique.

## 14.2 Scores principaux

|Score|Description|
|---|---|
|`closeness`|proximité du ratio de surface demandé|
|`balance`|équilibre des masses|
|`simpleFractions`|proximité de fractions simples|
|`directionality`|proximité des segments avec angles notables|
|`support`|grandes masses visuellement basses|
|`alignment`|proximité de points avec guides harmoniques|
|`readingOrder`|lecture spatiale stable|
|`smallFirst`|petite région tôt dans l’ordre de lecture|

## 14.3 Règles harmoniques dans le scoring

|Critère|Règle|
|---|---|
|`simpleFractions`|teste les fractions avec dénominateurs de `2` à `12`|
|`directionality`|favorise `0°`, `30°`, `45°`, `60°`, `90°`, etc.|
|`alignment`|favorise `0`, `25`, `1/3`, `50`, `2/3`, `75`, `100`|
|`exactness`|favorise les aires proches du ratio cible|

## 14.4 Règle stricte

Ne pas modifier :

```txt
src/lib/scoring.ts
```

dans cette PR.

Règle :

> Le scoring classe les propositions. Il ne doit pas être présenté comme une preuve harmonique absolue.

---

# 15. Famille observée : α = √6/2

## 15.1 Statut

Cette famille vient des ratios lus dans les captures de vaisseau.

Elle n’est pas encore codée dans Norma.

Elle doit être documentée comme :

```txt
observed_external
candidate_to_add
```

mais aussi avec prudence :

```txt
do_not_use_yet
```

pour le moteur runtime actuel.

## 15.2 Définition

```txt
α = √6 / 2 ≈ 1.224744871
```

Ce n’est pas directement un ratio musical simple.

Mais :

```txt
α² = 3/2
```

Donc α est une racine géométrique de la quinte juste.

## 15.3 Puissances

|Forme|Valeur exacte|Valeur approx.|Lecture|
|---|--:|--:|---|
|`α¹`|`√6/2`|`1.2247`|géométrique|
|`α²`|`3/2`|`1.5000`|harmonique classique|
|`α³`|`3√6/4`|`1.8371`|semi-harmonique|
|`α⁴`|`9/4`|`2.2500`|harmonique composé|
|`α⁵`|`9√6/8`|`2.7557`|semi-harmonique|
|`α⁶`|`27/8`|`3.3750`|harmonique composé|
|`α⁷`|`27√6/16`|`4.1335`|proche de `φ³`|
|`α⁸`|`81/16`|`5.0625`|proche de `πφ`|

Règle :

```txt
α^(2n) = (3/2)^n
```

Cela signifie que les puissances paires de α forment une chaîne de quintes justes.


|Ratio|Valeur|Nom classique|Statut|
|---|---|---|---|
|1/11/11/1|1.000|unisson|référence générale|
|2/12/12/1|2.000|octave|référence générale|
|3/23/23/2|1.500|quinte juste|déjà central via α2\alpha^2α2|
|4/34/34/3|1.333|quarte juste|référence générale|
|5/45/45/4|1.250|tierce majeure|référence générale|
|8/58/58/5|1.600|sixte / proche doré selon contexte|référence générale|

---

# 16. Famille dorée observée

## 16.1 Ratios dorés observés

|Forme|Valeur approx.|Usage|
|---|--:|---|
|`φ`|`1.618`|nombre d’or|
|`φ²`|`2.618`|extension dorée|
|`φ³`|`4.236`|extension dorée forte|
|`φ⁴`|`6.854`|extension dorée très forte|
|`φ⁵`|`11.090`|grande expansion|
|`1/φ`|`0.618`|position / format vertical|
|`φ⁻²`|`0.382`|complément doré|
|`2/φ`|`1.236`|format Poussin horizontal|
|`φ/2`|`0.809`|format Poussin vertical|
|`φ²/2`|`1.309`|format Poussin horizontal|
|`2/φ²`|`0.764`|format Poussin vertical|

## 16.2 Statut

Cette famille existe déjà partiellement dans Norma :

- pour les surfaces ;
    
- pour les positions ;
    
- pour certains angles ou lectures pentagonales.
    

Mais certains usages observés dans les captures ne sont pas encore intégrés comme règles moteur.

Statut recommandé selon le contexte :

```txt
coded_currently
```

pour les usages déjà dans l’app.

```txt
observed_external
candidate_to_add
```

pour les usages vus dans les captures.

---

# 17. Famille circulaire et cercle-or observée

## 17.1 Ratios circulaires

|Forme|Valeur approx.|Lecture|
|---|--:|---|
|`π`|`3.142`|cercle pur|
|`2π`|`6.283`|circonférence/rayon|
|`π/φ`|`1.942`|cercle réduit par or|
|`π/φ²`|`1.200`|cercle réduit par or carré|
|`πφ`|`5.083`|cercle amplifié par or|
|`πφ²`|`8.225`|cercle amplifié par or carré|

## 17.2 Statut

Ces ratios ont été observés dans les captures.

Ils ne sont pas encore une famille codée dans Norma.

Statut recommandé :

```txt
observed_external
candidate_to_add
```

Mais utiliser aussi :

```txt
ambiguous
```

quand ils sont proches d’une puissance de `α`.

---

# 18. Règle rayon / diamètre

## 18.1 Suffixes observés

Dans les captures de vaisseau, les suffixes semblent importants.

|Suffixe|Lecture|
|---|---|
|`_r`|radius / rayon|
|`_d`|diameter / diamètre|

## 18.2 Règle stricte

Ne jamais supprimer le suffixe :

```txt
_r
_d
```

Pourquoi ?

Parce qu’un même objet comparé par rayon ou diamètre peut changer le ratio par un facteur `2`.

Exemple :

```txt
relation en rayon    -> peut donner 2π
relation en diamètre -> peut donner π
```

Règle Norma Core future :

> La nature de la mesure fait partie du ratio. Un ratio entre diamètres n’est pas le même objet sémantique qu’un ratio entre rayons.

---

# 19. Collisions numériques importantes

## 19.1 Définition

Certaines constantes différentes sont très proches.

Le moteur ne doit pas choisir trop tôt.

Il doit garder plusieurs matches possibles.

## 19.2 Table des collisions

|Constante A|Valeur|Constante B|Valeur|Lecture|
|---|--:|---|--:|---|
|`α`|`1.2247`|`π/φ²`|`1.1999`|proche mais écart notable|
|`α³`|`1.8371`|`π/φ`|`1.9416`|proche mais pas identique|
|`α⁷`|`4.1335`|`φ³`|`4.2361`|collision possible|
|`α⁸`|`5.0625`|`πφ`|`5.0832`|collision très forte|
|`1.707`|`1.707`|`1 + 1/√2`|`1.7071`|match fort Poussin|
|`1.236`|`1.236`|`2/φ`|`1.2361`|match fort Poussin|

## 19.3 Règle moteur future

Préférer :

```txt
possibleMatches[]
```

au lieu de :

```txt
match
```

Le moteur doit pouvoir dire :

- match principal ;
    
- match alternatif ;
    
- écart numérique ;
    
- famille ;
    
- statut ;
    
- confiance ;
    
- raison.
    

---

# 20. Inventaire complet des ratios observés dans les captures de vaisseau

## 20.1 Statut global

Cette section contient les ratios extraits précédemment.

Statut global :

```txt
observed_external
```

Ne pas encore injecter directement dans Norma App.

Ne pas les classer comme `coded_currently`.

Ne pas supprimer les suffixes `_r` et `_d`.

Ne pas inventer les valeurs illisibles.

---

## 20.2 Bloc A — main vessel features A, B, C, D, E, F

|Ratio observé|Match possible|
|---|---|
|`E_r / D_r`|`(√6/2)²`|
|`C_d / D_r`|`π · φ`|
|`C_d / D_r`|`(√6/2)^8`|
|`C_d / E_r`|`(√6/2)^6`|
|`E_r / F_r`|`π / φ²`|
|`A_d / F_r`|`(√6/2)^5`|
|`B_d / F_r`|`(√6/2)^7`|

---

## 20.3 Bloc B — features G, H, J, K, L, M, N

|Ratio observé|Match possible|
|---|---|
|`D_r / J_r`|`(√6/2)²`|
|`H_d / F_r`|`π / φ`|
|`C_r / K_d`|`φ³`|
|`E_r / J_r`|`(√6/2)^4`|
|`A_r / J_r`|`φ²`|
|`C_d / G_r`|`(√6/2)²`|
|`E_r / L_r`|`φ⁵`|
|`H_r / D_r`|`√6/2`|
|`F_r / K_r`|`φ³`|
|`G_r / D_r`|`(√6/2)^6`|
|`G_r / E_r`|`(√6/2)^4`|
|`E_r / K_r`|`(√6/2)^8`|

---

## 20.4 Bloc C — autre table zoomée

|Ratio observé|Match possible|
|---|---|
|`D_d / B_r`|`√6/2`|
|`A_d / F_r`|`φ³`|
|`A_r / B_r`|`√6/2`|
|`A_r / D_d`|`1`|
|`J_r / D_r`|`(√6/2)^3`|
|`J_d / H_r`|`φ³`|
|`C_r / H_r`|`π / φ`|
|`J_d / B_r`|`(√6/2)^4`|
|`G_r / H_r`|`√6/2`|
|`J_d / A_r`|`(√6/2)^3`|
|`C_d / D_r`|`(√6/2)^6`|
|`J_r / F_r`|`π / φ`|
|`H_d / F_r`|`(√6/2)^3`|
|`C_d / J_r`|`(√6/2)^3`|
|`H_d / G_r`|`φ`|
|`G_d / E_r`|`π / φ`|
|`J_d / E_r`|`(√6/2)^6`|

---

## 20.5 Bloc D — grande table verticale

|Ratio observé|Match possible|
|---|---|
|`H_r / R_r`|`π · 2`|
|`H_r / R_d`|`π`|
|`G_r / N_r`|`(√6/2)^8`|
|`E_r / Q_r`|`(√6/2)^5`|
|`H_r / S_d`|`π · φ²`|
|`H_d / N_r`|`π · φ²`|
|`H_r / N_r`|`(√6/2)^7`|
|`G_r / N_r`|`π · φ`|
|`H_d / Q_r`|`π · φ²`|
|`B_d / L_r`|`φ²`|
|`F_r / R_r`|`φ⁴`|
|`K_d / C_r`|`(√6/2)^6`|
|`F_r / R_d`|`(√6/2)^6`|
|`G_r / Q_r`|`φ³`|
|`D_d / Q_r`|`(√6/2)^5`|
|`B_r / Q_r`|`(√6/2)^7`|
|`F_r / P_r`|`π · 2`|
|`A_r / P_r`|`φ⁵`|
|`D_d / P_r`|`φ⁵`|
|`A_r / Q_r`|`(√6/2)^8`|
|`K_r / E_r`|`φ²`|
|`F_r / N_r`|`(√6/2)^4`|
|`E_r / N_r`|`φ²`|
|`D_d / Q_r`|`π · φ`|
|`A_r / Q_r`|`π · φ`|
|`F_r / P_d`|`φ²`|
|`M_d / H_r`|`π / φ`|
|`E_r / P_d`|`π`|
|`C_r / ?`|`1`|

Note :

```txt
C_r / ?
```

Le dernier dénominateur est illisible.

Garder `?`.

Ne pas inventer.

---

## 20.6 Bloc E — table du bas à droite

|Ratio observé|Match possible|
|---|---|
|`D_r / K_r`|`(√6/2)^6`|
|`G_r / A_r`|`π / φ`|
|`E_r / H_r`|`√6/2`|
|`B_d / H_r`|`φ³`|
|`E_r / K_r`|`π · φ`|
|`F_r / K_r`|`(√6/2)^7`|
|`B_r / J_d`|`π / φ`|
|`C_d / H_r`|`(√6/2)^7`|
|`G_d / B_r`|`φ²`|
|`H_d / E_r`|`φ`|
|`B_r / K_d`|`φ³`|

---

# 21. Patterns observés dans les captures de vaisseau

## 21.1 Chaîne α

La famille `α = √6/2` est très dominante.

On observe des puissances de `α` de `1` à `8`.

Cela ressemble à une échelle hiérarchique.

Règle candidate :

> Les rapports `α^n` fonctionnent comme une échelle multiplicative. Les exposants peuvent s’additionner ou se soustraire dans des chaînes de features.

Exemple conceptuel :

```txt
E / D = α²
G / E = α⁴
donc G / D = α⁶
```

Ce pattern est observé.

Il n’est pas encore une règle moteur.

## 21.2 Famille dorée secondaire

On observe :

```txt
φ
φ²
φ³
φ⁴
φ⁵
```

Cette famille semble servir aux transitions fortes entre features.

Statut :

```txt
observed_external
candidate_to_add
```

## 21.3 Famille circulaire

On observe :

```txt
π
2π
π/φ
π/φ²
πφ
πφ²
```

Cette famille semble liée aux rayons, diamètres, courbures et circularité.

Statut :

```txt
observed_external
candidate_to_add
ambiguous
```

selon les collisions numériques.

## 21.4 Hubs géométriques

Certaines features reviennent souvent comme ancres.

|Ancre|Lecture probable|
|---|---|
|`D`|ouverture / noyau|
|`F`|cou / transition|
|`J`|courbure / structure|
|`K`|ancre de comparaison|
|`N`|extension / curvature|
|`Q`|ancre secondaire dense|
|`P/R`|rayon / diamètre / cercle|

Règle :

> Ne pas coder ces lectures comme vérités. Les garder comme observations.

---

# 22. Organisation recommandée de la future Bible technique

## 22.1 Catégories de données

Quand la Bible deviendra un catalogue structuré, utiliser ces catégories :

|Catégorie|Contenu|
|---|---|
|`aspectRatioRules`|formats largeur/hauteur|
|`surfaceRatioPresets`|ratios `A:B:C`|
|`positionTokens`|points normalisés|
|`angleTokens`|angles harmoniques|
|`intersectionPresets`|règles point + angle + merge|
|`constructionFamilies`|`parallel`, `crossed`, `V`, `radiant`, etc.|
|`snappingRules`|règles soft/hard snap|
|`scoringRules`|heuristiques de classement|
|`observedFeatureRatios`|ratios extraits d’objets externes|
|`constantFamilies`|`φ`, `√2`, `δ`, `α`, `π`|
|`aliasRules`|collisions et équivalences proches|
|`classificationRules`|exact, strong, ambiguous, speculative|

## 22.2 Champs minimaux pour chaque entrée

Chaque entrée devrait avoir :

|Champ|Rôle|
|---|---|
|`id`|identifiant stable|
|`label`|nom lisible|
|`value`|valeur numérique si applicable|
|`expression`|formule symbolique|
|`family`|famille mathématique|
|`level`|format, surface, position, angle, etc.|
|`status`|`coded_currently`, `observed_external`, etc.|
|`source`|app, capture, Poussin, manuel|
|`confidence`|`exact`, `strong`, `approximate`, `speculative`|
|`notes`|explication courte|
|`aliases`|constantes proches ou équivalentes|
|`possibleMatches`|matches alternatifs conservés|
|`doNotAutoSelect`|`true` si ambigu ou spéculatif|

## 22.3 Exemple d’entrée future

Exemple conceptuel pour un format Poussin :

```txt
id: "poussin.aspect.1_618"
label: "Poussin golden horizontal"
value: 1.618
expression: "φ"
family: "golden"
level: "format"
status: "observed_external"
source: "Poussin"
confidence: "strong"
doNotAutoSelect: false
```

Exemple conceptuel pour `1.325` :

```txt
id: "poussin.aspect.1_325"
label: "Poussin observed unclassified"
value: 1.325
expression: null
family: "observed"
level: "format"
status: "observed_external"
source: "Poussin"
confidence: "unknown"
doNotAutoSelect: true
notes: "No obvious canonical match. Do not force."
```

---

# 23. Fichiers à lire dans le repo actuel

Avant de modifier quoi que ce soit, lire ces fichiers.

|Fichier|Pourquoi|
|---|---|
|`README.md`|comprendre les vérités produit actuelles|
|`src/types.ts`|comprendre les types `A/B/C`, families, configs|
|`src/lib/presets.ts`|ratios, positions, angles, intersections déjà codés|
|`src/lib/ratios.ts`|conversion ratio → pourcentages → aires|
|`src/lib/compositions.ts`|builders géométriques|
|`src/lib/candidates.ts`|génération de propositions|
|`src/lib/manualEditing.ts`|snapping et handles manuels|
|`src/lib/scoring.ts`|scoring actuel|
|`src/lib/viewTransform.ts`|rotation snap harmonique|
|`src/lib/geometry.ts`|géométrie basse couche|
|`src/lib/__tests__/harmonic.test.ts`|tests existants du système harmonique|

---

# 24. Fichiers à modifier en première étape

## 24.1 Fichier attendu

Créer :

```txt
docs/harmonic-ratio-bible.md
```

Si le dossier n’existe pas, créer :

```txt
docs/
```

Optionnel :

```txt
docs/README.md
```

seulement si le projet a besoin d’un index de documentation.

## 24.2 Contenu attendu

Le fichier doit contenir :

- les sections de cette Bible ;
    
- des tables propres ;
    
- des statuts clairs ;
    
- les valeurs Poussin complètes ;
    
- les ratios `A:B:C` existants ;
    
- les tokens de position ;
    
- les angles ;
    
- les intersections ;
    
- les constructions ;
    
- le snapping ;
    
- le scoring ;
    
- les familles observées ;
    
- les collisions ;
    
- les ratios de vaisseau ;
    
- les règles de prudence ;
    
- les fichiers à lire ;
    
- les fichiers à ne pas modifier ;
    
- les acceptance criteria.
    

---

# 25. Fichiers à ne pas modifier en première étape

Ne pas modifier :

```txt
src/lib/presets.ts
src/lib/compositions.ts
src/lib/candidates.ts
src/lib/scoring.ts
src/lib/manualEditing.ts
src/lib/viewTransform.ts
src/types.ts
```

Pourquoi ?

Parce que cette Bible contient :

- des ratios déjà codés ;
    
- des ratios observés ;
    
- des ratios candidats ;
    
- des ratios ambigus ;
    
- des ratios non validés.
    

On doit d’abord valider la taxonomie avant d’impacter le moteur.

---

# 26. Fichiers à modifier en deuxième étape seulement après validation

Après validation produit et architecture, on pourra créer un catalogue structuré.

Options possibles :

```txt
src/lib/harmonicCatalog.ts
```

ou :

```txt
src/lib/ratioPacks/coreHarmonics.ts
src/lib/ratioPacks/poussinFormats.ts
src/lib/ratioPacks/observedFeatureRatios.ts
```

Mais ne pas le faire dans la première PR.

---

# 27. Règles strictes à respecter

## Règle 1 — Ne pas mélanger les niveaux

Poussin = format global.

Norma `A:B:C` = surfaces.

Tokens = positions.

Angles = orientations.

Intersections = relations point + angle + merge.

Snapping = assistance UI.

Scoring = classement heuristique.

Vaisseau = ratios observés entre features.

## Règle 2 — Ne pas surinterpréter

Si une valeur est proche d’une formule, mais pas évidente, la marquer :

```txt
speculative
```

ou :

```txt
unknown
```

Exemple :

```txt
1.325
```

n’a pas de match canonique évident.

Ne pas inventer.

## Règle 3 — Garder les collisions

Si deux matches sont possibles, conserver les deux.

Exemple :

```txt
C_d / D_r
```

peut matcher selon contexte :

```txt
πφ
α⁸
α⁶
```

Ne pas écraser.

## Règle 4 — Préserver les suffixes

Ne pas supprimer :

```txt
_r
_d
```

Ils changent le sens de la mesure.

## Règle 5 — Préserver le contexte source

Chaque ratio doit dire d’où il vient :

- app actuelle ;
    
- Poussin ;
    
- capture vaisseau ;
    
- règle mathématique ;
    
- hypothèse ;
    
- observation manuelle.
    

## Règle 6 — Ne pas casser l’existant

La première PR est documentaire.

Elle ne doit pas modifier le comportement de Norma.

---

# 28. Acceptance criteria

La tâche est réussie si :

1. un fichier `docs/harmonic-ratio-bible.md` existe ;
    
2. il contient les niveaux : format, surface, position, angle, intersection, construction, snapping, scoring, observation ;
    
3. il contient la liste complète Poussin ;
    
4. il contient les valeurs Poussin exactes : `0.353`, `0.618`, `0.707`, `0.764`, `0.796`, `0.809`, `0.828`, `1`, `1.236`, `1.309`, `1.325`, `1.353`, `1.382`, `1.414`, `1.5`, `1.618`, `1.707`, `2` ;
    
5. il garde `1.325` comme observé non classé / à vérifier ;
    
6. il garde `0.796` comme lecture possible mais à vérifier ;
    
7. il contient les ratios de surface actuels de Norma ;
    
8. il explique que tous les presets `A:B:C` ne sont pas harmoniques classiques ;
    
9. il contient le carré canonique `100×100` de l’app actuelle ;
    
10. il contient les tokens de position actuels ;
    
11. il contient les angles harmoniques actuels ;
    
12. il contient les règles de rotation snap ;
    
13. il contient les presets d’intersection actuels ;
    
14. il contient les détails `HarmonicCrossedConfig` ;
    
15. il contient la recherche automatique harmonique par densité ;
    
16. il contient les seuils soft/hard snap ;
    
17. il contient les règles de scoring et précise qu’elles sont heuristiques ;
    
18. il contient la famille `α = √6/2` ;
    
19. il contient les familles `φ`, `π`, `πφ` ;
    
20. il contient l’inventaire des ratios observés dans les captures de vaisseau ;
    
21. il marque clairement les ratios codés vs observés vs candidats ;
    
22. il explique les collisions numériques ;
    
23. il explique pourquoi Poussin n’est pas un ratio `A:B:C` ;
    
24. il explique pourquoi les ratios de vaisseau ne doivent pas être injectés directement ;
    
25. il contient une section “fichiers à lire” ;
    
26. il contient une section “ne pas modifier” ;
    
27. il ne change aucun fichier runtime ;
    
28. les tests existants ne sont pas impactés.
    

---

# 29. Vérifications à faire avant livraison

Avant de livrer :

- vérifier que la liste Poussin contient bien les 18 valeurs ;
    
- vérifier que `1.325` est bien marqué à vérifier ;
    
- vérifier que `0.796` n’est pas présenté comme un match sûr ;
    
- vérifier que `C_r / ?` reste avec `?` ;
    
- vérifier que les suffixes `_r` et `_d` ne sont pas supprimés ;
    
- vérifier que Poussin est classé comme `aspectRatioRules` ;
    
- vérifier que les surfaces Norma sont classées comme `surfaceRatioPresets` ;
    
- vérifier que les tokens `1/4`, `1/3`, `φ⁻²`, etc. sont classés comme `positionTokens` ;
    
- vérifier que les angles sont classés comme `angleTokens` ;
    
- vérifier que les presets Tertian/Golden/Root-two/Pentagonal/Musical sont classés comme `intersectionPresets` ;
    
- vérifier que les règles de snap sont classées séparément ;
    
- vérifier que les règles de scoring sont décrites comme heuristiques ;
    
- vérifier que les collisions sont bien gardées ;
    
- vérifier que la Bible ne prétend pas que tout est déjà codé ;
    
- vérifier que la PR ne modifie aucun fichier runtime.
    

---

# 30. Risques

|Risque|Exemple|Prévention|
|---|---|---|
|Mélange de niveaux|mettre Poussin dans `A:B:C`|garder `level` obligatoire|
|Surinterprétation|forcer `1.325`|marquer `unknown` ou `à vérifier`|
|Régression app|modifier `presets.ts` trop tôt|PR documentaire seulement|
|Perte de contexte|supprimer `_r` / `_d`|garder les ratios bruts|
|Faux match unique|choisir `πφ` au lieu de garder `α⁸` aussi|utiliser `possibleMatches`|
|Explosion de complexité|tout intégrer au moteur|d’abord doc, ensuite pack|
|Non-déterminisme futur|aliases non ordonnés|prévoir ordre stable|
|Confusion UI/core|snap UI = vérité core|documenter séparation|
|Confusion scoring/règle|scoring = preuve harmonique|rappeler que scoring = heuristique|
|Confusion app/core|`100×100` codé partout|documenter comme état actuel app|

---

# 31. Recommandation de PR

## 31.1 Titre

```txt
docs: add harmonic ratio bible
```

## 31.2 Scope

```txt
Documentation only.
No runtime behavior change.
No preset modification.
No solver modification.
No scoring modification.
```

## 31.3 Fichiers attendus

```txt
docs/harmonic-ratio-bible.md
```

Optionnel :

```txt
docs/README.md
```

si le dossier `docs` est nouveau.

## 31.4 Message de PR

Le message de PR doit expliquer :

- pourquoi la Bible existe ;
    
- ce qu’elle couvre ;
    
- ce qu’elle ne change pas ;
    
- pourquoi certains ratios sont marqués `observed_external` ou `candidate_to_add` ;
    
- pourquoi les collisions sont intentionnellement conservées ;
    
- pourquoi Poussin est séparé des presets `A:B:C` ;
    
- pourquoi les ratios de vaisseau ne sont pas injectés dans le moteur.
    

---

# 32. Décisions à verrouiller

1. Norma distingue les ratios de format, surface, position, angle, intersection, construction, snapping, scoring et observation externe.
    
2. Les formats Poussin sont des ratios largeur/hauteur, pas des ratios de surface.
    
3. Les ratios `A:B:C` actuels restent les seuls presets de surface codés tant qu’une nouvelle décision n’est pas prise.
    
4. Les tokens harmoniques actuels de position sont conservés comme base canonique.
    
5. Les angles harmoniques actuels sont conservés comme base canonique.
    
6. Les presets d’intersection actuels sont conservés comme base canonique.
    
7. La famille `α = √6/2` est une famille observée externe, candidate pour futur pack, mais non codée actuellement.
    
8. Les familles `π`, `2π`, `π/φ`, `πφ` et `πφ²` sont observées/candidates, pas encore core.
    
9. Les collisions numériques doivent être gardées comme `possibleMatches`.
    
10. Les ratios ambigus ou incertains doivent rester marqués `ambiguous`, `speculative` ou `unknown`.
    
11. Les suffixes `_r` et `_d` sont sémantiques et doivent être préservés.
    
12. Le snapping est une aide UI, pas une vérité du core.
    
13. Le scoring est une heuristique de classement, pas une contrainte géométrique dure.
    
14. La première étape doit être documentaire.
    
15. Aucune modification runtime ne doit être faite sans validation de la taxonomie.
    

---

# 33. Résumé simple pour le développeur junior

Tu dois créer une Bible propre.

Tu ne dois pas coder le moteur.

Tu ne dois pas changer les presets existants.

Tu ne dois pas changer le solver.

Tu ne dois pas changer le scoring.

Tu dois classer les ratios par nature.

Tu dois être prudent.

Un ratio proche n’est pas automatiquement une vérité.

Un ratio observé n’est pas automatiquement une règle.

Un ratio de format n’est pas un ratio de surface.

Un angle n’est pas une position.

Une position n’est pas un ratio `A:B:C`.

Un snap UI n’est pas une règle du core.

Un score n’est pas une preuve harmonique.

Le but est de préparer Norma à devenir un moteur sérieux de géométrie proportionnelle, pas une collection confuse de nombres sacrés.