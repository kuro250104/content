## Centrer des éléments

Définir une largeur pour un élément, en utilisant la propriété ```width``` permet d’éviter que celui-ci ne s’étende sur toute la largeur de son contenant. Ainsi l’élément prendra la largeur définie ; et l’espace restant sera réparti de manière égale entre les deux marges extérieures.

Ainsi, pour aligner des éléments à l’intérieur d’un ```display:block;``` tels que des ```<div>```, il faut utiliser ```margin: auto;```.

__Remarque__ : La méthode ci-dessus pour centrer un élément **n’aura pas d’effet** si la propriété ```width``` **n’est pas définie** ou si la largeur **n’est pas définie à 100 %**.

Exemple :

```css
div {
	width: 500px; /* L'élément à une largeur de 500 pixels */
	margin: auto; /* L'espace restant est réparti équitablement entre les deux margin afin de centrer l'élément */
}
```

## Centrer du texte

Pour centrer du texte au sein d’un élément, il suffit d’utiliser ```text-align: center;```.

Exemple :

```css
.citation {
	text-align: center; /* Le texte est centré au sein de l’élément */
}
```

## Centrer une image

Centrer une image se fait en réglant les marges extérieures gauche et droite sur ```auto```, au sein d’un élément ```block```.

Exemple :

```css
div img {
	margin-left: auto;
	margin-right: auto; /* L'image sera centrée au sein de la div car les deux marges extérieures gauche et droite sont définies à auto */
}
```

## Aligner à gauche ou à droite avec position

L’alignement du texte peut également s’effectuer en utilisant la propriété CSS ```position```. En effet, les différentes valeurs que cette propriété peut recevoir permettent de jouer sur l’alignement des éléments. 

__Remarque__ :  Un cours dédié à cette propriété détail son utilisation.

Exemple :

```css
div {
    right: 0;
	position: absolute; /* L'élément est aligné à droite */
}
```

## Aligner des éléments à gauche ou à droite avec float

Une autre méthode pour aligner des éléments à gauche ou à droite est d’utiliser la propriété ```float```. 

__Remarque__ : Un cours dédié à cette propriété est disponible et détaille l’utilisation du ```float```.

## Aligner verticalement en utilisant les marges intérieures

En CSS, il existe plusieurs moyens d’aligner un élément verticalement. Un de ces moyens est d’ajuster les marges intérieures supérieures et inférieures.

Exemple :

```css
.center {
	padding: 10px 0; /* Ici, l'élément est centré verticalement car les padding supérieures et inférieures sont à 0 */
}
```

Dans cet exemple, l’élément HTML est centré verticalement car les marges intérieures supérieures et inférieures sont définies à 0. Cependant, les valeurs doivent être ajustées en fonction des besoins.

## Aligner verticalement en utilisant la hauteur des lignes

Un autre moyen que propose le langage CSS pour aligner verticalement un élément est d’utiliser la propriété ```line-height```.

Exemple :

```css
.center {
	line-height: 1.5; /* Ici, l'élément est centré verticalement par rapport à la hauteur de la ligne */
}
```