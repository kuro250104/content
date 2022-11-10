## Introduction

JQuery permet de copier, remplacer ou supprimer des éléments ou du contenu dans le DOM.

## Copier ou cloner des éléments HTML avec jQuery

La méthode ```clone()``` permet de créer une copie d'un élément ou d'une série d'éléments ainsi que le contenu y étant rattaché.

Une fois un élément copié, Il ne reste qu’à utiliser une méthode jQuery pour placer la copie à l’endroit souhaité dans le dans le DOM.

```html
<!-- Code HTML de base -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <p id="text">Un paragraphe</p>
        <p id="text2">Un deuxième paragraphe</p>
    </div>
</body>
```

```js
$(document).ready(function(){
    // copie des éléments ayant pour classe "container" et stockage
    // de cette copie dans la variable "container"
    let container = $(".container").clone();
    // intégration de la copie juste avant la fermeture de l'élément
    // <body>
    container.appendTo("body");
});
```

Après exécution :

```html
<!-- Code HTML après exécution -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <p id="text">Un paragraphe</p>
        <p id="text2">Un deuxième paragraphe</p>
    </div>
    <div class="container">
        <h1>Cours jQuery</h1>
        <p id="text">Un paragraphe</p>
        <p id="text2">Un deuxième paragraphe</p>
    </div>
</body>
```

## Supprimer des éléments et des contenus HTML avec jQuery

Pour supprimer des éléments ou du contenu du DOM, il est possible d’utiliser les méthodes ```remove()```, ```detach()```, ```empty()``` ou ```unwrap()```.

La méthode ```remove()``` permet de supprimer un élément ou une collection d'éléments ainsi que leur contenu. De plus, toutes les données et événements jQuery associés à ces éléments seront supprimés. Il est possible de passer des sélecteurs en argument de cette méthode pour filtrer les éléments à supprimer, à partir d’une sélection initiale.

La méthode ```detach()``` fonctionne exactement de la même manière que remove(), mais permet de conserver les données associées à l'élément supprimé en les stockant dans une variable de telle sorte à pouvoir les réutiliser plus tard.

La méthode ```empty()``` permet de supprimer tout le contenu d'un ou plusieurs éléments sans supprimer l'élément lui-même (le balisage HTML de la sélection sera conservé).

Enfin, la méthode ```unwrap()``` permet de supprimer l'élément parent d'un ou plusieurs éléments. Il est possible de passer un sélecteur en argument de cette méthode afin de n’effectuer la suppression que si l'objet parent correspond audit sélecteur.

```html
<!-- Code HTML de base -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <p id="text">Un paragraphe</p>
        <p id="text2">Un deuxième paragraphe</p>
    </div>
    <section>
        <p>Un paragraphe en dehors du div</p>
    </section>
</body>
```

```js
$(document).ready(function(){
    // supprimer la balise avec l'id "text" et l'ensemble de ce qu'elle
    // contient
    $("p").remove("#text");

    // supprimer la balise <h1> et son contenu, et stocke le tout dans
    // une variable "titre"
    let titre = $("h1").detach();

    // insère le contenu de la variable "titre" directement après
    // l'ouverture de la balise <body>
    titre.prependTo("body");

    // supprime le contenu de la balise avec l'id "text2" tout en 
    // conservant la balise.
    $("#text2").empty();

    // enlève les balises <section> parentes des balises <p>
    $("p").unwrap("section");
});
```

Après exécution :

```html
<!-- Code HTML après exécution -->
<body>
    <h1>Cours jQuery</h1>
    <div class="container">
        <p id="text2"></p>
    </div>
    <p>Un paragraphe en dehors du div</p>
</body>
```

## Remplacer des éléments HTML avec jQuery

JQuery permet également de remplacer des éléments par d'autres grâce aux méthodes ```replaceAll()``` ou ```replaceWith()```.

La méthode ```replaceAll()``` s’utilise avec un argument représentant la sélection à remplacer. La méthode doit s’appliquer sur l’élément devant servir de contenu de remplacement.

La méthode ```replaceWith()``` fonctionne différemment : il faut l’appliquer à l'élément à supprimer et à remplacer, en lui passant le contenu de remplacement en tant qu’argument.

```html
<!-- Code HTML de base -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <p id="text">Un paragraphe</p>
        <p id="text2">Un deuxième paragraphe</p>
    </div>
    <section>
        <p>Un paragraphe en dehors du div</p>
    </section>
</body>
```

```js
$(document).ready(function(){
    $(" <p>Je suis un paragraphe sans div ni section en parent</p>").replaceAll("section");
    $("#text").replaceWith("<span>Je suis un span</span>");
});
```

Après exécution :

```html
<!-- Code HTML après exécution -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <span>Un élément span</span>
        <p id="text2">Un deuxième paragraphe</p>
    </div>
    <p>Un paragraphe sans div ni section en parent</p>
</body>
```