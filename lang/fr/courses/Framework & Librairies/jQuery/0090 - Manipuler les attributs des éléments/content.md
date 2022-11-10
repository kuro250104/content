## Introduction

JQuery permet de manipuler les différents attributs des éléments HTML. Il permet ainsi d’en ajouter ou d’en modifier, de telle sorte à modifier le comportement de l'élément cible.

## Récupérer la valeur d’un attribut ou définir un attribut

La méthode ```attr()``` de jQuery permet de récupérer la valeur d'un attribut, d’en ajouter un ou bien d’en modifier un existant.

Pour récupérer la valeur d'un attribut, il faut passer le nom de l’attribut souhaité en argument de la méthode ```attr()```. Cette méthode agira alors comme un getter et ne retournera que la valeur d'attribut du premier élément sélectionné.

Il est également possible de passer une seconde valeur en argument de cette méthode. De la sorte, le premier argument permettra de cibler l’attribut souhaité, tandis que le second permettra de définir sa valeur. Ainsi si l’attribut existe déjà, alors il sera modifié, tandis que s’il n’existe pas, il sera créé.

```html
<!-- Code HTML avant exécution -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <span>Un élément span</span>
        <p id="text2">Un deuxième paragraphe</p>
    </div>
    <p>Un paragraphe en dehors du div</p>
    <p>Un <a href="https://www.google.com">lien</a> vers Google</p>
    <span id="valAttr"></span>
</body>
```

```js
$(document).ready(function(){
    // récupération de l'id des balises "p" et stockage dans la 
    // variable "pid"
    let pid = $("p").attr("id");

    // insertion de la valeur de l'attribut "id" de la balise "p"
    // dans l'élément possédant l'id "valAttr"
    $("#valAttr").textContent = "Premier id de p : " + pid;
    // ajout de l'attribut "target", avec la valeur "_blank" sur
    // toutes les balises <a>
    $("a").attr("target","_blank");
});
```

Après application du jQuery :

```html
<!-- Code HTML avant exécution -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <span>Un élément span</span>
        <p id="text2">Un deuxième paragraphe</p>
    </div>
    <p>Un paragraphe en dehors du div</p>
    <p>Un <a href="https://www.google.com" target="_blank">lien</a> vers           Google</p>
    <span id="valAttr">Premier id de p : p1</span>
</body>
```

## La méthode prop() et les propriétés du DOM

La méthode ```prop()``` permet de récupérer la valeur d'attribut du premier élément sélectionné, ou d'ajouter des attributs à chaque élément sélectionné ou de modifier la valeur d'un attribut existant.

Elle est similaire à la méthode ```attr()``` à ceci près qu’elle interagit sur le contenu HTML en modifiant également le DOM. Il est souvent dit de ces méthodes que ```attr()``` prend en compte l’état actuel de l’élément ciblé, tandis que ```prop()``` prend en compte son état original.

Pour les versions supérieures à jQuery 1.6 (que vous devriez donc utiliser majoritairement), il est davantage recommandé de se servir de la méthode ```prop()```.

## Supprimer un attribut ou une propriété

Pour supprimer un attribut, jQuery propose la méthode ```removeAttr()```, qui prend en paramètre le nom de l’attribut à supprimer.

De même, il existe la méthode ```removeProp()``` qui permet de supprimer une propriété de l'élément sélectionné.

La différence entre les deux méthodes est similaire à celle existante entre les méthodes ```attr()``` et ```prop()```. Il est ainsi ici aussi davantage recommandé de se servir de la méthode ```removeProp()``` plutôt que ```removeAttr()```.

```html
<!-- code HTML avant exécution du jQuery -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <span>Un élément span</span>
        <p id="text">Un paragraphe</p>
    </div>
    <p>Un paragraphe en dehors du div</p>
    <p>Un <a href="https://www.google.com">lien</a> vers Google</p>
</body>
```

```js
// premier code jQuery
$(document).ready(function () {
    $("a").removeAttr("href");
});
```

```html
<!-- code HTML après exécution du jQuery -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <span>Un élément span</span>
        <p id="text">Un paragraphe</p>
    </div>
    <p>Un paragraphe en dehors du div</p>
    <p>Un <a>lien</a> vers Google</p>
</body>
```

```js
// second code jQuery
$(document).ready(function () {
    $("#text").prop("code", "1234")
    .append("Le code est ", $("#text").prop("code"))
    .removeProp("code")
    .append(" Maintenant le code est ", $("#text").prop("code"));
});
```

```html
<!-- code HTML après exécution du second code jQuery -->
<body>
    <div class="container">
        <h1>Cours jQuery</h1>
        <span>Un élément span</span>
        <p id="text">Le code est 1234 Maintenant le code est </p>
    </div>
    <p>Un paragraphe en dehors du div</p>
    <p>Un <a>lien</a> vers Google</p>
</body>
```

## Récupérer ou mettre à jour la valeur courante d’éléments

La méthode ```val()``` permet de récupérer ou de mettre à jour la valeur actuelle de l'élément. Cette méthode est principalement utilisée avec les éléments de formulaire.

```js
$(document).ready(function () {
    // récupération de la valeur d'un élément possédant l'id
    // "text" et stockage dans la variable "valeurInput"
    let valeurInput = $(#text).val();

    // affichage de la variable "valeurInput"
    console.log(valeurInput);
});
```

## Les méthodes permettant de manipuler spécifiquement les attributs class

JQuery propose 4 méthodes spécifiques à la manipulation des attributs de classes.

La méthode ```hasClass()``` permet de déterminer si au moins un élément sélectionné a un attribut de classe spécifique. Il faut passer le nom de la classe recherchée comme argument de cette méthode. 

La méthode ```addClass()``` permet d'ajouter une ou plusieurs classes à un ensemble d'éléments. Il faut ici également passer la classe ou les classes à ajouter en argument.

La méthode ```removeClass()``` permet de supprimer une, plusieurs ou toutes les classes de chaque élément de la sélection. Si vous utilisez cette méthode sans argument, toutes les classes de l'élément sélectionné seront supprimées. Si une ou plusieurs classes sont passées comme argument, alors seules celles-ci seront supprimées.

La méthode ```toggleClass()``` permet d’ajouter ou de retirer une ou plusieurs classes, en fonction de l’état actuel de la sélection. Il est possible de passer un ou plusieurs noms de classe en argument. Pour chacun d’entre eux, si la classe est déjà existante dans l’élément sélectionné, alors elle sera supprimée. A contrario, si la classe n’est pas existante, alors elle sera ajoutée.

```html
<!-- Code HTML de base -->
<body>
    <button id="button1">Changer en bleu</button>
    <button id="button2">Toggle</button>
    <div class="display">
        <p>Un premier paragraphe</p>
        <p>Un deuxième paragraphe</p>
    </div>
    <p id="text">Troisième paragraphe hors div</p>
</body>
```

```js
// Code jQuery
$(document).ready(function(){
    // le code ci-dessous s’exécutera lors du click sur l’élément
    // possédant l’id “button1”
    $("#button1").click(function(){

        // Vérification de la non existence de la classe “bleu” sur 
        // l’élément possédant l’id “text”
        if(!$("#text").hasClass("bleu")){

            // Ajout de la classe bleu sur l’élément possédant
            // l’id “text”
            $("#text").addClass("bleu");
        }

        // modification du css en indiquant une couleur de police
        // bleue sur les éléments possédant la classe “bleu”
        $(".bleu").css("color", "blue");
    });

    // le code ci-dessous s’exécutera lors du click sur l’élément
    // possédant l’id “button2”
    $("#button2").click(function(){

        // Ajoute ou supprime les classes “hide” et “display” sur
        // tous les éléments “div”.
        $("div").toggleClass("hide display");

        // Cache les éléments possédant la classe “hide”
        $(".hide").hide();

        // Affiche les éléments possédant la classe “hide”
        $(".display").show();
    });
});
```

```html
<!-- Code HTML après un clic sur les 2 boutons-->
<body>
    <button id="button1">Changer en bleu</button>
    <button id="button2">Toggle</button>
    <div class="hide" style="display: none">
        <p>Un premier paragraphe</p>
        <p>Un deuxième paragraphe</p>
    </div>
    <p id="text" class="bleu" style="color: blue">Troisième paragraphe hors div</p>
</body>
```