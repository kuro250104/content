L’affichage (*display*, en anglais) en CSS est une notion très importante. Cette notion permet de comprendre comment les éléments HTML sont agencés lorsqu’il n’y a pas de CSS qui entre en jeu, mais cela permet également de mieux comprendre et contrôler la mise en page en CSS. 

## La propriété display

La propriété ```display``` permet de définir si et comment un élément HTML est affiché à l’écran. 

Chaque élément HTML dispose d’une valeur ```display``` par défaut, en fonction du type d’élément. Pour la plupart des éléments HTML, la valeur par défaut attribuée à la propriété ```display``` est ```block``` ou ```inline```. 

## Les éléments “block-level”

Un élément HTML dit “block-level” (donc disposant de la propriété CSS “display: block;”) commence toujours sur une nouvelle ligne et prend toute la largeur disponible. Cela signifie que l’élément est étiré de la gauche vers la droite, tant qu’il reste de la place. 

Les éléments ```block``` ont la possibilité de se voir attribuer une largeur définie et fixe.

Voici une liste non exhaustive d’éléments courants en HTML de type “block-level” :

- ```<div>```
- titres ```<h1>``` à ```<h6>```
- ```<p>```
- ```<form>```
- ```<header>```
- ```<footer>```
- ```<section>```

## Les éléments “inline level”

Les éléments HTML dits “inline level” (disposant de la propriété CSS ```display: inline;```) est un élément qui ne commence pas sur une nouvelle ligne - autrement dit, il continue sur la ligne en cours - et prend seulement la largeur nécessaire à l’affichage de son contenu. 

Contrairement aux éléments block, les éléments inline ne peuvent pas avoir de largeur fixe définie, celle-ci n’étant pas prise en compte.

Ci-dessous, une liste non exhaustive d’éléments courants en HTML de type “inline level” :

- ```<img>```
- ```<a>```
- ```<span>```

## La valeur none

Lorsque la propriété CSS display reçoit la valeur none, l’élément concerné n’est plus affiché sur la page web et les autres éléments de la page prennent la place de l’élément concerné.

## Inline-block

La propriété display peut également recevoir la valeur ```inline-block```. Cette valeur agit de la même manière que ```inline```, mais laisse néanmoins la possibilité au développeur d’agir sur la largeur de l’élément.

Exemple : 

```css
span {
	display: inline-block;
	width: 100px; /* Grâce à la valeur inline-block envoyée à la propriété display, l'élément peut avoir une largeur définie (ce qui n'est pas possible avec la valeur inline seule) */
}
```

## La valeur flex

Cette valeur est évoquée plus en détails dans le cours sur flexbox. 

Lorsque cette valeur est donnée à display, les éléments sont automatiquement affichés les uns à côté des autres, comme des inline. Il existe d’autres propriétés propres à flexbox pour modifier, par la suite, ces valeurs d’affichage. Ces propriétés sont évoquées dans le cours sur flexbox.

Exemple :

```css
div img {
	display: flex; /* Les image contenues dans la div sont affichées les unes à côté des autres */
}
```

## La valeur grid

La valeur grid (*grille*, en anglais), permet de concevoir la page web comme une grille qui, comme un tableau, est divisée en lignes et en colonnes. Cependant, grid permet aux éléments de se chevaucher entre eux, tandis qu’un tableau ne le peut pas. 

Un cours entier est dédié à la mise en page par grille (grid layout).

Exemple :

```css
h1 {
	display: grid;
}
```

## Changer la valeur par défaut de display

Chaque élément a une valeur de display par défaut - ```block``` ou ```inline```. Cependant, le langage CSS permet de changer cette valeur. En effet, changer un élément ```block``` en ```inline```, et inversement, peut être utile pour modifier le design d’une page web tout en respectant les standards du web.

__Remarque__ : Changer la valeur ```display``` d’un élément modifie *seulement la manière dont l’élément concerné est affiché* (en ```block``` ou en ```inline```), *cela ne change pas le type d’élément et ne change pas non plus les autres éléments du même type*.

Exemple avec un élément span :

```css
{
    display: block; /* Ici, l'élément <span> est affiché en block */
}
```

## Cacher un élément

Cacher un élément HTML, en CSS, peut se faire de 2 manières différentes :

- En attribuant la valeur ```none``` à la propriété ```display```. Cela permet de **cacher l’élément** et le reste de la page est affiché **comme si l’élément n’existait pas**. 
- En utilisant la propriété ```visibility``` et en lui attribuant la valeur ```hidden``` (*caché*, en anglais). Cela permet de cacher l’élément HTML, mais **l’élément garde le même espace que lorsqu’il est affiché**. 

__Remarque__ : Avec ces deux possibilités, l’élément est caché, c'est-à-dire qu’il n’est pas affiché sur la page web. Cependant, **le code HTML reste présent**, donc **disponible en cas d’inspection du code source par l’utilisateur**.

Exemple en utilisant la propriété ```display``` :

```css
h1 {
	display : none;
}
```

Exemple utilisant la propriété ```visibility``` :

```css
.title {
	visibility: hidden;
}
```