## Introduction

JQuery propose différentes méthodes pour une gestion des événements avancée. Parmi celles-ci, la méthode ```on()``` déjà partiellement abordée, les méthodes ```trigger()```, ```triggerHandler()``` et ```off()``` permettent de déclencher ou de supprimer des événements. Quelques propriétés utiles de l’objet event permettent également de gérer des événements de manière plus poussée.

## La méthode on()

Dans le cas d'utilisation le plus simple, la syntaxe de la méthode ```on()``` est similaire à la méthode JavaScript addEventListener, car il est possible de transmettre le nom de l'événement en tant que premier argument pour un traitement, et transmettre une fonction de rappel (callback) à exécuter une fois que l'événement est déclenché en tant que deuxième argument.

```js
$(document).ready(function(){
    $("p").on("click", function(){
        $(this).hide();
    })
});
```

Le premier cas d'utilisation de ```on()``` est très simple. Cependant, l'utilisation de ```on()``` permet d'attacher plusieurs événements à un même élément en lui passant un argument sous forme d’objet javascript.

```html
<!-- Code HTML de base -->
<style>
    .rouge {
        background-color: red;
    }
</style>

<body>
    <h1>Titre principal</h1>
    <div>
        <p>Un paragraphe dans un div</p>
        <p>Un autre paragraphe dans un div</p>
    </div>
    <p id="text">Un paragraphe hors div</p>
</body>
```

```js
$(document).ready(function(){
    // Enregistrement d’un gestionnaire pour plusieurs événements pour un 
    // élément
    $("div").on("mouseenter mouseleave", function () {
        $(this).toggleClass("rouge");
    });

    // Enregistrement de plusieurs gestionnaires pour plusieurs événements     
    // pour un seul élément
    $("#text").on({
        // Si click, affiche “J'ai cliqué”
        click: function () {
            $(this).text("J'ai cliqué");
        },
        // Quand la souris est dans la zone, change le fond en noir
        mouseenter: function () {
            $(this).css("background-color", "black"); 
        },
        //”Quant la souris sort de la zone, change le fond en blanc
        mouseleave: function () {
            $(this).css("background-color", "white");
        }
    });
});
```

## Déclencher un événement avec trigger() et triggerHandler()

Les méthodes jQuery ```trigger()``` et ```triggerHandler()``` permettent de déclencher des événements "manuellement" en passant le nom de l’événement en argument.

Contrairement à ```trigger()```, la méthode ```triggerHandler()``` ne déclenche pas l'action par défaut de l’élément, il se contente de déclencher l’événement lié. Par exemple, ```triggerHandler("submit")``` n’engendre pas la soumission d’un formulaire.

```trigger()``` affecte tous les éléments avec des caractéristiques cibles, tandis que ```triggerHandler()``` n'affecte que le premier élément cible rencontré.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <input type="text" placeholder="Je veux le focus" id="focus">
    <button id="button1">trigger("focus")</button>
    <button id="button2">triggerHandler("focus")</button>
    <span id="message"></span>
</body>
```

```js
$(document).ready(function(){           
    // trigger() s'exécute lors du clic sur le bouton #button1. Ainsi le 
    // focus est mis sur l’élément “#focus”
    $('#button1').click(function () {
        $('#focus').trigger('focus');
    });

    // triggerHandler() s'exécute. Excute le gestionnaire d'evenement
    // de l'evenement declenche mais ne declenche pas l'action de
    // l'evenement
    $('#button2').click(function () {
        $('#focus').triggerHandler('focus');
    });

    // On attache un gestionnaire d'évènement focus à notre input
    $('#focus').focus(function () {
        $('#message').text('Evènement focus déclenché');
    })
});
```

## Supprimer des gestionnaires d’événements avec off()

La méthode jQuery ```off()``` permet de supprimer un événement attaché. L’utilisation de cette méthode peut nécessiter l’utilisation d'arguments : si une valeur d’événement est passée en argument, alors seulement celui-ci est supprimé. Si aucune valeur n’est passée, alors l’ensemble des événements attachés à l’élément seront supprimés.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <button id="button1">Pas de clic possible</button>
    <button id="button2">Ajout de gestionnaire d'event click</button>
    <button id="button3">Suppr de gestionnaire d'event click</button>
    <span id="message">Bouton cliqué</span>
</body>
```

```js
$(document).ready(function(){           
    //Le span est caché par défaut
    $("#message").hide();

    // Lorsqu'on clique sur button2, un gestionnaire d'événement click est 
    // ajouté à button1
    $("#button2").click(function () {
        $("#button1").on("click", function () {
            //Cache le span
            $("#message").show();
        });
        //Modifie le texte de button1
        $("#button1").text("Cliquez ici");
    });

    // Lorsqu'on clique sur button3, le gestionnaire d"évènement click de 
    // button1 est supprimé
    $("#button3").click(function () {
        //Supprime l'événement click du bouton
        $("#button1").off("click");
        //Change le texte du bouton
        $("#button1").text("Pas de clic possible");
        //Cache le span
        $("#message").hide();
    });
});
```

## Les propriétés de l’objet event

L’utilisation des événements en jQuery entraîne systématiquement l’utilisation d’un objet event.

Celui-ci possède de nombreux attributs parmi lesquels pageX et pageY déjà abordés dans d’autres cours. Deux autres attributs en lien avec la gestion des événement avancée sont disponibles : target et type.

La propriété target contient l'élément qui a déclenché l'événement. Sa valeur peut être un élément attaché au gestionnaire d'événements ou à l'un de ses descendants. Cette propriété est très utile dans le cas d'événements bouillonnants pour déterminer le déclencheur.

La propriété type indique le type d'événement déclenché. Cette propriété est surtout utile dans les situations où plusieurs gestionnaires d'événements sont reliés au même élément.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <div>
        <h2>Titre du div</h2>
        <p>Un paragraphe dans un div</p>
        <p>Un autre paragraphe avec <span>un span</span></p>
    </div>
    <p>Elément cliqué : <span id="res"></span></p>
    <p>Evénement déclenché (p) : <span id="res2"></span></p>
</body>
```

```js
$(document).ready(function(){        
    //On attache un gestionnaire d'événement click au div   
    $("div").click(function (event) {
        //On récupère l'élément déclencheur de l'événement grâce à target
        //On affiche son nom en utilisant nodeName
        $("#res").html(event.target.nodeName);
    });

    //On attache plusieurs gestionnaires aux éléments p du div
    $("div p").on("click mouseover mouseout", function (event) {
        //On récupère et on affiche le type d'événement déclenché
        $("#res2").text(event.type);
    });
});
```