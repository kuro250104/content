## Introduction

JQuery permet de gérer une multitude d’événements concernant les formulaires grâce à de nombreuses méthodes présentées ci-dessous.

## Les méthodes focus() et focusin()

Lorsque l'élément est l'élément actif du document, c'est-à-dire lorsque le curseur de la souris se trouve sur l'élément qu'il contient, l'élément à ce qu’on appelle le “focus”. Par exemple, lorsqu'un utilisateur clique sur un champ de formulaire, celui-ci devient alors “focus”.

JQuery fournit deux méthodes pour gérer l'événement de focus : les méthodes ```focus()``` et ```focusin()```. L'événement de focus est ainsi envoyé à l'élément lorsqu'il obtient le focus.

La méthode ```focusin()``` est similaire à la précédente, à ceci près qu’elle attache un événement à l’élément courant ainsi qu’à ses éléments enfants.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <form>
        <div>
            <label for="nom">Nom : </label>
            <input type="text" id="prenom">
        </div>
        <div>
            <label for="prenom">Prénom : </label>
            <input type="text" id="prenom">
        </div>
        <div>
            <label for="mail">Mail : </label>
            <input type="email" id="mail">
        </div>
    </form>
</body>
```

```js
$(document).ready(function(){
    //Change la couleur de fond du champ en rouge dès qu'il a les focus
    $("input").focus(function () {
        $(this).css("background-color", "red");
    });

    /* Avec on()
    $("input").on('focus', function() {
        $(this).css("background-color", "red");
    });
    */

    //Change la couleur de fond des label en orange dès qu'un élément dans 
    //le formulaire a le focus
    $("form").focusin(function () {
        $("label").css("background-color", "orange");
    });

    /* Avec on()
    $("form").on('focusin', function() {
        $("label").css("background-color", "orange");
    });
    */
});
```

## Les méthodes blur() et focusout()

JQuery fournit deux méthodes pour gérer l'événement de perte de focus : ```blur()``` et ```focusout()```. La méthode ```blur()``` est l’exacte opposé de ```focus()```, puisqu’elle attache un événement pour un élément qui perd le focus.

La méthode ```focusout()``` est quant à elle l’exacte opposé de ```focusin()```, elle est donc similaire à ```blur()``` à ceci près que les éléments enfants seront également concernés par les événements.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <form>
        <div>
            <label for="nom">Nom : </label>
            <input type="text" id="prenom">
        </div>
        <div>
            <label for="prenom">Prénom : </label>
            <input type="text" id="prenom">
        </div>
        <div>
            <label for="mail">Mail : </label>
            <input type="email" id="mail">
        </div>
    </form>
</body>
```

```js
$(document).ready(function(){
    //Change la couleur de fond du champ en rouge dès qu'il a les focus
    $("input").focus(function () {
        $(this).css("background-color", "red");
    });

    /* Avec on()
    $("input").on('focus', function() {
        $(this).css("background-color", "red");
    });
    */

    //Change la couleur de fond du champ en orange dès qu'il perd les focus
    $("input").blur(function () {
        $(this).css("background-color", "orange");
    });

    /* Avec on()
    $("input").on('blur', function() {
        $(this).css("background-color", "orange");
    });
    */
});
```

## La méthode change()

La méthode ```change()``` permet de déclencher un événement lorsque la valeur de l’élément ciblé change.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <form>
        <div>
            <label for="nom">Nom : </label>
            <input type="text" id="prenom">
        </div>
        <select>
            <option value="france">France</option>
            <option value="belgique">Belgique</option>
        </select>
    </form>
    <p>Option choisie : <span></span></p>
</body>
```

```js
$(document).ready(function(){
    //Dès qu'une option différente est choisie, récupère et affiche sa valeur
    $("select").change(function () {
        $("span").text($(this).val());
    });

    /* Avec on()
    $("select").on('change', function () {
        $("span").text($(this).val());
    });
    */
});
```

## La méthode submit()

La méthode ```submit()``` permet de déclencher un événement lors de la soumission d’un formulaire. Cette méthode ne s’applique donc que sur les éléments de type formulaire.

```html
<!-- Code HTML de base -->
<body>
    <h1>Titre principal</h1>
    <form method="post" action="#">
        <div>
            <label for="nom">Nom : </label>
            <input type="text" id="prenom">
        </div>
        <input type="submit" value="Envoyer">
    </form>
</body>
```

```js
$(document).ready(function(){
    //Affiche un message lors de l'envoi du formulaire
    $("form").submit(function () {
        alert("Formulaire envoyé");
    });

    /* Avec on()
    $("form").on('submit', function () {
        alert("Formulaire envoyé");
    });
    */
});
```