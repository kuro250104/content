Le langage CSS permet de styliser les formulaires HTML, afin de les rendre plus attrayants et de les faire correspondre avec le design et la mise en page. 

## Styliser les champs input

Pour définir une largeur à un champ input, il faut utiliser la propriété ```width```.

Exemple :

```css
input {
	width: 400px; /* Les champs du formulaire ont une largeur de 400px */
}
```

## Marges intérieures sur les inputs

Pour ajouter un espace entre le bord du champ de texte et l’endroit où l’utilisateur doit commencer à écrire son texte, il faut utiliser la propriété ```padding```.

__Remarque__ : S’il y a plusieurs champs à la suite, il est recommandé de définir également des marges extérieures avec ```margin```. Cela laissera plus d’espace à l’extérieur des champs.

Exemple :

```css
input[type="text"] {
    padding-left: 20px;
}
```

## Ajouter une bordure

Pour ajouter une bordure autour d’un input, il faut utiliser la propriété ```border```. De plus, pour arrondir les coins, la propriété ```border-radius``` doit également être utilisée.

Exemple :

```css
input[type="text"] {
	border: 1px solid green;
	border-radius: 3px;
}
```

## Inputs colorés

Pour changer la couleur d’un input, la propriété ```background-color``` doit être utilisée, de même que ```color``` doit être utilisée pour changer la couleur de la police à l’intérieur du champ.

Exemple :

```css
input[type="text"] {
	background-color: red;
	color: white;
}
```

## Les input focus

Un input est dit “focus” lorsque le curseur se trouve à l’intérieur du champ. Ainsi est-il possible de styliser un input lorsque le curseur se trouve à l’intérieur, grâce à la pseudo-classe ```:focus```.

Exemple :

```css
input[type="text"]:focus {
	background-color: white;
	color: black;
}
```

## Ajouter une image/icône dans un input

Le langage CSS permet d’ajouter une image, ou plutôt une icône, à l’intérieur d’un input. Pour ce faire, il faut utiliser la propriété ```background-image``` et la positionner en utilisant ```background-position```.

Exemple :

```css
input[type="text"] {
	background-color: white;
	background-image: url("search.png");
	background-position: 10px 10px;
	background-repeat: no-repeat;
	padding-left: 40px;
}
```

L’exemple ci-dessus ajoute l’image d’une loupe dans le champ de texte. La marge intérieure gauche est définie à 15 pixels afin que l’écriture n’empiète pas sur l’image.

## Styliser un textarea

Le langage CSS permet également de styliser les ```textareas```. Cela permet notamment de définir la propriété ```resize``` à ```none```, permettant de ne pas pouvoir agrandir le ```textarea```. 

Exemple :

```css
textarea {
	width: 300px;
	height: 100px;
	border: 3px solid rgb(127, 143, 166);
	border-radius: 3px;
	padding: 10px 20px;
	resize: none;
}

textarea:focus {
	border: 3px solid rgb(86, 115, 154);
	outline: none;
}
```

## Styliser une liste d’option

Il est également possible de styliser une liste d'options.

Exemple :

```css
select {
	width: 50%;
	padding: 10px 20px;
	border: none;
	border-radius: 4px;
	outline: none;
	background-color: grey;
}
```

## Styliser un bouton

L’exemple ci-dessous montre comment styliser un bouton en CSS :

```css
input[type="button"], input[type="submit"] {
	background-color: red;
	border: none;
	color: white;
	text-align: center;
	padding: 10px 20px;
	margin: 4px 2px;
	text-decoration: none;
}
```