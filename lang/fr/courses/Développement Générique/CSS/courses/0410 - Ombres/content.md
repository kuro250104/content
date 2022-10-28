Le langage CSS permet d’ajouter un effet ombre à du texte ou à un élément HTML. De manière générale, cela donne un effet 3D à une image. 

## La propriété text-shadow

Pour appliquer un effet d’ombre à un élément texte, la propriété ```text-shadow``` doit être utilisée. 

Dans son utilisation la plus minimale, il suffit de préciser l’ombre horizontale et l’ombre verticale à ajouter au texte. Si ces deux paramètres sont précisés, cela donnera plus un effet 3D sur le texte qu’un réel effet d’ombres. 

Exemple :

```css
h1  {
	text-shadow: 2px 2px;
}
```

### Ajouter une couleur d’ombre

Pour changer la couleur de l’ombre derrière un texte, il faut ajouter la couleur après les valeurs d’ombre horizontale et verticale. 

Exemple :

```css
h1  {
	text-shadow: 2px 2px green;
}
```

### Ajouter un effet de flou

Afin que l’effet d’ombre soit total et qu’il n’y ait pas simplement un effet 3D du texte, il faut préciser une valeur de flou avant les valeurs d’ombres. 

Exemple :

```css
h1  {
	text-shadow: 2px 5px 5px green;
}
```

### Ombres multiples

Il est possible d’ajouter plusieurs ombres autour d’un texte. Pour ce faire, il faut simplement séparer les différentes valeurs d’ombres par une virgule.

Exemple :

```css
h1  {
	text-shadow: 0 0 5px green, 0 0 7px #32CD32; /* Les différentes valeurs d'ombres sont séparées par une virgule */
}
```

## La propriété box-shadow

La propriété ```box-shadow``` s’utilise pour ajouter de l’ombre à n’importe quel élément HTML. Son utilisation est similaire à **text-shadow**, à ceci près que **text-shadow** s’utilise seulement pour les éléments textes. 

Dans son utilisation la plus simple, il est possible de déclarer seulement une valeur d’ombre horizontale et une valeur d’ombre verticale. 

Exemple :

```css
div {
    box-shadow: 3px 3px;
}
```

### Ajouter une couleur d’ombre

Pour ajouter une couleur d’ombre, il faut préciser la couleur à utiliser, après les valeurs d’ombres horizontale et verticale. 

Exemple :

```css
div {
    box-shadow: 3px 3px grey; /* L'ombre sera de couleur grise */
}
```

### Effet de flou

Pour renforcer l’effet d’ombre, il est possible d’ajouter un effet de flou. Pour ce faire, il faut préciser la valeur de flou à ajouter à l’effet d’ombre, avant les valeurs d’ombre horizontale et verticale. 

Exemple : 

```css
div {
	box-shadow: 5px 10px 5px grey; /* Ici, l'effet de flou est défini à 10 pixels */
}
```