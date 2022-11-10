Dans ce nouveau cours, nous examinerons les méthodes fournies par jQuery pour créer des effets de fondu et de slide.

## Créer des effets de fondu 

« Fondu » fait référence à la disparition progressive ou à l'apparition d'un élément. C'est donc l'effet de la transition d'un état à un autre. jQuery nous offre quatre façons de créer des effets de fondu :

- La méthode ```fadeOut()```
- La méthode ```fadeIn()```
- La méthode ```fadeTo()```
- La méthode ```fadeToggle()```

Ces méthodes utilisent en fait la valeur de l'attribut opacity de l'élément cible et augmenteront progressivement cette valeur de 1 à 0 (totalement opaque à totalement transparent), et vice versa. Une fois que l'opacité atteint 0, display: none; est appliqué pour le faire disparaître complètement de la page.

Plus précisément, la méthode ```fadeOut()``` permet de masquer l'élément cible en rendant l'élément cible progressivement transparent, tandis que la méthode ```fadeIn()``` aura l'effet inverse, qui est de montrer progressivement l'élément caché.

La méthode ```fadeToggle()``` permet d'inverser la visibilité des éléments en faisant apparaître progressivement des éléments initialement cachés, ou à l'inverse, en faisant progressivement disparaître les éléments initialement opaques avec un effet de fondu.

Enfin, la méthode ```fadeTo()``` permet de définir le niveau de seuil d'opacité (entre 0 et 1) que l'élément doit atteindre progressivement. Si l'élément est initialement plus transparent que ce niveau, il deviendra progressivement trouble et vice versa.

Il est possible de passer jusqu'à trois paramètres aux méthodes ```fadeOut()```, ```fadeIn()``` et ```fadeToggle()``` : la durée de la transition, la fonction d'accélération qui doit être utilisée pour effectuer la transition, et la fonction de rappel à exécuter une fois la conversion terminée. En ajoutant le niveau d'opacité comme deuxième paramètre, la méthode ```fadeTo()``` prendra en charge jusqu'à 4 paramètres.

Concernant la durée de la transition, nous pourrons spécifier le nombre de millisecondes que l'effet doit durer, ou utiliser les mots clés slow ou fast.

En ce qui concerne la fonction d'accélération qui doit être utilisée pour obtenir l'effet, jQuery ne prend en charge que le swing et le linéaire par défaut, ce qui crée une transition en douceur.

```html
<body>
    <h1>Titre principal</h1>
    <button id="button1">fadeOut()</button>
    <button id="button2">fadeIn()</button>
    <button id="button3">fadeToggle()</button>
    <button id="button4">fadeTo()</button>
</body>
```

```js
$(document).ready(function(){
    $("#button1").click(function () {
        //Disparition du titre en 400ms
        $("h1").fadeOut();
    });

    $("#button2").click(function () {
        //Apparition du titre en 2 secondes
        $("h1").fadeIn(2000);
    });

    $("#button3").click(function () {
        //Inversion de l'état de visibilité de h1 avec un effet de fondu
        //Apparition du titre en 2 secondes 
        $("h1").fadeToggle(2000);
    });

    $("#button4").click(function () {
        //Fondu jusqu'à un certain niveau d'opacité, 0.3
        $("h1").fadeTo(2000, 0.3);
    });
});
```

## Créer des effets de slide en jQuery

jQuery fournit également des méthodes pour créer des effets de slides. Ici, «slide» fait référence au fait qu'un élément est progressivement déployé ou progressivement plié. Par exemple, cet effet peut être intéressant lors de la création d'un menu déroulant.

Pour créer cet effet, nous pouvons choisir parmi les trois méthodes suivantes :

- La méthode ```slideDown()```
- La méthode ```slideUp()```
- La méthode ```slideToggle()```

La méthode ```slideDown()``` permet de "développer" progressivement un élément, tandis que la méthode ```slideUp()``` aura l'effet inverse et permet de "plier" progressivement un élément.

La méthode ```slideToggle()``` permet d'agrandir progressivement les éléments réduits, ou inversement, de développer progressivement les éléments développés.

Ces trois méthodes peuvent accepter jusqu'à trois paramètres, qui sont du même type que les méthodes précédentes : durée, fonction d'accélération et fonction de rappel qui seront exécutées à la fin de l'effet.

```html
<body>
    <h1>Titre principal</h1>
    <button id="button1">slideUp()</button>
    <button id="button2">slideDown()</button>
    <button id="button3">slideToggle()</button>
</body>
```

```js
$(document).ready(function(){
    $("#button1").click(function () {
        //Replie le titre en 400ms
        $("h1").slideUp();
    });

    $("#button2").click(function () {
        //Déplie le titre en 2 secondes
        $("h1").slideDown(2000);
    });

    $("#button3").click(function () {
        //Déplie le titre s'il est plié ou le plie s'il est déplié
        $("h1").slideToggle(2000);
    });
});
```