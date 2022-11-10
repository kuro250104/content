Dans ce nouveau cours, nous étudierons deux méthodes, elles permettent soit simplement d'afficher ou de masquer un élément immédiatement, soit de l'afficher ou de le masquer progressivement en combinant des effets de slide et de fondu.

## Afficher ou cacher un contenu instantanément avec show() et hide()

Les méthodes ```show()``` et ```hide()``` nous permettent respectivement d'afficher le contenu HTML masqué ou de masquer le contenu HTML visible.

Nous pouvons déjà utiliser ces méthodes sans paramètres pour afficher ou masquer les éléments immédiatement.

Dans la première utilisation la plus basique, les méthodes ```show()``` et ```hide()``` seront lues dans l'état de propriété d'affichage CSS de l'élément HTML cible. La propriété CSS display va voir son état changé entre display et none.

```html
<body>
    <h1>Titre principal</h1>
    <button id="button1">Cache</button>
    <button id="button2">Affiche</button>
</body>
```

```js
$(document).ready(function(){     
    $("#button1").click(function () {
        //Cache le titre h1
        $("h1").hide();
    });

    $("#button2").click(function () {
        //Affiche le titre h1
        $("h1").show();
    });
});
```

## Afficher ou cacher un contenu progressivement avec show() et hide()

Ensuite, nous pourrons passer les trois paramètres aux méthodes show() et hide() (et à d'autres méthodes de création d'effets).

Le premier paramètre correspond à la durée de l'animation. Nous pourrons spécifier la durée sous la forme d'un nombre correspondant au nombre de millisecondes que l'effet doit durer, ou utiliser les mots clés slow (600ms) ou fast (200ms) pour spécifier la durée.

Le deuxième paramètre correspond à la fonction d'accélération. Le but de la fonction d'accélération est de régler la vitesse de l'animation à différents points de l'animation. La fonction d'accélération par défaut est "swing", mais nous pouvons également passer la valeur linear pour que notre effet soit effectué à une vitesse constante.

Enfin, le troisième paramètre sera une fonction de rappel qui ne sera exécutée qu'une fois l'effet terminé.

```html
<body>
    <h1>Titre principal</h1>
    <button id="button1">Cache</button>
    <button id="button2">Affiche</button>
</body>
```

```js
$(document).ready(function(){     
    $("#button1").click(function () {
        //Cache le tritre h1 avec une vitesse progressive sur une durée
        //de 5 secondes
        $("h1").hide(5000, "linear", function () {
            alert("H1 caché");
        });
    });

    $("#button2").click(function () {
        //Affiche le titre h1
        $("h1").show();
    });
});
```

## Inverser l’état de visibilité d’un élément avec toggle()

La méthode ```toggle()``` nous permettra d'inverser l'état de visibilité de l'élément HTML, c'est-à-dire de l'afficher lorsqu'il est masqué ou de le masquer lorsqu'il est affiché.

Cette nouvelle méthode sera utilisée exactement comme la méthode précédente, soit sans paramètres, soit avec le même type de paramètres que ```show()``` et ```hide()```.

```html
<body>
    <h1>Titre principal</h1>
    <h2>Titre secondaire</h2>
    <button id="button1">toggle() h1</button>
    <button id="button2">toggle() h2</button>
</body>
```

```js
$(document).ready(function(){ 
    //Inverse l'état de visibilité de h1 lors d'un clic sur #button1  
    $("#button1").click(function () {
        $("h1").toggle();
    });

    //Inverse progressivement l'état de visibilité de h2 lors d'un 
    //clic sur #button2 en conservant la fonction d'accélération par défaut
    //et alert un message à la fin
    $("#button2").click(function () {
        $("h2").toggle(2000, function () {
            alert("Etat de visibilité changé");
        });
    });
});
```