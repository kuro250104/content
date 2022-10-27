Comparé à ```display: inline;```, l’utilisation de ```display: inline-block;``` permet de définir une largeur et une hauteur à un élément. De même, avec ```inline-block```, les marges intérieures et extérieures sont respectées, ce qui n’est pas le cas avec la valeur ```inline```.

Comparé à ```display: block;```, la valeur ```inline-block``` n’ajoute pas de retour à la ligne après l’élément, ce qui permet de faire en sorte que cet élément se situe à côté d’un autre élément. 

```display: inline-block;``` est généralement utilisé afin de créer un menu horizontal, permettant de définir une largeur au menu, tout en gardant la disposition inline.

Exemple avec ```display: block;``` :

```css
nav ul {
	width: 50%; /* La disposition block permet de définir une largeur pour l'élément */
	display: block;
	background-color: green;
}
```

Exemple avec ```display: inline;``` :

```css
nav ul li {
	display: inline; /* La disposition inline ne prend pas en compte la largeur */
	padding-right: 5px;
}
```

Exemple :

```css
nav li {
	width: 50px; /* La disposition inline-block permet d'afficher les éléments comme des inline, tout en permettant de définir
	une largeur */
	display: inline-block;
	padding-right: 5px;
}
```