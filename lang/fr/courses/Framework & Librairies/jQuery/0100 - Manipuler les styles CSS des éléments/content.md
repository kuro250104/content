## Introduction

jQuery dispose de plusieurs méthodes qui permettent de manipuler le CSS des éléments composants une page web.

## La méthode css()

JQuery permet d’utiliser une méthode nommée ```css()``` de deux manières différentes : soit en tant que “getter” pour obtenir la valeur liée à une propriété CSS d’un élément, soit en tant que “setter” pour définir une propriété CSS ainsi que sa valeur pour un élément sélectionné.

Afin d’obtenir la valeur d’une propriété CSS liée à la sélection, il faut spécifier ladite propriété recherchée en argument.

Pour définir la valeur d’une propriété pour une sélection, il faut passer deux arguments à la méthode ```css()``` : les attributs CSS souhaités ainsi que leurs valeurs.

Enfin, pour définir plusieurs attributs et valeurs à une sélection d'éléments en une seule fois, il est possible de passer un objet javascript en argument en respectant la syntaxe suivante : ```css({"prop1: value", "prop2: value"})```.

```html
<!-- Code HTML initial -->
<body>
    <button id="button1">Changer la police</button>
    <p>Famille de polices actuellement utilisée : <span id="font"></span></p>
    <div>
        <p>Un premier paragraphe</p>
        <p>Un deuxième paragraphe</p>
    </div>
</body>
```

```js
$(document).ready(function(){
    // Récupération de la police d’écriture
    let font = $("body").css("font-family");
    // Écriture du nom de la police dans la balise possédant
    // l'identifiant “font”
    $("#font").text(font);
    $("#button1").click(function () {
        //Lors du clic sur le bouton change la police d'écriture
        $("body").css("font-family", "Nunito, Futura, Verdana");
        //Met à jour la valeur du span
        font = $("body").css("font-family");
        $("#font").text(font);
    });
});
```

```html
<!-- Code HTML après un clic sur le bouton -->
<body style="font-family: Nunito, Futura, Verdana;">
    <button id="button1">Changer la police</button>
    <p>Famille de polices actuellement utilisée : <span id="font">Nunito, Futura, Verdana</span></p>
    <div>
        <p>Un premier paragraphe</p>
        <p>Un deuxième paragraphe</p>
    </div>
</body>
```

## Les méthodes liées aux dimensions des éléments

JQuery fournit également une série de méthodes qui permettent d'obtenir ou de définir la largeur et la hauteur d'un élément.

La méthode ```width()``` permet d'obtenir la largeur du premier élément de la sélection, ou de définir cette largeur pour tous les éléments de la sélection en passant la largeur (en pixel) comme argument sans préciser l’unité.

La méthode ```innerWidth()``` permet d'obtenir la largeur de l’élément et le padding du premier élément de la sélection, ou de définir la largeur des éléments de la sélection. Cette largeur est définie sans unité, mais toujours exprimée en pixel.

La méthode ```outerWidth()``` permet d'obtenir la largeur, le padding et la bordure du premier élément de la sélection, ou de définir cette largeur en pixel pour tous les éléments de la sélection en la passant en argument.

```html
<!-- Code HTML initial -->
<body>
    <div>
        <p>Un premier paragraphe</p>
        <p>Un deuxième paragraphe</p>
    </div>
    <p id="text">Troisième paragraphe hors div</p>
    <p>Largeur avec css() : <span id="css"></span></p>
    <p>Largeur avec width() : <span id="width"></span></p>
</body>
```

```js
// Code jQuery s'exécutant dès que le DOM est prêt
$(document).ready(function(){
    // récupération de la taille de l'élément "div" avec la méthode css()
    let largeurCss = $("div").css("width");
    // récupération de la taille de l'élément "div" avec la méthode width()
    let largeurWidth = $("div").width();

    // affichage de la variable "largeurCss" dans l'élément possédant
    // l'identifiant "css"
    $("#css").text(largeurCss);
    // affichage de la variable "largeurWidth" dans l'élément possédant
    // l'identifiant "width"
    $("#width").text(largeurWidth);
});
```

Après exécution : 

```html
<!-- Code HTML après exécution du jQuery -->
<body>
    <div>
        <p>Un premier paragraphe</p>
        <p>Un deuxième paragraphe</p>
    </div>
    <p id="text">Troisième paragraphe hors div</p>
    <p>Largeur avec css() : <span id="css">1359px</span></p>
    <p>Largeur avec width() : <span id="width">1359</span></p>
</body>
```

## Les méthodes offset() et position()

La méthode ```offset()``` permet de récupérer la position du premier élément sélectionné ou de redéfinir la position de tous les éléments sélectionnés par rapport au document. Pour être plus précis, la position récupérée ou définie par ```offset()``` sera la position du coin supérieur gauche de l'élément.

Cette méthode retourne un objet contenant deux attributs “top” et “left”, qui contiennent les coordonnées de l'élément par rapport aux bords supérieur et gauche du document.

La méthode ```position()``` permet également de récupérer la position actuelle d’un élément, mais contrairement à ```offset()```, elle sera calculée par rapport à la position du premier objet parent positionné de l'élément (donc le premier bloc parent disposant d’une propriété css “position”). La position récupérée sera la position du coin supérieur gauche incluant la marge extérieur de l'élément sélectionné par rapport à la marge intérieur de l'élément parent positionné.

Deux attributs “top” et “left” sont également retournés, de la même manière que pour la méthode ```offset()```.

```html
<!-- Code HTML de base -->
<body>
    <h1>Cours jQuery</h1>
    <div id="div1" style="position:relative">
        <p>Un premier paragraphe</p>
        <p>Un deuxième paragraphe avec un <span id="span1">span</span></p>
    </div>
    <p id="p3">Troisième paragraphe hors div</p>
    <span id="resultat"></span>
</body>
```

```js
$(document).ready(function () {
    // récupération de l'offset de la balise <h1>
    let h1off = $("h1").offset();
    // récupération de l'offset de l'élément possédant l'identifiant
    // "div1"
    let div1off = $("#div1").offset();
    // récupération de l'offset de l'élément possédant l'identifiant
    // "span1"
    let span1off = $("#span1").offset();
    // récupération de la position de l'élément possédant l'identifiant
    // "span1"
    let span1pos = $("#span1").position();
    // définition de l'offset de l'élément possédant l'identifiant
    // "p1" à 150px du haut du document, et à 100px à gauche du 
    // document
    $("#p1").offset({ top: 150, left: 100 });

    let res = document.getElementById("resultat");
    // affichage des valeurs récupérées dans le HTML
    res.innerHTML =
        "Offset h1 (gauche, haut) : " + h1off.left + ", " + h1off.top +
        "<br>Offset div1 : " + div1off.left + ", " + div1off.top +
        "<br>Offset span1 : " + span1off.left + ", " + span1off.top +
        "<br>Position span1 : " + span1pos.left + ", " + span1pos.top;
});
```

Après exécution : 

```html
<!-- Code HTML après exécution du jQuery -->
<body>
    <h1>Cours jQuery</h1>
    <div id="div1" style="position:relative">
        <p>Un premier paragraphe</p>
        <p>Un deuxième paragraphe avec un <span id="span1">span</span></p>
    </div>
    <p id="p3">Troisième paragraphe hors div</p>
    <span id="resultat">Offset h1 (gauche, haut) : 8, 21.4375<br>Offset div1 : 8, 79.875<br>Offset span1 : 226.125,
        113.875<br>Position span1 : 218.125, 34</span>
</body>
```