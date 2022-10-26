En CSS, les propriétés d’arrière-plan (*background*, en anglais), sont utilisées afin de styliser les éléments HTML. Ce cours détaillera les différentes propriétés CSS d’arrière-plan. 

## Définir la couleur d’arrière-plan

Pour définir la couleur d'arrière-plan d’un élément HTML, il suffit d’utiliser la propriété ```background-color```.
L’exemple ci-dessous montre comment utiliser cette propriété afin de changer la couleur d’arrière-plan d’un titre ```h1``` :

```css
h1 {
    background-color : blue;
}
```

Cette propriété s’applique à n’importe quel élément HTML, aussi bien une ```<div>```, qu’un ```<p>```, par exemple. Elle s'utilise exactement comme montré dans l’exemple ci-dessus.

### L’opacité

Le CSS permet également de changer l’opacité/la transparence de la couleur de fond. Pour ce faire, la propriété ```opacity``` est utilisée. 

Pour changer l’opacité d’une couleur de fond, il suffit de spécifier une valeur entre 0.0 et 1.0. 0.0 étant une transparence totale et 1.0, une opacité totale. 

Exemple :

```css
h1 {
    background-color : blue;
    opacity : 0.5; /* Ici, la couleur sera transparente de 50 % et opaque à 50 % */
}
```

__Remarque__ : 

- Pour la virgule, en CSS, il faut utiliser la notation anglo-saxonne. Ainsi, pour attribuer un chiffre à virgule à une propriété CSS, il suffit de remplacer la virgule par le point. 
- Lorsque la propriété ```opacity``` est utilisée afin de rendre transparent l’arrière-plan d’un élément, **tous les éléments enfants hériteront aussi de cette opacité**. Cela peut donc rendre le texte au sein de cet élément si transparent qu’il en deviendrait illisible.

## Changer l’image d’arrière-plan

Le CSS rend possible d’ajouter ou de changer l’image d’arrière-plan d’un élément HTML. Pour ce faire, le CSS utilise la propriété ```background-image```.

__Remarque__ : Par défaut, l’image d’arrière-plan sera répétée afin de couvrir l’ensemble de l’arrière-plan de l’élément. 

L’exemple ci-dessous montre l’utilisation de la propriété ```background-image``` pour changer l’image d’arrière-plan d’un titre ```h1``` :

Dans l’exemple ci-dessus, le titre ```h1``` se verra attribuer l’image “image.jpg” en arrière-plan.

Attention de bien utiliser ```url()``` avant d’écrire le nom de l’image, sinon ce bout de code ne sera pas interprété et le titre apparaîtra sans image d'arrière-plan. Attention également à bien entourer le nom de l’image par des guillemets, sinon, encore une fois, le code ne fonctionnera pas.

## La répétition de l’arrière-plan

### La propriété background-repeat

Comme précisé dans le point précédent, par défaut, une image d’arrière-plan est répétée à la fois verticalement et horizontalement. 

Cependant, le CSS rend possible le fait de répéter une image seulement verticalement ou seulement horizontalement. Pour ce faire, le CSS utilise la propriété ```background-repeat```.

Exemple :

```css
h1 {
    background-image : url("degrade_titre.jpg");
    background-repeat : repeat-x;
}
```

Dans l’exemple ci-dessus, l’image “degrade_titre” sera répétée horizontalement, grâce à la valeur ```repeat-x```. Si l’image devait être répétée verticalement, la valeur ```background-repeat : repeat-y``` aurait été utilisée à la place.

### La propriété background-repeat : no-repeat

Le CSS permet également de ne pas répéter une image d’arrière. Pour faire cela, il faut ajouter la valeur ```no-repeat``` à la propriété ```background-repeat```.

Exemple : 

```css
body {
    background-image : url("image.jpg");
    background-repeat : no-repeat; /* L'image d'arrière-plan ne sera pas répétée */
}
```

### La propriété background-position

Lorsqu’une image de fond est utilisée, celle-ci est, par défaut, placée au même endroit que le texte. Le CSS permet de changer cela, grâce à la propriété background-position. 

Cette propriété permet de changer la position de l’image d'arrière-plan. Son utilisation est simple : il suffit de lui donner une valeur précisant l’endroit où l’image doit être placée.

Exemple :

```css
body {
    background-image : url("ski.jpg");
    background-repeat : no-repeat;
    background-position : right top; /* Ici, l'image sera placée en haut à droite du corps de la page */
}
```

## Fixer l’image d’arrière-plan

Le CSS utilise une propriété permettant soit de faire défiler (scroll) l’image d’arrière-plan avec le reste de la page, soit de fixer l’image (c'est-à-dire qu’elle ne défilera pas en même temps que le texte).

Cette propriété est la suivante : ```background-attachment```. Cette propriété prend soit la valeur scroll, si l’image doit défiler en même temps que le texte, soit la valeur ```fixed```, si l’image doit rester fixée. 

Exemple :

```css
body {
    background-image : url("ski.jpg");
    background-repeat : no-repeat;
    background-position : right top;
    background-attachment : fixed /* Ici, l'image restera fixée. Elle ne défilera pas en même temps que le texte. */
}
```

## La propriété raccourcie

Dans les points précédents, beaucoup de lignes de code sont écrites et beaucoup de propriétés sont utilisées simplement pour un arrière-plan. 

Le CSS permet d’écrire tout cela en une seule ligne, en utilisant la propriété ```background```.

Dans l’exemple suivant, toutes les propriétés sont utilisées : 

```css
body {
    background-color : red;
    background-image : url("ski.jpg");
    background-repeat : no-repeat;
    background-position : right top;
    background-attachment : fixed
}
```

Voici maintenant le même code, raccourcie, cette fois, grâce à la propriété ```background``` :

```css
body {
    background : red url("ski.jpg") no-repeat right top fixed;
}
```

__Remarque__ : Lorsque la propriété raccourcie est utilisée, il est primordial que les valeurs des propriétés soient dans l’ordre suivant :

- ```background-color```
- ```background-image```
- ```background-repeat```
- ```background-position```
- ```background-fixed```

Cependant, si une des propriétés ci-dessus n’a pas besoin d’être utilisée, il suffit de ne pas lui donner de valeur dans la propriété ```background```. 