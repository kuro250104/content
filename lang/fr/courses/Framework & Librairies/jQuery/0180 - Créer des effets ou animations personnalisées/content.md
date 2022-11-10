Dans ce nouveau cours, nous allons apprendre à créer des effets personnalisés ou des "animations" en utilisant la méthode jQuery animate().

## Présentation de la méthode jQuery animate() et limitations

La méthode ```animate()``` nous permettra de créer des effets ou des animations sur n'importe quelle propriété CSS numérique. Nous lui passons les propriétés que nous voulons animer comme paramètres obligatoires.

Ensuite, nous pouvons également lui transmettre la durée de l'animation en millisecondes, la fonction d'accélérateur (vitesse de l’animation, swing : plus lentement au début / à la fin, mais plus rapidement au milieu par défaut ou linear : vitesse constante) et la fonction de rappel à exécuter après la fin de l'animation, il s’agit ici d’une fonction qui sera exécutée une fois que l’animation sera terminée, aussi appelée callback, en paramètres optionnels.

Tout d'abord, veuillez noter que vous ne pourrez pas utiliser l'animation à tout moment, n'importe où. Tout d'abord, vous devez savoir que la plupart des propriétés CSS non numériques ne peuvent pas être animées avec ```animate()``` en utilisant jQuery (jQuery sans extension spécifique).

Par exemple, sauf si vous utilisez l'extension jQuery.color, vous ne pouvez pas utiliser ```animate()``` pour animer les propriétés CSS liées aux couleurs.

Vous devez également connaître la notation abrégée des propriétés CSS, telles que les polices, les bordures, etc. ```animate()``` n'est pas bien prise en charge. Par conséquent, lorsque nous voulons les animer, nous aimons toujours utiliser la version complète de ces propriétés.

## Exemples d’utilisation de jQuery animate()

Nous pourrons animer une ou plusieurs propriétés CSS en utilisant ```animate()```. Commençons par animer les propriétés CSS individuelles. Par exemple, nous pouvons animer les propriétés width, height et font-size des éléments un par un.

```html
<body>
    <h1>Titre principal</h1>
    <button id="button1">animate width</button>
    <button id="button2">animate height</button>
    <button id="button3">animate font-size</button>
</body>
```

```js
$(document).ready(function(){
    $("#button1").click(function () {
        //Diminue la largeur de h1 de 20% sur 1 seconde 
        $("h1").animate({ width: "-=20%" }, 1000);
    });

    $("#button2").click(function () {
        //Fait passer la hauteurà 0 si elle n'est pas à 0 ou la rétablit
        $("h1").animate({ height: "toggle" });
    });

    $("#button3").click(function () {
        //Passe la taille de police à 20px sur 2 secondes
        $("h1").animate({ fontSize: "20px" }, 2000);
    });
});
```

Au lieu d'animer les propriétés CSS une à une indépendamment les unes des autres, nous pouvons également les animer en même temps en passant plusieurs propriétés en tant que paramètres à ```animate()```. Pour cela, nous utiliserons la syntaxe suivante :

```html
<body>
    <h1>Titre principal</h1>
    <button id="button1">animate</button>
</body>
```

```js
$(document).ready(function(){
    $("h1").animate({
        //Diminue la largeur de h1 de 20% sur 1 seconde 
        //Fait passer la hauteurà 0 si elle n'est pas à 0 ou la rétablit
        //Passe la taille de police à 20px sur 2 secondes
        width: "-=20%", height: "toggle", fontSize: "20px"
    }, 1000);
});
```

## La file d’attente ou queue des animations

Dans l'exemple précédent, nous avons fourni plusieurs propriétés CSS pour la méthode ```animate()```. Dans ce cas, lorsque nous cliquons sur le bouton, différentes propriétés commencent à s'animer en même temps.

Si nous changeons pour lier à tour de rôle différentes méthodes d'animation, que va-t-il se passer maintenant ? Dans ce cas, ces méthodes seront exécutées l'une après l'autre : chaque méthode attendra que la méthode précédente ait terminé son travail.

```html
<body>
    <h1>Titre principal</h1>
    <button id="button1">animate</button>
</body>
```

```js
$(document).ready(function(){
    //On chaine les méthodes; les animations se font dans l'ordre d'écriture
    $("#button1").click(function () {
        $("h1")
        //Diminue la largeur de h1 de 20% sur 5 secondes
            .animate({ width: "-=20%" }, 5000)
            //Passe la taille de police à 20px sur 2 secondes
            .animate({ fontSize: "20px" }, 2000)
            //Attends 0.5 d'opacité en 2 secondes
            .fadeTo(2000, 0.5);
    });
});
```