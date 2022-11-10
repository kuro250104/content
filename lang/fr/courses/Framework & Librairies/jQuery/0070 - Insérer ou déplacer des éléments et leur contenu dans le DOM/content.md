## Introduction

JQuery dispose de nombreuses manières pour insérer du contenu dans le DOM. Il est possible de classer ces méthodes selon les 3 catégories suivantes :

- Une méthode qui permet d'insérer du contenu dans un élément HTML, c'est-à-dire qui crée un élément enfant de la sélection initiale.
- Une méthode qui permet d'insérer du contenu avant ou après l'élément HTML, c'est-à-dire qui crée un élément de même niveau (frère) que la sélection initiale.
- Une méthode qui permet d'insérer du contenu autour d'un élément HTML, c'est-à-dire qui crée un élément parent de la sélection initiale.

## Insérer du contenu dans un élément

En plus des méthodes ```html()``` et ```text()``` déjà présentées, jQuery fournit quatre méthodes pour insérer du contenu ou des éléments dans d'autres éléments : ```prepend()```, ```append()```, ```prependTo()``` et ```appendTo()```.

Les méthodes ```prepend()``` et ```append()``` nous permettront d'insérer du contenu en tant que premier et dernier élément enfant de l'élément cible, respectivement. Le contenu à insérer doit être passé en paramètre de ces méthodes.

```html
<!-- Code HTML de base -->
<div class="container">
    <h1>Cours jQuery</h1>
    <p id="text">Un paragraphe</p>
    <p id="text2">Un deuxième paragraphe</p>
</div>
```

```js
$(document).ready(function(){
    // ajout d'un contenu au début des éléments disposants de la
    // classe "container"
    $(".container").prepend("<p>Je suis ajouté avec prepend()</p>");
    // ajout d'un contenu à la fin des éléments disposants de la
    // classe "container"
    $(".container").append("<ul><li>Element</li><li>Element</li></ul>")
});
```

```html
<!-- Code HTML une fois le jQuery exécuté -->
<div class="container">
    <p>Je suis ajouté avec prepend()</p>
    <h1>Cours jQuery</h1>
    <p id="text">Un paragraphe</p>
    <p id="text2">Un deuxième paragraphe</p>
    <ul>
        <li>Element</li>
        <li>Element</li>
    </ul>
</div>
```

Les méthodes ```prependTo()``` et ```appendTo()``` permettent d'effectuer les mêmes opérations que ```prepend()``` et ```append()```. La différence entre ces deux ensembles de méthodes réside dans leur syntaxe : en utilisant ```prependTo()``` et ```appendTo()```, le contenu à insérer sera avant la méthode et sera inséré dans l'élément spécifié en paramètre.

```js
$(document).ready(function(){
    $("<p>Je suis ajouté avec prepend()</p>").prependTo(".container");
    $("<ul><li>Element</li><li>Element</li></ul>").appendTo(".container");
});
```

## Insérer du contenu avant ou après un élément

Pour insérer du contenu avant ou après un élément, jQuery nous propose d’utiliser l’une des quatres méthodes ```before()```, ```after()```, ```insertBefore()``` ou ```insertAfter()```.

Les méthodes ```before()``` et ```after()``` permettent respectivement d'ajouter du contenu avant et après la sélection d'un élément. Le contenu à ajouter doit être passé en argument.

Les méthodes ```insertBefore()``` et ```insertAfter()``` permettent d'effectuer les mêmes opérations que ```before()``` et ```after()```. Là encore, il s'agit d'une différence syntaxique : il faut ici spécifier le contenu à ajouter avant la méthode, et passer la sélection de l'élément auquel le contenu doit être ajouté comme argument.

```html
<!-- Code HTML de base -->
<div class="container">
    <h1>Cours jQuery</h1>
    <p id="text">Un paragraphe</p>
    <p id="text2">Un deuxième paragraphe</p>
</div>
```

```js
$(document).ready(function(){
    $("#text").before("<p>Je suis ajouté avec before()</p>");
    $("<span>Je suis ajouté avecinsertAfter()</span>").insertAfter("#text");
});
```

Après exécution : 

```html
<!-- Code HTML une fois le jQuery exécuté -->
<div class="container">
    <h1>Cours jQuery</h1>
    <p>Je suis ajouté avec before()</p>
    <p id="text">Un paragraphe</p>
    <span>Je suis ajouté avec insertAfter()</span>
    <p id="text2">Un deuxième paragraphe</p>
</div>
```

## Insérer du contenu autour d’un élément

Pour insérer une structure HTML autour de l'élément sélectionné, jQuery met à disposition les méthodes ```wrap()```, ```wrapAll()``` ou ```wrapInner()```.

La méthode ```wrap()``` permet d'ajouter une structure HTML autour de chaque élément de la sélection initiale. La structure doit être passée en argument de la méthode.

La méthode ```wrapAll()``` permet d'ajouter une structure HTML autour de toute la sélection. Il faut ici aussi passer cette structure en argument de la méthode.

La méthode ```wrapInner()``` permet d'ajouter une structure HTML autour du contenu de chaque élément sélectionné. Il faut ici aussi passer cette structure en argument de la méthode.

```html
<!-- code HTML de base -->
<div class="container">
    <h1>Cours jQuery</h1>
    <p id="text">Un paragraphe</p>
    <p id="text2">Un deuxième paragraphe</p>
</div>
```

```js
$(document).ready(function(){
    // Entoure le contenu de toutes les balises <p> d’une balise <section>
    // les balises <p> seront donc placées toutes les deux à l’intérieur
    // d’une balise <section>
    $("p").wrapAll("<section></section>");

    // Entoure le contenu de chaque balise <p> d’une balise <div>
    // chaque balise <p> sera placée à l’intérieur d’une balise <div>
    // À la suite de la commande précédente, les balises
    // <div> seront ainsi contenues dans les balises <section>
    $("p").wrap("<div></div>");

    // Intègre une balise <span> dans chaque balise <p>, directement
    // après l’ouverture de la balise <p>, et juste avant sa fermeture
    $("p").wrapInner("<span></span>");
});
```

Après exécution  :

```html
<!-- Code HTML après exécution du jQuery -->
<div class="container">
    <h1>Cours jQuery</h1>
    <section>
        <div>
            <p id="text"><span>Un paragraphe</span></p>
        </div>
        <div>
            <p id="text2"><span>Un deuxième paragraphe</span></p>
        </div>
    </section>
</div>
```

## Déplacer un contenu HTML dans le DOM

Il est possible de déplacer un contenu existant en utilisant l'une des méthodes décrites précédemment, et en passant cette fois en paramètre un sélecteur des éléments à y placer.

```html
<!-- code HTML de base -->
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
    // positionne l'élément possédant l'id "text" directement après
    // l'élément <body>
    $("#text").prependTo("body");
    // positionne l'élément possédant l'id "text2" juste avant
    // l'élément <h1>
    $("#text2").insertBefore("h1");
});
```

Après exécution :

```html
<!-- Code HTML après exécution du jQuery -->
<body>
    <p id="text">Un paragraphe</p>
    <div class="container">
        <p id="text2">Un deuxième paragraphe</p>
        <h1>Cours jQuery</h1>
    </div>
</body>
```