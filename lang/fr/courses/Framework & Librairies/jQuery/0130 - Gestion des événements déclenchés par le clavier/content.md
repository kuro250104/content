## Introduction

Tout comme jQuery permet de gérer les événements déclenchés par la souris, il permet également de gérer les événements liés au clavier, tels que l’appui sur une touche, son relâchement, etc...

## Les méthodes keydown() et keyup()

La méthode ```keydown()``` permet de gérer les événements liés à l’appuie d’une touche sur le clavier. Si la touche maintenue enfoncée, l'événement sera renvoyé chaque fois que le système d'exploitation prendra en compte la répétition de la touche.

À l’inverse, la méthode ```keyup()``` permet de gérer les événements de relâchement d’une touche clavier.

Chacune de ces méthodes prend en argument une fonction, dans laquelle il est généralement passé un argument “event”, qui permet d'interagir avec l’événement déclenché, et donc par exemple de récupérer le nom de la touche clavier qui est déclenchée.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <label for="texte">Ecrivez dans le champ : </label>
    <input type="text" id="texte">
    <p>Code de la dernière touche pressée : <span></span></p>
</body>
```

```js
$(document).ready(function(){
    // Change la couleur de fond du champ en bleu dès qu'une touche est 
    // pressée et affiche le code de la dernière touche pressée
    $("#texte").keydown(function (event) {
        $(this).css("background-color", "red");
        $("span").text(event.which);
    });

    /* Avec on()
    $("#texte").on('keydown', function(event) {
        $(this).css("background-color", "red");
        $("span").text(event.which);
    });
    */

    // Change la couleur de fond du champ en jaune dès qu'une touche est 
    // pressée
    $("#texte").keyup(function () {
        $(this).css("background-color", "orange");
    });

    /* Avec on()
    $("#texte").on('keyup', function() {
        $(this).css("background-color", "orange");
    });
    */
});
```

## La méthode keypress()

La méthode ```keypress()``` est similaire à ```keydown()```, puisqu’elle enregistre un événement lors de l’appuie sur une touche clavier. Les différences notoires sont : 

- ```keypress()``` ne se déclenche que lorsqu’une touche de caractère est déclenchée. Ainsi l’appuie sur les touches “Ctrl”, “alt”, (etc…) ne sont pas pris en compte par cette méthode.
- ```keypress()``` ne se déclenche qu’une seule fois par appuis sur une touche. Ainsi si une touche clavier prise en compte par ```keypress()``` est maintenue enfoncée, un seul événement sera déclenché.

L’événement ```keypress()``` renvoie en retour d’exécution le code ASCII correspondant au caractère déclencheur de l’événement.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <label for="texte">Ecrivez dans le champ : </label>
    <input type="text" id="texte">
    <p>Code caractère (keypress) : <span id="span1"></span></p>
    <p>Code touche (keydown) : <span id="span2"></span></p>
</body>
```

```js
$(document).ready(function(){
    // Renvoie le code ASCII dans l’élément possédant l’id “span1”
    $("#texte").keypress(function (event) {
        $("#span1").text(event.which);
    });

    /* Avec on()
    $("#texte").on('keypress', function(event) {
        $("#span1").text(event.which);
    });
    */

    // Renvoie le code lié à la touche dans le span2
    $("#texte").keydown(function (event) {
        $("#span2").text(event.which);
    });

    /* Avec on()
    $("#texte").on('keydown', function(event) {
        $("#span2").text(event.which);
    });
    */
});
```