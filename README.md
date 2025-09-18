# Élévation de Cubes Isométrique NxN

Démo : https://rodeofly.github.io/isometric-cubes/isometric-cubes.html

Ce projet fournit une interface web interactive pour dessiner des piles de cubes en perspective isométrique à partir d'une matrice carrée NxN d'élévations (hauteurs). Chaque cellule de la matrice représente le nombre de cubes empilés à cet emplacement. L'utilisateur peut :

* Modifier dynamiquement la taille de la matrice (augmenter ou réduire la dimension).
* Ajuster l’élévation de chaque cellule par clic gauche (ajouter un cube) ou clic droit (retirer un cube).
* Faire pivoter la matrice de 90° (les piles et leurs couleurs tournent ensemble).
* Régénérer aléatoirement une nouvelle matrice.
* Réinitialiser toutes les cellules à zéro.
* Incrémenter/décrémenter toutes les cellules d’un pas à la fois.
* Appliquer un ombrage sur les faces (effet visuel).
* Choisir l’épaisseur des lignes des contours (0 à 10).
* Harmoniser les couleurs des faces selon différents schémas (triade, tétrade, monochromatique, analogues) en conservant la teinte de la face du dessus.
* Appliquer une couleur unique à toutes les faces en cyclant sur 16 teintes du spectre HSL.
* Passer à une palette adaptée aux daltoniens (différentes simulations de palettes pour protanopie, deuteranopie, etc.).

L’interface s’adapte automatiquement à la taille du navigateur et dispose d’une marge en bas afin que la base des cubes ne soit pas tronquée.

---

## Fonctionnalités principales

1. **Matrice dynamique**

   * Boutons `+` / `-` pour ajouter ou supprimer une ligne et une colonne de zéros.
   * Clic gauche sur une cellule pour ajouter un cube (jusqu'à la hauteur maximale autorisée).
   * Clic droit sur une cellule pour retirer un cube (jusqu’à 0).

2. **Affichage isométrique**

   * Calcul automatique des coordonnées isométriques (angles de 30° par rapport à l’horizontale).
   * Empilement des cubes en relief, chaque couche de cube dessinée du bas vers le haut.
   * Espace libre en bas du canvas (20 px) pour ne pas tronquer la base.

3. **Contrôles de style & couleurs**

   * Sélecteurs de couleur pour chaque face latérale (4 faces) et le dessus.
   * Bouton **Ombrage** : applique un dégradé d’ombres différentes sur chaque face pour un effet plus réaliste.
   * Curseur **Épaisseur lignes** (0–10) pour ajuster l’épaisseur des contours des cubes (0 = sans contour).
   * Bouton **Harmoniser Couleurs** : cycles entre quatre schémas (triade, tétrade, monochromatique, analogues) en conservant la teinte de la face du dessus.
   * Bouton **Couleur Unique** : applique une même teinte HSL à toutes les faces, en cyclant sur 16 pas du spectre.
   * Bouton **Daltonien** : applique une palette adaptée aux déficiences visuelles (protanopie, deutéranopie, etc.) en trois variantes prédéfinies.

4. **Actions globales**

   * **Tourner 90 °** : rotation de la matrice d’une case (chaque pile et ses couleurs tournent).
   * **Régénérer** : génère aléatoirement une nouvelle matrice d’élévations (valeurs entre 1 et 5).
   * **Réinitialiser** : met toutes les cellules à zéro.
   * **+1 Toutes** / **-1 Toutes** : incrémente ou décrémente chaque cellule de la matrice (sans dépasser les limites).

---

## Installation & utilisation

1. **Cloner le dépôt**
   En SSH (si ta clé SSH est configurée) :

   ```bash
   git clone git@github.com:rodeofly/isometric-cubes.git
   ```

   Ou en HTTPS (avec un token GitHub pour s’authentifier) :

   ```bash
   git clone https://github.com/rodeofly/isometric-cubes.git
   ```

2. **Se déplacer dans le dossier**

   ```bash
   cd isometric-cubes
   ```

3. **Ouvrir le fichier HTML dans un navigateur**

   * Double-clique sur `index.html`, ou
   * Lance un serveur local (par exemple) :

     ```bash
     # Sur Python 3
     python3 -m http.server 8080
     ```

     puis ouvre `http://localhost:8080/index.html` dans ton navigateur.

4. **Interaction**

   * Ajuste les couleurs, ombrage, épaisseur lignes via la colonne de gauche.
   * Manipule la matrice à coups de clics.

---

## Développement & contribution

* **Structure**

  * Le cœur de l’application est dans `index.html` (HTML + CSS + JavaScript).
  * Tout est géré côté client (pas de dépendance à un serveur ou à une bibliothèque externe).

* **Débogage**

  * Ouvre la console JavaScript (F12) pour voir d’éventuelles erreurs.
  * Le code est commenté pour faciliter la compréhension des fonctions principales (`drawCubeAt`, `drawAll`, `generateHarmoniousColors`, etc.).

* **Ajout de fonctionnalités**

  * Pour ajouter un nouveau schéma de couleurs ou une variante daltonien, modifie les tableaux `harmonySchemes` ou `daltonPalettes` dans le script.
  * Pour changer la taille des cubes, ajuste la variable `s` (actuellement 50 px).

---

## License

Ce projet est distribué sous licence MIT. Consulte le fichier `LICENSE` pour plus d’information.
