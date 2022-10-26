Le CSS met à disposition différentes propriétés afin de styliser l’ensemble du texte d’une page HTML.

La suite de ce cours détail l'utilisation de ces propriétés.

## Colorer un texte

Pour ajouter de la couleur à un texte, il suffit d’utiliser la propriété ```text-color```.

Cette propriété reçoit une des valeurs suivantes :

- ```nom``` : nom de la couleur en anglais
- ```HEX``` : définit la couleur en fonction de sa valeur hexadécimale
- ```RGB``` : définit la couleur du texte en fonction de sa quantité de rouge, de vert et de bleu

La couleur par défaut du texte d’une page HTML est définie dans le sélecteur ```body```.

Exemple :

```css
body {
	color : red; /* Par défaut, le texte de la page sera de couleur rouge */
}

h1 {
	color : yellow; /* Les titres h1 seront de couleur jaune */
}
```

## Alignement du texte

### Alignement horizontal

Pour aligner horizontalement, le langage CSS met à disposition la propriété ```text-align```. Un texte ne pouvant être centré que de 4 manières différentes, cette propriété peut recevoir une des valeurs suivantes :

- ```left``` : permet d’aligner le texte à gauche
- ```right``` : permet d’aligner le texte à droite
- ```center``` : permet de centrer le texte
- ```justify``` : permet de justifier un texte (justifier un texte permet de faire comme dans un livre : que le texte soit aligné à gauche et à droite)

Exemple :

```css
body {
	text-align : center; /* Ici, le texte de la page est centré */
}
```

### Alignement vertical

Le langage CSS permet également d’aligner un texte horizontalement sur une page. Pour ce faire, il faut utiliser la propriété ```vertical-align```. 

Cette propriété peut recevoir une des 3 valeurs suivantes :

- ```top``` : aligne le texte horizontalement en haut de la page
- ```center``` : aligne le texte horizontalement au centre de la page
- ```bottom``` : aligne le texte horizontalement en bas de la page

Exemple :

```css
body {
	vertical-align: bottom; /* Ici, le texte de la page est aligné verticalement en bas de la page */
}
```

## “Décorer” le texte

Le CSS permet par ailleurs d’ajouter une “décoration” au texte d’une page. Concrètement, cela permet de souligner un texte, d’ajouter une ligne au-dessus d’un texte ou encore de barrer un texte. 

Pour ce faire, il faut utiliser la propriété ```text-decoration```. Cette propriété reçoit une des valeurs suivantes :

- ```none``` : n’ajoute aucune décoration au texte (cette valeur est principalement utilisée pour supprimer le soulignement des liens)
- ```underline``` : permet de souligner un texte
- ```overline``` : ajoute une ligne au-dessus du texte
- ```line-through``` : permet de barrer un texte

Exemple : 

```css
body {
	text-decoration : underline; /* Ici, le texte sera souligné */
}
```

__Remarque__ : Il  n’est pas recommandé de souligner un texte autre qu’un lien, car cela peut plonger l’internaute dans la confusion.

## “Transformer” le texte

En CSS, il est également possible de “transformer” un texte. Cela permet de mettre ce texte soit tout en majuscule, soit tout en minuscule, soit de mettre la première lettre d’un ou plusieurs mots en majuscule. 

Afin de pouvoir faire cela, la propriété `text-transform` doit être utilisée et recevoir une des valeurs ci-dessous :

- ```uppercase``` : met tout le texte en majuscule
- ```lowercase``` : met tout le texte en minuscule
- ```capitalize``` : met chaque première lettre en majuscule

Exemple :

```css
p.quote {
	text-transform: uppercase; /* Ici, le texte d'un paragraphe de classe quote sera mis en majuscule */
}
```

## Espacement du texte

En CSS, il existe des propriétés permettant de gérer l’espacement du texte

### Alinéa

Il est possible de créer un alinéa (*indent*, en anglais), c’est-à-dire de décaler le premier mot d’un paragraphe vers la droite afin de créer un léger décalage avec le reste du paragraphe. Cela rend la lecture plus agréable et, dans un texte contenant plusieurs paragraphes, cela permet de spécifier au lecteur qu’il a changé de paragraphe. 

Pour créer un alinéa en CSS, il suffit d’utiliser la propriété ```text-indent```. Cette propriété reçoit en valeur le nombre de pixels vers la droite dont il faut le premier mot du paragraphe.

Exemple :

```css
p {
	text-indent: 10px; /* Ici, le premier mot du paragraphe aura une indentation de 10 pixels */
}
```

### Espacement des lettres 

Le langage CSS permet également de définir un espacement entre les lettres d’un texte. Pour ce faire, la propriété ```letter-spacing``` doit être utilisée. 

Cette propriété reçoit en valeur le nombre de pixels dont les lettres doivent être espacées. 

Exemple :

```css
p {
	letter-spacing: 2px; /* L'espacement entre les lettres sera de 2 pixels */
}
```

### Interligne

La propriété ```line-height``` est utilisée pour définir la hauteur de boîte d’une ligne.

Sur des éléments bloc, la propriété ```line-height``` indique la hauteur des lignes au sein d’un élément. Sur des éléments de type ```inline```, cette propriété définit la hauteur utilisée afin de calculer la hauteur de boîte d’une ligne. 

Exemple :

```css
div {
	line-height: 20px; /* L'interligne sera de 0.6 pixels */
}
```

Dans cet exemple, la hauteur des lignes au sein de l’élément ```div``` est de 20px.

### Espace entre les mots

La propriété ```word-spacing``` rend possible d’augmenter ou de réduire l’espacement des mots.

Pour augmenter l’espacement des mots entre eux, il faut attribuer à cette propriété un nombre de pixels **positif**, tandis que pour réduire l’espace entre les mots, il faut attribuer à ```word-spacing``` un nombre de pixels **négatif**. 

Exemple :

```css
p {
	word-spacing: 3px; /* Dans tous les paragraphes, les mots seront espacés de 3 pixels */
}

p.quote {
	word-spacing: -2px; /* Dans tous les paragraphes de classe quote, l'espace entre les mots sera réduit de 2 pixels */
}
```

### Gérer les espaces

Le langage CSS permet également de gérer les espaces blancs au sein d’un élément. En effet, lorsque la propriété ```white-space``` est utilisée, celle-ci permet par exemple d’indiquer s’il y aura un retour à la ligne après un espace.

Cette propriété reçoit une des valeurs suivantes :

- ```normal``` : Les espaces blancs sont gérés normalement, comme les autres espaces blancs sur la page. Les retours à la ligne sont gérés naturellement afin de remplir la boîte
- ```nowrap``` : Les retours à la lignes sont supprimés
- ```pre``` : Les espaces blancs sont conservés comme tels, et les retours à la ligne s’effectuent avec des caractères de retour à la ligne, ou des balises HTML telles que ```<br />```
- ```pre-wrap``` : Les espaces sont conservés tels quels. Les retours à la ligne sont gérés par des caractères de saut de lignes, des balises HTML telles que ```<br />```. Il y a également des retours à la ligne automatiques
- ```pre-line``` : Les espaces sont regroupés. Comme pour la ```pre-wrap```, les retours à la ligne sont gérés par des caractères de saut de ligne, des balises HTML et il y a, là aussi, des retours à ligne automatiques.

L’exemple ci-dessous supprime les retours à la ligne automatique :

```css
p {
	white-space : no-wrap;
}
```

__Remarque__ : La propriété ```white-space``` ne permet en aucun cas de gérer la coupure des mots. Pour ce faire, il faudra utiliser la propriété ```word-break```.

## Ajouter de l’ombre

Pour ajouter de l’ombre à un texte, il suffit d’utiliser la propriété ```text-shadow```. Cette propriété peut recevoir les propriétés suivantes, dans cet ordre :

- nombre de pixels verticaux à ombrager 
- nombre de pixels horizontaux à ombrager
- nombre de pixels pour ajouter un effet de flou (optionnel)
- nom de la couleur en anglais (optionnel)

Exemple :

```css
p {
	text-shadow: 2px 2px 7px orange; /* 2 pixels verticaux et horizontaux seront ombragés, avec un effet de flou sur 7 pixels. L'ombre sera de couleur orange */
}
```