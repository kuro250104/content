Le contour (*outline* en anglais) est une ligne, colorée ou non, dessinée à l'extérieur d’une bordure entourant un élément.

En CSS, le contour est principalement utilisé pour faire ressortir un élément. 

La suite de ce cours détail les différentes propriétés utilisées. 

## Le contour

Pour faire des contours sur la bordure d’un élément HTML et styliser ce contour, il faut utiliser une ou plusieurs des cinq propriétés suivantes :

- ```outline-style```
- ```outline-color```
- ```outline-width```
- ```outline-offset```
- ```outline```

__Remarque__ : Le contour **n’est pas** une bordure. Le contour est simplement dessiné à l’extérieur de l’élément HTML, **autour** de la bordure. Ainsi, le contour ne doit-il pas être pris en compte dans le calcul de la largeur et la hauteur total d’un élément HTML.

### Le style de contour

Pour définir le style de contour, il faut utiliser la propriété CSS outline-style. Cette propriété peut prendre plusieurs valeurs dont voici quelques exemples :

- ```dotted``` : Définit un contour avec des points
- ```dashed``` : Définit un contour avec des pointillés
- ```solid``` : Définit un contour dit solide (avec des traits pleins)
- ```double``` : Définit un contour “double”
- ```none``` : Ne définit aucun contour
- ```hidden``` : Définit un contour caché

__Remarque__ : La propriété ```outline-style``` doit être déclarée afin que les autres propriétés de ce cours puissent fonctionner.

## Largeur du contour

Comme pour les bordures, le CSS permet de définir une largeur à un contour, en utilisant la propriété ```outline-width```.

Cette propriété peut recevoir une des valeurs suivantes :

- ```thin``` : épaisseur prédéfinie de **1 pixel**
- ```medium``` : épaisseur prédéfinie de **3 pixels**
- ```thick``` : épaisseur prédéfinie de **5 pixels**
- ```taille``` : possibilité d’attribuer une taille au choix en px, pt, cm, em

L’exemple ci-dessous montre l’utilisation de cette propriété et des différentes valeurs :

```css
h1 {
	outline-style : solid;
	outline-width : thin; /* Ici, le titre a un contour d'une épaisseur de 1 pixel */
}
p {
	outline-style : dotted;
	outline-width : medium; /* Ici, le paragraphe a un contour dotted d'une épaisseur de 3 pixels */
}

p.idee {
	outline-style : solid;
	outline-width : thick; /* Les paragraphes de classe idée à un contour d'une épaisseur de 5 px */
}

div {
	outline-style : dashed;
	outline-width : 7px; /* Ici, la div a un contour d'une épaisseur définie à 7px */
}
```

__Rappel__ : Afin de pouvoir utiliser cette propriété, ```outline-style``` doit **obligatoirement** avoir été **déclaré préalablement**.

## Couleur du contour

Le langage CSS permet également d’attribuer une couleur à un contour. Pour ce faire, la propriété ```outline-color``` est utilisée. 

Cette propriété prend une des valeurs suivantes :

- ```couleur``` : nom de la couleur en anglais
- ```HEX``` : valeur hexadécimale d’une couleur 
- ```RGB``` : attribue une couleur selon sa quantité de rouge, de vert et de bleu
- ```invert``` : procède à une inversion de la couleur, afin de permettre que le contour soit visible indépendamment de la couleur de fond.

Exemple :

```css
p {
	outline-style: hidden;
	outline-width: thin;
	outline-color: blue; /* Ici, le contour est de couleur bleu */
	margin-right: 900px;
}
```

Exemple utilisant la valeur ```invert``` :

```css
p {
	border : 1px solid blue;
	outline-style: hidden;
	outline-color: invert; /* Procède à une inversion de la couleur afin de s'assurer que l'outline soit visible, indépendamment de la couleur de fond */
}
```

## Propriété raccourcie

Afin de rendre le code plus lisible et de gagner du temps, le CSS permet d’utiliser la propriété raccourcie ```outline```.

Cela permet de rassembler les valeurs des trois propriétés suivantes en une seule :

- ```outline-width```
- ```outline-style``` (obligatoire)
- ```outline-color```

La propriété peut recevoir **1, 2 ou 3 valeurs**. L’ordre n’est pas important. 

Exemple :

```css
body {
	outline : solid; /* La propriété reçoit 1 valeur */
}

h1 {
	outline: solid blue; /* La propriété reçoit 2 valeurs */
}

p {
	outline: thick ridge green; /* La propriété reçoit 3 valeurs */
}
```

## La propriété outline-offset

La propriété ```outline-offset``` permet de laisser un espace en le côté/la bordure d’un élément HTML et le contour. Cet espace est transparent. 

Cette propriété reçoit en valeur le nombre de pixels d’écart entre le côté/la bordure de l’élément et le contour.

Exemple :

```css
p {
	border : 5px solid black;
	outline : thick solid;
	outline-offset: 15px; /* Ici, il y aura un écart de 15 pixels entre la bordure et le contour du paragraphe */
}
```