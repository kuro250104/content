Le module Flexbox Layout (boîte flexible) (une recommandation candidate du W3C en octobre 2017) vise à fournir un moyen plus efficace de disposer, d'aligner et de répartir l'espace entre les éléments d'un conteneur, même lorsque leur taille est inconnue et/ou dynamique (d'où le mot "flex").

L'idée principale de la mise en page flexible est de donner au conteneur la possibilité de modifier la largeur/hauteur (et l'ordre) de ses éléments pour remplir au mieux l'espace disponible (principalement pour s'adapter à tous les types de dispositifs d'affichage et de tailles d'écran). Un conteneur flexible étend les éléments pour remplir l'espace libre disponible ou les rétrécit pour éviter tout débordement.

## Container / Items

Le Flexbox est relativement simple à comprendre, si l'on pose correctement les bases. Un élément devient un **container** (*conteneur* en français) à partir du moment où sa propriété ```display```prend pour valeur ```flex```. Dans le même temps, l'ensemble des éléments HTML étant des ***enfants directs*** du **container** sont considérés comme des **items** (*éléments* en français).

D'après l'exemple suivant : 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container {
            display: flex;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item div1">
            <p>Ma phrase 1</p>
        </div>
        <div class="item div2">
            <p>Ma phrase 2</p>
        </div>
        <div class="item div3">
            <div class="normal sousdiv1">
                <p>Ma phrase 3</p>
            </div>
            <div class="normal sousdiv2">
                <p>Ma phrase 4</p>
            </div>
        </div>
        <div class="item div4">
            <p>Ma phrase 4</p>
        </div>
    </div>
</body>
</html>
```

Quelques explications sur le code ci-dessus : 

- un ```display: flex```est appliqué en CSS à la classe ```.container```.
- la ```<div class="container">``` est donc devenue un **container** flex. C'est la seule ```<div>``` du code à en être un.
- les ```<div>``` 1, 2, 3 & 4 sont des enfants directs du **container**, ils sont donc devenus des **items** flex.
- les ```<div class="normal sousdiv1">``` et ```<div class="normal sousdiv2">``` sont des divs normales : elles ne sont ni des **container**, ni des **items**.

Il est **primordial** de bien faire le distinguo entre les **containers** et les **items**. Certaines propriétés devront s'appliquer sur les **containers**, tandis que d'autres devront s'appliquer sur les **items**. Dans les deux cas de figure, les effets de positionnement seront produits sur les **items**, et non sur les **containers** !

Il est important de noter que la majorité des effets applicables sur les **containers** sont suffisant pour positionner l'ensemble des **items**, y compris pour la gestion du resonsive. De la sorte, il est important de réaliser les positionnements d'abords en jouant avec les **containers**, avant d'influer sur les **items** en dernier recours.

__remarque__ : Un item est un enfant direct d'un **container**, mais il peut cumuler les deux statuts et devenir lui-même un **container** (en plus d'un **item**) si la propriété ```display: flex;``` lui est appliqée.

## Propriétés des containers

### flex-direction

Cela établit l'axe horizontal, définissant ainsi la direction dans laquelle les éléments flexibles sont placés dans le **container** flex. Flexbox est un concept de mise en page unidirectionnel. Pensez aux éléments flexibles comme étant principalement disposés soit en rangées horizontales, soit en colonnes verticales.

```css
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```

- ```row```  (*default*) : de gauche à droite en ltr; de droite à gauche en rtl
- ```row-reverse``` : de droite à gauche en ltr; de gauche à droite en rtl
- ```column``` : comme ```row```, mais de haut en bas
- ```column-reverse``` : comme ```row-reverse```, mais de bas en haut

### flex-wrap

Par défaut, les éléments flexibles essaieront tous de tenir sur une seule ligne. Vous pouvez changer cela et permettre aux éléments de s'enrouler selon les besoins avec cette propriété.

__remarque__ : une large partie du responsive peut être réaliser sans media query, uniquement grâce à cette propriété

```css
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

- ```nowrap``` (*default*) : tous les éléments flexibles seront sur une seule ligne
- ```wrap``` : les éléments flex s'enroulent sur plusieurs lignes, de haut en bas.
- ```wrap-reverse``` : les éléments flex s'enroulent sur plusieurs lignes, de bas en haut.

### flex-flow

Il s'agit d'un raccourci pour les propriétés ```flex-direction``` et ```flex-wrap```, qui définissent ensemble les axes principal et transversal du conteneur flex. La valeur par défaut est ```row nowrap```.

```css
.container {
  flex-flow: column wrap;
}
```

### justify-content

Ceci définit l'alignement le long de l'axe principal. Il permet de répartir l'espace libre restant lorsque tous les éléments flexibles d'une ligne sont inflexibles, ou sont flexibles mais ont atteint leur taille maximale. Il exerce également un certain contrôle sur l'alignement des éléments lorsqu'ils débordent de la ligne.

```css
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
```

- ```flex-start``` (*default*) : les **items** sont empaquetés vers le début de la direction de flex.
- ```flex-end``` : les **items** sont empaquetés vers la fin de la direction de flex.
- ```start``` : les **items** sont empaquetés vers le début de la direction du mode d'écriture.
- ```end``` : les **items** sont emballés vers la fin de la direction du mode d'écriture.
- ```left``` : les **items** sont emballés vers le bord gauche du **container**, sauf si cela n'a pas de sens avec la direction de flex, alors il se comporte comme ```start```.
- ```right``` : les **items** sont regroupés vers le bord droit du conteneur, sauf si cela n'a pas de sens avec la direction de flex, alors il se comporte comme le ```end```.
- ```center``` : les **items** sont centrés le long de la ligne
- ```space-between``` : les **items** sont répartis uniformément sur la ligne ; le premier élément est sur la ligne de départ, le dernier élément sur la ligne d'arrivée.
- ```space-around``` : les **items** sont répartis uniformément sur la ligne avec un espace égal autour d'eux. Notez que visuellement, les espaces ne sont pas égaux, puisque tous les éléments ont le même espace des deux côtés. Le premier élément aura une unité d'espace contre le bord du **container**, mais deux unités d'espace entre l'élément suivant parce que cet élément suivant a son propre espacement qui s'applique.
- ```space-evenly``` : les **items** sont répartis de manière à ce que l'espacement entre deux éléments (et l'espace par rapport aux bords) soit égal.

Il existe également deux mots-clés supplémentaires que vous pouvez associer à ces valeurs : ```safe``` et ```unsafe```. L'utilisation de ```safe``` garantit que, quelle que soit la manière dont vous effectuez ce type de positionnement, vous ne pouvez pas pousser un élément de telle sorte qu'il soit rendu hors de l'écran (par exemple, en haut) et que le contenu ne puisse pas être défilé (ce que l'on appelle "perte de données").


### align-items

Ceci définit le comportement par défaut pour la disposition des **items** le long de l'axe vertical sur la ligne actuelle.

```css
.container {
    align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
}
```

- ```stretch``` (*default*) : s'étire pour remplir le container (respecte toujours la largeur min/max)
- ```flex-start``` / ```start``` / ```self-start``` : les éléments sont placés au début de l'axe vertical. La différence entre les deux est subtile, et concerne le respect des règles de ```flex-direction``` ou des règles de mode d'écriture.
- ```flex-end``` / ```end``` / ```self-end``` : les éléments sont placés à la fin de l'axe vertical. Là encore, la différence est subtile et concerne le respect des règles de ```flex-direction``` par rapport aux règles du mode d'écriture.
- ```center``` : les éléments sont centrés sur l'axe vertical.
- ```baseline``` : les éléments sont alignés de manière à ce que leurs lignes de base soient alignées (c'est-à-dire le centre vertical de chaque bloc).

### align-content

Cette propriété permet d'aligner les lignes d'un **container** lorsqu'il y a un espace supplémentaire dans l'axe vertical, de la même manière que ```justify-content``` aligne les éléments individuels dans l'axe horizontal.

__remarque__ : cette propriété ne prend effet que sur les **container** multilignes, où ```flex-wrap``` est défini sur ```wrap``` ou ```wrap-reverse```). Un **container** à ligne unique (c'est-à-dire où ```flex-wrap``` est défini sur sa valeur par défaut, ```no-wrap```) ne reflétera pas ```align-content```.

```css
.container {
    align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}
```

- ```normal``` (*default*) : les **items** sont regroupés dans leur position par défaut, comme si aucune valeur n'avait été définie.
- ```flex-start``` / ```start``` : les **items** sont regroupés au début du **container**. Le ```flex-start``` (plus supporté) respecte la direction du **flex** tandis que le ```start``` respecte la direction du **mode d'écriture**.
- ```flex-end``` / ```end``` : les **items** sont regroupés à la fin du **container**. L'option (mieux supportée) ```flex-end``` respecte la direction **flex** tandis que ```end``` respecte la direction du **mode d'écriture**.
- ```center``` : les **items** sont centrés dans le **container**
- ```space-between``` : les **items** sont répartis uniformément ; la première ligne est au début du **container** tandis que la dernière est à la fin.
- ```space-around``` : les **items** sont répartis uniformément avec un espace égal autour de chaque ligne.
- ```space-evenly``` : les **items** sont répartis de manière égale avec un espace égal autour d'eux.
- ```stretch``` : les **items** s'étirent pour occuper l'espace disponible

### gap, row-gap, column-gap

La propriété ```gap``` contrôle explicitement l'espace entre les **items** du flex. Elle applique cet espace uniquement entre les éléments et non sur les bords extérieurs.

```css
.container {
    display: flex;
    gap: 10px;
    gap: 10px 20px; /* row-gap column gap */
    row-gap: 10px;
    column-gap: 20px;
}
```

Ce comportement pourrait être considéré comme une gouttière minimale, car si la gouttière est plus grande d'une manière ou d'une autre (à cause de quelque chose comme ```justify-content : space-between;```) alors l'écart ne prendra effet que si cet espace finit par être plus petit.

## Propriétés des items

__remarque__ : les propriétés qui concernent les **items** sont à appliquer en CSS **directement sur les items eux-même**, et non pas sur le **container** !

### order

Par défaut, les **items** sont disposés dans l'ordre de la source. Toutefois, la propriété ```order``` contrôle l'ordre dans lequel ils apparaissent dans le **container**.

```css
.item {
    order: 5; /* default is 0 */
}
```

__remarque__ : hormis pour certains cas exceptionnels, il est déconseillé de changer les ordre d'apparition des éléments HTML en CSS. Si vous êtes amenés à utiliser ce genre de propriété, questionnez vous bien avant sur la bonne utilisation ou non de votre HTML.



### flex-grow

Ce paramètre définit la capacité d'un **item** à croître si nécessaire. Il accepte une valeur sans unité qui sert de proportion. Elle dicte la quantité d'espace disponible à l'intérieur du **container** que l'élément doit occuper.

Si tous les éléments ont la valeur ```flex-grow``` définie sur 1, l'espace restant dans le conteneur sera distribué de manière égale à tous les enfants. Si l'un des enfants a une valeur de 2, il occupera deux fois plus d'espace que les autres (ou il essaiera, du moins).

```css
.item {
    flex-grow: 4; /* default 0 */
}
```

__remarque__ : les nombres négatifs ne sont pas valide.

### flex-shrink

Ceci définit la capacité d'un élément flexible à rétrécir si nécessaire.

```css
.item {
    flex-shrink: 3; /* default 1 */
}
```

__remarque__ : les nombres négatifs ne sont pas valide.

### flex-basis

Cette propriété définit la taille par défaut d'un élément avant que l'espace restant ne soit distribué. Il peut s'agir d'une longueur (par exemple, 20 %, 5rem, etc.) ou d'un mot clé. Le mot-clé ```auto``` signifie "regardez ma propriété largeur ou hauteur" (ce qui était temporairement fait par le mot-clé ```main-size``` jusqu'à ce qu'il soit déprécié). Le mot-clé ```content``` signifie "dimensionner en fonction du contenu de l'élément" - ce mot-clé n'est pas encore bien supporté, il est donc difficile de le tester et de savoir ce que font ses frères ```max-content```, ```min-content``` et ```fit-content```.

```css
.item {
    flex-basis:  | auto; /* default auto */
}
```

Si la valeur est ```0```, l'espace supplémentaire autour du contenu n'est pas pris en compte. S'il est défini sur ```auto```, l'espace supplémentaire est distribué en fonction de sa valeur ```flex-grow```.

### flex

Cette propriété est l'abréviation de ```flex-grow```, ```flex-shrink``` et ```flex-basis``` combinés. Les deuxième et troisième paramètres (```flex-shrink``` et ```flex-basis```) sont facultatifs. La valeur par défaut est ```0 1 auto```, mais si vous le définissez avec une seule valeur numérique, comme ```flex : 5;```, cela change la ```flex-basis``` à ```0%```, donc c'est comme définir ```flex-grow : 5; flex-shrink : 1; flex-basis : 0%;```.

```css
.item {
    flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```

### align-self

Cette propriété permet de remplacer l'alignement par défaut (ou celui spécifié par ```align-items```) pour les **items** de manière individuelle.

Les valeurs disponibles sont les mêmes que pour la propriété ```align-items```, vous pouvez donc vous y référer.

```css
.item {
    align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

Notez que ```float```, ```clear``` et ```vertical-align``` n'ont aucun effet sur un **item**.
