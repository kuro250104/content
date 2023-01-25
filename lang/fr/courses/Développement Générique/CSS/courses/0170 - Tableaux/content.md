Le langage CSS permet également de styliser les tableaux créés en HTML.

La suite de ce cours détaille l’ensemble des propriétés utilisables pour styliser les tableaux HTML.

## Bordures

Pour styliser les bordures d’un tableau, il faut utiliser la propriété raccourcie ```border```. Cette propriété s’utilise exactement telle que décrite dans le cours sur les bordures, c'est-à-dire qu’elle reçoit les valeurs suivantes :

- Épaisseur de la bordure
- Style de bordure
- Couleur de la bordure

Exemple :

```css
table, th, td {
	border : 5px solid black; /* Ici, le tableau ses cellules ont une bordure de 5px, de type solid et de couleur noire */
}
```

## Tableau avec une largeur complète

Il est par ailleurs possible de donner une largeur au tableau, en utilisant la propriété CSS ```width```. Cependant, dans certains cas, il est possible d’avoir besoin qu’un tableau prenne toute la largeur de la fenêtre du navigateur. Pour ce faire, la propriété ```width``` doit recevoir la valeur 100%.

Exemple : 

```css
table {
	width: 100%; /* Le tableau prend ici toute la largeur de l'écran */
}
```

## Fusionner les cellules d’un tableau

Pour fusionner les cellules d’un tableau, il suffit d’utiliser la propriété ```border-collapse``` et de lui attribuer la valeur ```collapse``` (*s’effondrer*, en anglais).


Exemple :

```css
table {
	border-collapse: collapse; /* Les cellules du tableau sont fusionnées */
}
```

## Taille d’un tableau

La hauteur et la largeur d’un tableau sont définis par les propriétés ```height``` et ```width```.

Exemple :

```css
table {
	width: 500px;
}

th {
	height: 250px;
}
```

Dans cet exemple, le tableau a une largeur de 500 pixels, tandis que les cellules ont une hauteur de 250 pixels.

## Alignement du texte dans un tableau 

### Alignement horizontal

La propriété ```text-align``` permet de définir l’alignement horizontal du texte contenu dans les balises ```<th>``` et ```<td>```.

Cette propriété reçoit une des trois valeurs suivantes :

- ```left``` : aligne le texte horizontalement à gauche
- ```center``` : aligne le texte horizontalement au centre
- ```right``` : aligne le texte horizontalement à droite 

__Remarque__ : Par défaut, l’alignement des éléments ```<th>``` est au centre, tandis que l’alignement des éléments ```<td>``` est à gauche. 

Exemple :

```css
td {
	text-align: center;
}
```

### Alignement vertical

Pour aligner verticalement le contenu d’un tableau, la propriété ```vertical-align``` doit être utilisée. 

Cette propriété reçoit une des trois valeurs suivantes :

- ```top``` : aligne le contenu verticalement en haut
- ```middle``` : aligne le contenu verticalement au centre
- ```bottom``` : aligne le contenu verticalement en bas

__Remarque__ : Par défaut, le contenu d’un tableau est aligné au centre (avec la valeur ```middle```), à la fois pour les éléments contenus dans un ```<th>``` et ceux contenus dans un ```<td>```.

Exemple :

```css
td {
	vertical-align: middle; /* Le texte dans le tableau est centré verticalement */
}
```

## Styliser les tableaux

### Marges intérieures

Afin de gérer l’espacement entre les bordures et le texte, il faut utiliser la propriété padding pour les éléments ```<th>``` et ```<td>```.

Exemple :

```css
th, td {
	padding: 15px; /* Les marges intérieures des <th> et <td> sont définies à 15px */
}
```

### Lignes horizontales

Afin de styliser un tableau, il est possible de n’ajouter que des lignes horizontales afin de séparer les lignes entre elles. 

Pour ce faire, la propriété ```border-bottom``` doit être utilisée avec les éléments ```<th>``` et ```<td>```.

Exemple :

```css
th, td {
	border-bottom: 1px solid black;
}
```

### Surligner au survol de la souris

Comme pour les liens, le langage CSS permet de changer la couleur de fond d’une ligne d’un tableau au survol de la souris. Pour ce faire, le sélecteur ```:hover``` doit être utilisé avec l'élément ```<tr>```.

Ensuite, pour changer la couleur de fond, la propriété ```background-color``` est utilisée.

Exemple : 

```css
tr:hover {
	background-color: red; /* Au survole d'une ligne par la souris, les lignes sont surlignées en rouge */
}
```

### Surligner une ligne sur deux

Pour surligner une ligne sur deux d’un tableau, il faut ajouter le sélecteur ```:nth-child()``` aux éléments ```<tr>``` puis d’utiliser la propriété ```background-color``` pour changer la couleur d’arrière-plan des rangées paires (*even*, en anglais) ou impaires (*odd*, en anglais). 

Exemple :

```css
tr:nth-child(even) {
	background-color: grey; /* Les rangées paires ont un arrière-plan de couleur gris */
}
```

## Tableau responsive

Rendre un tableau responsive signifie que des barres de défilement seront ajoutées si la fenêtre de l’utilisateur est moins large que le tableau. 

Pour ce faire, il faut ajouter, dans le code HTML, un élément type ```<div>``` avec un ```style="overflow-x:auto;"``` autour des balises HTML ```<table>```. Il est également possible de définir cette propriété directement dans le CSS, tant que vous pensez bien à cibler l’élément conteneur du tableau.

__Remarque__ : Ne pas oublier le point-virgule (;) à la fin de la ligne ```overflow-x:auto```, sinon cela ne sera pas interprété par le navigateur et le responsive ne fonctionnera pas.

Exemple :

```html
<body>
	<div class="tabl">
		<table>
			Contenu du tableau 
		</table>
	</div>
</body>
```
Et le CSS sera :

```css
.tabl{
	overflow-x: auto;
}
```
