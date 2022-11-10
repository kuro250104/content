Dans ce nouveau cours, nous étudierons quelques fonctions avancées liées à l'animation : comment gérer la file d'attente, arrêter l'animation ou comment augmenter le délai avant le début de l'animation.

La file d'attente dans jQuery est utilisée pour l'animation. Vous pouvez les utiliser à toutes les fins que vous souhaitez. Il s'agit d'un tableau de fonctions stockées élément par élément à l'aide de ```jQuery.data()```.

## Gérer la file d’attente en jQuery

À l'aide de plusieurs méthodes jQuery, nous pourrons interagir avec cette file d'attente de différentes manières :

- La méthode ```queue()```
- La méthode ```dequeue()```
- La méthode ```clearQueue()```

La méthode jQuery ```queue()``` retournera différentes fonctions de la file d'attente pour l'élément, ou nous permettra de manipuler la file d'attente de différentes manières en fonction du nombre de paramètres à lui passer.

En passant le nom de la file d'attente en tant que paramètre unique, nous pouvons déjà utiliser ```queue()```. Vous devez savoir ici que le nom par défaut de la file d'attente des effets jQuery est fx.

```html
<body>
    <h1>Titre principal</h1>
    <button id="button1">Animation</button>
    <p>Taille de la queue : <span></span></p>
</body>
```

```js
$(document).ready(function(){
    $("#button1").click(function(){
        $("h1")
            //Diminue la largeur de h1 de 20% sur 5 secondes 
            .animate({width: "-=20%"},5000)
            //Augmente la taille de la police de 20px sur 2 secondes
            .animate({fontSize: "20px"},2000)
            //Fondu jusqu'à 0.5 d'opcité sur 2 secondes
            .fadeTo(2000, 0.5);
    });
 
    function enAttente(){
        //Récupère les infos liées à la file d'attente
        let queue = $("h1").queue("fx");
        //Affiche la taille de la file d'attente
        $("span").text(queue.length);
        //Actualise (quasiment) en direct cette taille
        setTimeout(enAttente, 10);
    };
    enAttente();
});
```

Nous pouvons également passer la fonction de rappel comme deuxième paramètre de la méthode ```queue()``` pour interagir avec la file d'attente. Par exemple, cela nous permettra d'ajouter de nouvelles animations à la file d'attente.

Lorsqu’on ajoute une fonction de rappel avec ```queue()```, on doit impérativement à la fin appeler ```dequeue()``` afin de dire à jQuery de continuer à exécuter les animations suivantes.

```html
<style>
    .bleu {
        background-color: lightBlue;
    }

    .orange {
        background-color: orange
    }

    div {
        width: 100px;
        height: 100px;
        position: relative;
        border: 2px solid black;
    }
</style>

<body>
    <h1 class="blue">Titre principal</h1>
    <button id="button1">Animation du carré</button>
    <div class="orange"></div>
</body>
```

```js
$(document).ready(function(){
    $("#button1").click(function () {
        $("div")
            //Ajoute 200px de marge sur la gauche sur 1 seconde
            .animate({ left: "+=200px" }, 1000)
            //Ajoute 50px de marge sur le haut sur 400ms
            .animate({ top: "+=50px" }, 400)
            //Effectu le changement de couleur du carré entre le bleu et le orange
            .queue(function () {
                $(this).toggleClass("blue orange").dequeue();
            })
            //Diminue la marge gauche de 200px sur 1 seconde
            .animate({ left: "-=200px" }, 1000)
            //Diminue la marge haute de 50px sur 400ms
            .animate({ top: "-=50px" }, 400)
    });
});
```

Ici, nous utilisons la méthode ```toggleClass()``` dans la fonction de rappel associée à queue () pour modifier la classe du div. Nous avons finalement chaîné ```dequeue()``` pour pouvoir passer à l'animation suivante.

Si vous supprimez l'appel à ```dequeue()``` du code ci-dessus, vous pouvez observer que l'animation s'arrête après l'appel de ```queue()```.

Enfin, la méthode ```clearQueue()``` nous permettra de supprimer toutes les fonctions actuellement dans la file d'attente.

```html
<style>
    .bleu {
        background-color: lightBlue;
    }

    .orange {
        background-color: orange
    }

    div {
        width: 100px;
        height: 100px;
        position: relative;
        border: 2px solid black;
    }
</style>

<body>
    <h1 class="blue">Titre principal</h1>
    <button id="button1">Animation du carré</button>
    <button id="button2">Supprimer la file d'attente</button>
    <div class="orange"></div>
</body>
```

```js
$(document).ready(function(){
    $("#button1").click(function () {
        $("div")
            //Ajoute 200px de marge sur la gauche sur 1 seconde
            .animate({ left: "+=200px" }, 1000)
            //Ajoute 50px de marge sur le haut sur 400ms
            .animate({ top: "+=50px" }, 400)
            //Effectu le changement de couleur du carré entre le bleu et le orange
            .queue(function () {
                $(this).toggleClass("blue orange").dequeue();
            })
            //Diminue la marge gauche de 200px sur 1 seconde
            .animate({ left: "-=200px" }, 1000)
            //Diminue la marge haute de 50px sur 400ms
            .animate({ top: "-=50px" }, 400)
    });
    //Supprime toutes les fonctions actuellement dans la file d'attente
    $("#button2").click(function () {
        $("div").clearQueue();
    });
});
```

## Stopper une animation avec les méthodes jQuery stop() ou finish()

Nous pourrons également utiliser la méthode ```stop()``` ou ```finish()``` pour arrêter l'animation et supprimer la fonction courante dans la file d'attente.

Tout d'abord, la méthode ```stop()``` mettra en pause l'animation actuelle par défaut.

Cette méthode peut utiliser deux valeurs booléennes comme paramètres. Le premier booléen spécifie si l'animation de la file d'attente doit également être supprimée (true) ou non (false). La valeur par défaut est false.

Le deuxième paramètre booléen indique si l'animation actuelle doit être terminée immédiatement, true ou false. De même, la valeur par défaut est false.

```html
<style>
    .bleu {
        background-color: lightBlue;
    }

    .orange {
        background-color: orange
    }

    div {
        width: 100px;
        height: 100px;
        position: relative;
        border: 2px solid black;
    }
</style>

<body>
    <h1 class="blue">Titre principal</h1>
    <button id="button1">Animation du carré</button>
    <button id="button2">Supprimer la file d'attente</button>
    <div class="orange"></div>
</body>
```

```js
$(document).ready(function(){
    $("#button1").click(function () {
        $("div")
            //Ajoute 200px de marge sur la gauche sur 1 seconde
            .animate({ left: "+=200px" }, 1000)
            //Ajoute 50px de marge sur le haut sur 400ms
            .animate({ top: "+=50px" }, 400)
            //Effectu le changement de couleur du carré entre le bleu et le orange
            .queue(function () {
                $(this).toggleClass("blue orange").dequeue();
            })
            //Diminue la marge gauche de 200px sur 1 seconde
            .animate({ left: "-=200px" }, 1000)
            //Diminue la marge haute de 50px sur 400ms
            .animate({ top: "-=50px" }, 400)
    });
    //Stop l'animation
    $("#button2").click(function () {
        $("div").stop(true);
    });
});
```

Par défaut, la méthode ```finish()``` arrêtera immédiatement l'animation en cours et supprimera toutes les animations de la file d'attente.

La différence entre la méthode ```finish()``` et la méthode ```stop()``` est que lorsqu'elle est utilisée, la valeur liée à la propriété CSS définie dans l'animation sera immédiatement définie sur sa valeur finale.

```html
<style>
    .bleu {
        background-color: lightBlue;
    }

    .orange {
        background-color: orange
    }

    div {
        width: 100px;
        height: 100px;
        position: relative;
        border: 2px solid black;
    }
</style>

<body>
    <h1 class="blue">Titre principal</h1>
    <button id="button1">Animation du carré</button>
    <button id="button2">Supprimer la file d'attente</button>
    <div class="orange"></div>
</body>
```

```js
$(document).ready(function(){
     $("#button1").click(function () {
        $("div")
            //Ajoute 200px de marge sur la gauche sur 1 seconde
            .animate({ left: "+=200px" }, 1000)
            //Ajoute 50px de marge sur le haut sur 400ms
            .animate({ top: "+=50px" }, 400)
            //Effectu le changement de couleur du carré entre le bleu et le orange
            .queue(function () {
                $(this).toggleClass("blue orange").dequeue();
            })
            //Diminue la marge gauche de 200px sur 1 seconde
            .animate({ left: "-=200px" }, 1000)
            //Diminue la marge haute de 50px sur 400ms
            .animate({ top: "-=50px" }, 400)
    });
    //Stop l'animation et supprime les animations dans la file d'attente
    $("#button2").click(function () {
        $("div").finish();
    });
});
```

## Ajouter un délai avant l’exécution d’animations avec delay()

La méthode ```delay()``` va nous permettre de définir un temps avant que certaines animations ne doivent être démarrées. Nous lions souvent cette méthode entre deux animations.

Il faut fournir le nombre de millisecondes correspondant au délai entre les deux animations comme paramètre de cette méthode.

```html
<style>
    .bleu {
        background-color: lightBlue;
    }

    .orange {
        background-color: orange
    }

    div {
        width: 100px;
        height: 100px;
        position: relative;
        border: 2px solid black;
    }
</style>

<body>
    <h1 class="blue">Titre principal</h1>
    <button id="button1">Animation du carré</button>
    <button id="button2">Supprimer la file d'attente</button>
    <div class="orange"></div>
</body>
```

```js
$(document).ready(function(){
    $("#button1").click(function () {
        $("div")
            //Ajoute 200px de marge sur la gauche sur 1 seconde
            .animate({ left: "+=200px" }, 1000)
            //Ajoute une pause d'une seconde
            .delay(1000)
            //Ajoute 50px de marge sur le haut sur 400ms
            .animate({ top: "+=50px" }, 400)
            //Ajoute une pause d'une seconde
            .delay(1000)
            //Diminue la marge gauche de 200px sur 1 seconde
            .animate({ left: "-=200px" }, 1000)
            //Ajoute une pause d'une seconde
            .delay(1000)
            //Diminue la marge haute de 50px sur 400ms
            .animate({ top: "-=50px" }, 400)
    });
});
```