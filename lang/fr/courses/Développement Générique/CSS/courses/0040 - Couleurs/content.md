Le but du CSS étant de mettre en forme une page HTML, il est possible de colorer des éléments d’une page HTML. 

En CSS, colorer un élément peut se faire de 2 manières différentes :
En spécifiant directement le nom de la couleur en anglais. Par exemple : red, blue, orange, green, etc.
En utilisant des valeurs RGB et HEX.

Dans un premier temps, ce cours détaillera comment colorer certains éléments d’une page HTML en spécifiant directement le nom de la couleur. Dans une seconde partie, ce cours détaillera l’utilisation des valeurs RGB et HEX .

## La couleur de fond

Le langage CSS permet de changer la couleur de fond des éléments HTML. Pour réaliser cela, la propriété ```background-color``` est utilisée. 

Cette propriété s’utilise de la manière suivante :

```css
selecteur {
    background-color : valeur (nom de la couleur);
}
```

Exemple :

```css
p {
    background-color : red;
}
```

Le code CSS de l’exemple permet de rendre l’arrière-plan d’un paragraphe rouge.

## La couleur du texte

Le CSS permet également de colorer le texte d’une page HTML. Pour ce faire, le CSS utilise une propriété toute prête : ```color```.

Cette propriété s’utilise exactement de la même manière que ```background-color```.

Exemple :

```css
p {
    color : blue
}
```

##  Les valeurs RGB, HEX et HSL

Dans les exemples ci-dessus, les différentes propriétés sont utilisées en spécifiant directement le nom de la couleur à utiliser. Néanmoins, la couleur des éléments HTML peut également être changée en utilisant des valeurs RGB et HEX.

### RGB

En informatique, les couleurs sont créées à partir d’une certaine quantité de rouge, de vert et de bleu ; d’où le nom RGB, pour “Red Green Blue”. C’est pourquoi le CSS permet de changer la couleur d’une élément HTML en précisant la quantité de rouge, de vert et de bleu à utiliser. 

Pour ce faire, en CSS, la formule suivante est utilisée :

```css
rgb(quantite_de_rouge, quantite_de_vert, quantite_de_bleu)
```

Chacun des paramètres Red, Green, Blue définit l’intensité de la couleur, en utilisant une valeur située entre 0 et 255. 

Par exemple, pour utiliser la couleur rouge, en RGB, il suffit d’écrire la formule suivante :

```css
rgb(255, 0, 0);
```

Dans l’exemple ci-dessus, la couleur rouge est élevée à son intensité maximum (255) tandis que le vert et le bleu sont abaissées à 0, donc inexistante. 

Autre exemple, si la couleur souhaitée est blanc, la formule RGB ressemblera donc à ceci :

```css
rgb(255, 255, 255);
```

Plus concrètement, le CSS offre la possibilité d’utiliser la formule RGB avec les propriétés de couleur situées plus haut dans ce cours. Voici comment réaliser cela :

```css
selecteur {
    color : rgb(rouge, vert, bleu); 
}
```

Exemple :

```css
p {
    background-color : rgb(0, 0, 0);
    color : rgb(255, 255, 255);
}
```

Ici, la couleur de fond des paragraphes sera de couleur noir, car la quantité de rouge, de vert et de bleu est abaissée à 0 ; tandis que la couleur du texte des paragraphes sera de couleur blanche. 

### HEX

Le HEX, pour hexadécimal, permet de déclarer une couleur en utilisant à la fois des chiffres, de 0 à 9, et des lettres, de a à f. 

Comme pour la formule RGB, le HEX désigne la couleur en spécifiant la quantité de rouge, de vert et de bleu. 

En CSS, l’utilisation de l’HEX se fait en utilisant le signe ```#```.

Par exemple, ```#ff0000``` est la forme hexadécimale de la couleur rouge. Ici, la quantité de rouge est élevée à son maximum, ff, tandis que les quantités de vert et de bleu sont à 0. 

L’utilisation des couleurs sous forme hexadécimales en CSS se fait de la manière suivante :

```css
selecteur {
    color : #rrggbb;
}
```

Exemple:

```css
h1 {
    background-color : #ff0000;
    color : #0000ff; /* Les quantités de rouge et de vert sont à 0 alors que le bleu est au maximum (ff) */
}
```

Dans l’exemple ci-dessus, le titre aura un fond de couleur rouge, tandis que le texte que le texte sera de couleur bleue.

### Formule HEX raccourcie

Lorsque les composantes de rouge, de vert et de bleu sont les mêmes dans la formule hexadécimale, il est également possible d’utiliser la formule raccourcie.

Voici la couleur rouge au format hexadécimal : ```#ff0000```.
Voici maintenant la couleur en utilisant la formule hexadécimale raccourcie : ```#f00```.