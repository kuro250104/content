## Introduction

JQuery dispose de plusieurs méthodes permettant de gérer les événements liés à la souris, parmi le clic, le survol, etc...

## Les méthodes click() et dblclick()

La méthode ```click()``` permet de gérer les événements de type “clic”, c'est-à-dire d'exécuter du code après un clic sur un élément.

La méthode ```dblclick()``` permet de gérer les événements de double-clic.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <div>
        <h2>Titre secondaire</h2>
        <p class="display">Je suis un paragraphe</p>
    </div>
</body>
```

```js
$(document).ready(function(){
    //Lors d'un clic sur le div
    $("div").click(function () {
        //On inverse les classes de p
        $("p").toggleClass("hide display");
        //Les éléments avec la classe hide seront cachés
        $(".hide").hide();
        //Les éléments avec la classe display seront visibles
        $(".display").show();
    });
    /* Il est possible de l'écrire avec on()
    $("div").on('click', function() {
        //On inverse les classes de p
        $("p").toggleClass("hide display");
        //Les éléments avec .hide seront cachés
        $(".hide").hide();
        //Les éléments avec .display seront visibles
        $(".display").show();
    });
    */

    //Lors d'un double clic sur le div
    $("div").dblclick(function () {
        // Une couleur de fond rouge est appliquée
        $(this).css("background-color", "red");
    });
    /* Il est possible de l'écrire avec on()
    $("div").on('dblclick', function() {
        //On lui applique une couleur de fond rouge
        $(this).css("background-color", "red");
    });
    */
});
```

## Les méthodes mouseenter(), mouseleave() et hover()

La méthode ```mouseenter()``` permet d'interagir avec l’événement de début de survol d’un élément. Il est déclenché lorsque la souris “entre” dans un élément, c'est-à-dire au moment précis où la souris commence son survol de l’élément. 

JQuery dispose d’une méthode similaire : ```mouseover()```. Celle-ci fonctionne de la même manière, à ceci près que les événements sont également déclenchés dès que la souris entre dans un élément enfant.

Ainsi ```mouseenter()``` est à utiliser dans le cas où un événement doit être déclenché lorsque la souris entre dans un élément, mais pas lorsqu’elle entre dans de potentiels éléments enfants. A contrario, si un événement doit être déclenché lors de l’entrée de la souris dans chaque élément : le cible ou un des enfants, alors il convient d’utiliser ```mouseover()```.

La méthode ```mouseleave()``` est l’inverse de ```mouseenter()``` : elle permet l’enregistrement d’événements se déclenchant lorsque la souris sort du survol d’un élément.

De la même manière, ```mouseout()``` dispose du même comportement que ```mouseover()```, mais ici encore non seulement lors de la sortie de la souris du survol d’un élément, mais aussi de ses éléments enfants.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <div>
        <h2>Titre secondaire</h2>
        <p class="display">Je suis un paragraphe</p>
    </div>
</body>
```

```js
$(document).ready(function(){
    // Lorsque la souris entre dans le div
    $("div").mouseenter(function () {
        //On ajoute une couleur de fond au div
        $(this).css("background-color", "red");
    });

    /* Avec on()
    $("div").on('mouseenter', function() {
        $(this).css("background-color", "red");
    });
    */

    // Lorsque la souris ressort du div
    $("div").mouseleave(function () {
        //On remet un fond blanc
        $(this).css("background-color", "#fff");
    });


    /* Avec on()
    $("div").on('mouseleave', function() {
        $(this).css("background-color", "#fff");
    });
    */
});
```

La méthode ```hover()``` regroupe à la fois le comportement de ```mouseenter()``` et de ```mouseleave()``` : le traitement de l’événement se fera en continu pendant que la souris survole l'élément.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <div>
        <h2>Titre secondaire</h2>
        <p class="display">Je suis un paragraphe</p>
    </div>
</body>
```

```js
$(document).ready(function(){
   $("div").hover(
        //Lorsque la souris entre dans la div ajoute un fond rouge
        function () { $(this).css("background-color", "red"); },
        //Lorsque la souris ressort de la div remet le fond blanc
        function () { $(this).css("background-color", "#fff"); }
    );
});
```

## Les méthodes mousedown() et mouseup()

Les méthodes jQuery ```mousedown()``` et ```mouseup()``` permettent respectivement de gérer les événements liés à l'appui du bouton de la souris sur un élément, puis à son relâchement.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <div>
        <h2>Titre secondaire</h2>
        <p class="display">Je suis un paragraphe</p>
    </div>
</body>
```

```js
$(document).ready(function(){
    //Lorsque le bouton de la souris est pressé au dessus du div
    $("div").mousedown(function () {
        //On change le fond en rouge
        $(this).css("background-color", "red");
    });

    /* Avec on()
    $("div").on('mousedown', function () {
        $(this).css("background-color", "red");
    });
    */

    //Lorsque le bouton de la souris est relâché
    $("div").mouseup(function () {
        //Le fond est blanc
        $(this).css("background-color", "#fff");
    });

    /* Avec on()
    $("div").on('mouseup', function () {
        $(this).css("background-color", "#fff");
    });
    */
});
```

## La méthode mousemove()

La méthode ```mousemove()``` permet d’interagir avec un les événements de déplacement de la souris. Par conséquent, cette méthode permet d'obtenir les coordonnées de la souris en temps réel en se basant toujours d’un point de départ.

Pour comprendre l'exemple suivant, vous devez d'abord savoir que lorsque vous enregistrez un événement dans le gestionnaire, un objet event est créé et lui est passé. Celui-ci à de nombreuses propriétés comme par exemple pageX et pageY qui renseignent la position de la souris par rapport aux coins supérieur haut et supérieur gauche du document.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <div>
        <h2>Titre secondaire</h2>
        <p class="display">Je suis un paragraphe</p>
    </div>
    <p>Position de la souris (X, Y): <span></span></p>
</body>
```

```js
$(document).ready(function(){
    /* Une référence à l'objet "event" est passée en argument de la méthode      
    mousemove() pour pouvoir utiliser ses propriétés */
    $("body").mousemove(function (event) {
        // Récupération de la position de la souris dans le document
        let pageCoords = "(" + event.pageX + ", " + event.pageY + ")";
        // Affichage de cette position dans une balise <p>
        $("p").text(pageCoords);
    });

    /* Avec on()
    $("body").on('mousemove', function(event) {
        let pageCoords = "(" + event.pageX + ", " + event.pageY + ")";
        $("p").text(pageCoords);
    });
    */
});
```