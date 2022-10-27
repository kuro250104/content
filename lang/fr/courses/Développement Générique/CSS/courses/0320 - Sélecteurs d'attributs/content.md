Les sélecteurs d’attributs permettent de cibler des éléments HTML spécifiques en fonction de leurs attributs ou de la valeur d’un attribut. 

## Sélecteur d’attribut

Pour sélectionner un attribut, il faut utiliser les crochets ```[ ]```.

Exemple :

```css
a[target] {
	color: red; /* Tous les éléments <a> avec un attribut target sont en rouge */
}
```

## L’attribut avec une valeur

Le langage CSS permet de sélectionner les éléments avec un attribut particulier. Pour ce faire, il faut utiliser le sélecteur d’attribut de cette manière : ```sélecteur[attribut="valeur"];```.

Exemple : 

```css
a[target="_blank"] {
	color: red; /* Tous les éléments <a> dont la valeur de l'attribut target est _blank sont en rouge */
}
```

## Le sélecteur ~

Lorsque le sélecteur d’attribut est utilisé de la façon suivante ```[attribute~="valeur"];```, cela permet de sélectionner tous les éléments **contenant un mot spécifique**.

Exemple :

```css
p[title~="important"] {
	color: red; /* Tous les éléments <p> dont l'attribut title contient le mot "important" sont de couleurs rouges  */
}
```

## Le sélecteur |

Lorsque le sélecteur ```|``` est utilisé avec le sélecteur d’attribut, cela permet de sélectionner les éléments avec l’attribut spécifié **commence avec la valeur spécifiée**.

Exemple :

```css
p[class|="quote"] {
	margin-left: 30px; /* Tous les éléments <p> dont l'attribut class commence avec le mot "quote" ont une marge extérieure gauche de
	30 pixels  */
}
```

## Le sélecteur ^

Lorsque ce sélecteur est utilisé, cela permet de sélectionner les éléments dont la valeur de l’attribut **commence par la valeur spécifiée**.

Exemple :

```css
p[class^="important"] {
	color: red; /* Tous les éléments <p> dont l'attribut class commence par la valeur "important" sont en rouge */
}
```

## Le sélecteur $

L’utilisation de ce sélecteur permet de ne sélectionner que les éléments dont la valeur de l’attribut spécifié **termine par la valeur spécifiée**.

Exemple :

```css
p[class$="test"] {
    background-color: red; /* Les paragraphes dont la valeur de l'attribut class termine par test ont un arrière-plan rouge */
}
```

## Le sélecteur *

Ce sélecteur permet de sélectionner les éléments dont l’attribut **contient l’attribut spécifié**.

Exemple :

```css
p[title*="image"] {
    color : red; /* Les paragraphes dont l'attribut titre contient la valeur image sont colorés en rouge */
}
```