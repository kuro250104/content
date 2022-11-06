## Durée approximative

2 jours

## Prérequis

- <a href="https://microlead.fr/echelles/javascript" title="Prérequis en JavaScript" target="_blank">JavaScript niveau 5</a>
- <a href="https://microlead.fr/echelles/html" title="Prérequis en HTML" target="_blank">HTML niveau 4</a>
- <a href="https://microlead.fr/echelles/css" title="Prérequis en CSS" target="_blank">CSS niveau 4</a>

## Énoncé

### Description courte

Recréer le jeu du Puissance 4 dans une application web en JavaScript.

### Listing de fonctionnalités

- Au chargement de la page, une grille vide de 7 cases de long par 6 cases de haut doit s’afficher.
- Au clic sur l’une des colonnes, un jeton de la couleur du joueur en train de jouer doit se placer dans la case la plus basse non occupée de cette colonne.
- Après qu’un jeton soit placé, c’est à l’autre joueur de jouer. La couleur de ses pions doit être différente du premier.
- Un indicateur doit préciser le joueur dont c’est le tour.
- Si 4 jetons de la même couleur sont adjacents (que ce soit verticalement, horizontalement, ou en diagonale), le joueur dont ce sont les jetons gagne et le jeu s’arrête.
- Si toute la grille est remplie sans qu’il n’y ait jamais 4 jetons adjacents, le jeu indique qu’il y a égalité avant de s’arrêter.

### Contraintes

- Il ne doit pas être possible de placer un jeton dans une colonne déjà pleinement remplie.
- Le jeu doit indiquer le vainqueur dès que celui-ci a placé son pion décisif.

### Pour aller plus loin

- Vous pouvez essayer de créer un mode « 1 joueur » en développant une intelligence artificielle simulant le joueur n°2.
- Vous pouvez faire en sorte d’annoncer la victoire d’un joueur avant qu’il ait posé ses 4 jetons adjacents si à la suite de son tour celui-ci dispose de 2 endroits où il pourrait poser son pion pour gagner.

### Critères de réussite

Le jeu est fonctionnel, il est possible de gagner, de perdre, ou de faire une égalité en suivant les règles.

### Astuces

#### Astuce 1

En récupérant toutes les colonnes dans une liste en JavaScript, puis en récupérant toutes les lignes de la même façon (ou inversement dépendamment de votre architecture HTML), vous pouvez aisément naviguer dans votre grille comme dans un tableau à double entrées (ex : ```document.querySelectorAll(‘.colonne’)[3].querySelectorAll(‘.ligne’)[1]``` peut vous permettre, dépendamment de votre architecture HTML encore une fois, d’accéder au contenu de la case située en abscisse 4 et ordonnée 2).