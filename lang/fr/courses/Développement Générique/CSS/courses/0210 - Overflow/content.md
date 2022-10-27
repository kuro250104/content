La propriété CSS ```overflow``` (*débordement*, en anglais) définit ce qu’il doit arriver avec un contenu qui est trop gros pour s’adapter à son contenant. Cette propriété permet par exemple de définir si le contenu “en trop” doit être caché ou bien si le navigateur doit ajouter des barres de défilement pour afficher le reste du contenu. 

## La propriété overflow

La propriété overflow reçoit une des 4 valeurs suivantes :

- ```visible``` : c’est la valeur attribuée par défaut. Le contenu en trop sera affiché mais dépassera simplement du contenant. 
- ```hidden``` : le contenu qui correspond à la taille du contenant est affiché, le reste est caché. 
- ```scroll``` : le contenu est montré et des barres de navigation sont ajoutées afin que le reste du contenu soit visible. 
- ```auto``` : pareil que pour ```scroll```, à la seule différence près que auto ajoute de barres de navigation seulement lorsque c’est nécessaire.

__Remarque__ : La propriété ```overflow``` ne peut être utilisée qu’avec des **éléments HTML de type block ayant une hauteur spécifiée**.

## Overflow visible

Par défaut, la propriété ```overflow``` est définie avec visible. Tout le contenu est montré, mais tout ce qui est “en trop” dépasse du conteneur. 

Exemple :

```css
.visible {
	width: 300px;
	height: 60px;
	background: red;
	overflow: visible; /* Le contenu en trop dépassera de l'élément (valeur par défaut) */
}
```

## Overflow hidden

Lorsque la propriété overflow reçoit la valeur hidden (caché, en anglais), tout le contenu pouvant rentrer dans le contenant est affiché, le reste est caché. 

Exemple :

```css
.hidden {
	width: 300px;
	height: 60px;
	background: red;
	overflow: hidden; /* Le contenu rentrant dans le rectangle rouge est affiché, le reste est caché */
}
```

## L’overflow scroll

En attribuant la valeur ```scroll``` (*défiler*, en anglais) est attribuée à la propriété CSS overflow, des barres de défilement sont ajoutées afin que l’ensemble du contenu soit visible de l’utilisateur. 

Exemple :

```css
.scroll {
	width: 300px;
	height: 60px;
	background: red;
	overflow: scroll; /* Le contenu rentrant dans le rectangle rouge est affiché, le reste est visible lorsque l'utilisateur utilise
	les barres de défilement */
}
```

## L’overflow auto

```overflow:auto;``` est, lorsqu’il est utilisé permet d’ajouter des barres de défilement seulement lorsque cela est nécessaire. 

Exemple :

```css
.auto {
	width: 300px;
	height: 60px;
	background: red;
	overflow: auto; /* Le contenu rentrant dans le rectangle rouge est affiché, si du contenu "déborde", des barres de 
	navigations sont ajoutées, si nécessaires */
}
```

## Overflow x et y

Les propriétés ```overflow-x``` et ```overflow-y``` permettent de définir comment doivent se comporter les débordements du contenu horizontalement et verticalement.

- ```overflow-x``` définit quoi faire avec le contenu horizontal.
- ```overflow-y``` définit quoi faire avec le contenu vertical.

__Remarque__ : Pour ne pas confondre ```x``` et ```y``` avec les position ```horizontales``` et ```verticales```, il suffit de s’imaginer un graphique sur lequel ```x``` est **l’axe des abscisses** (donc horizontal) et ```y``` **l’axe des ordonnées** (donc vertical).

Exemple :

```css
.xy {
	width: 300px;
	height: 60px;
	background: red;
	overflow-x: hidden; /* N'ajoute pas de barres de défilement horizontales */
	overflow-y: scroll; /* Ajoute des barres de défilement verticales */
}
```