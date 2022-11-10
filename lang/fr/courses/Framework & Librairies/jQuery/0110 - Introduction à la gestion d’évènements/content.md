## Introduction

JQuery inclut un système de gestion d’événements. Ceux-ci sont gérés grâce à des “écouteurs”, traditionnellement appelés “EventListeners” (fr : écouteurs d’événements). Le principe de base de la gestion d'événement est donc de placer des écouteurs qui vont déclencher des actions dès activation.

JQuery introduit de nombreux événements, voici une liste non exhaustive : 

- ```click```
- ```mouseenter```
- ```keyup```
- ```change```
- ```etc…```

Chacun de ces événements peut être appelé de trois manières différentes, voici 3 exemples en utilisant l’événement “click”, et se basant sur un code HTML simple : 

```html
<!-- Code HTML simple -->
<body>
    <p>Je suis un texte</p>
</body>
```

## 1 - Avec la méthode du nom de l’événement

Chaque événement dispose d’une méthode homonyme permettant de définir un écouteur d’événement de manière simple. L’événement de “click” est ainsi récupéré grâce à la méthode ```click()```:

```js
// Exemple avec la méthode "click"
$(document).ready(function () {
    // Lorsqu'on clique sur un élément p
    $("p").click(function () {
        // Modifie le texte sur l'élément p cliqué
        $(this).text("Paragraphe cliqué");
    });
});
```

```html
<!-- Code HTML après exécution -->
<body>
    <p>Paragraphe cliqué</p>
</body>
```

## 2 - Avec la méthode “on()” appliquée sur une sélection

La méthode “on” est une méthode générique qui permet d’appeler n’importe quel événement. Il faut lui spécifier en argument le nom de l’événement à appliquer sur la sélection initiale : 

```js
// Exemple avec la méthode "on"
$(document).ready(function () {
    // Lorsqu'on clique sur un élément p
    $("p").on("click", function () {
        // Modifie le texte sur l'élément p cliqué
        $(this).text("Paragraphe cliqué");
    });
});
```

```html
<!-- Code HTML après exécution -->
<body>
    <p>Paragraphe cliqué</p>
</body>
```

## 3 - Avec la méthode “on()” appliquée à la volée

La méthode ```on()``` permet également de définir des écouteurs d’événement sans avoir de sélection initiale. Cette manière de procéder est appelée une “délégation”. Il est possible de l’utiliser de la sorte : 

```js
// Exemple avec la méthode "on"
$(document).ready(function () {
    // Lorsqu'on clique sur un élément p
    $.on("click", "p", function () {
        // Modifie le texte sur l'élément p cliqué
        $(this).text("Paragraphe cliqué");
    });
});
```

```html
<!-- Code HTML après exécution -->
<body>
    <p>Paragraphe cliqué</p>
</body>
```

Les 3 méthodes ci-dessus ont donc le même effet et permettent toutes d’arriver au même résultat. De manière générale, il est plutôt recommandé d’utiliser la méthode ```on()```, puisqu’elle peut permettre de refactoriser votre code plus facilement par la suite.

Afin de voir l’intérêt et surtout les différences qui s’opèrent entre ces 3 manières de faire, il est important de comprendre comment fonctionne la propagation des événements ainsi que la délégation.

## Propagation des événements et délégation

Lorsqu’un événement est déclenché, il parcourt le DOM jusqu'à rencontrer le gestionnaire responsable de l'événement. Cette étape est également appelée "propagation".

Pour être plus précis, l'événement se déroule en 3 étapes différentes:

- La première étape, appelée étape de «capture», consiste à parcourir le DOM depuis l’élément racine jusqu’à atteindre l'élément qui a déclenché l'événement. Cette phase est usuellement nommée par son anglicisme Capturing.
- La seconde étape correspond au moment précis où l'événement atteint l’élément cible. Elle est nommée “étape cible” ou “Target” en Anglais.
- La dernière étape, dite de "bouillonnement" (Bubbling en anglais), est la phase inverse durant laquelle le parcours du DOM se fait dans le sens inverse de l’étape de capture.

Dans la plupart des cas, le gestionnaire d'événements est configuré pour traiter les événements durant la phase de bouillonnement. De la sorte, la phase de capture est généralement invisible.

Ce concept de propagation induit donc que les gestionnaires d’événements n’ont nul obligation d’être rattachés aux écouteurs, et c’est la raison pour laquelle il est possible d’attacher ledit écouteur à un élément parent plutôt qu’à l’élément cible. Ce principe est nommé délégation.

Grâce à ce concept de délégation, il est donc possible de mettre en place un seul et même écouteur d’événement pour plusieurs éléments simultanément. La conséquence de la délégation est que l’événement déclenché produira toujours le même résultat, mais pour différents éléments (en fonction de celui qui aura déclenché ledit événement).

```js
$(document).ready(function () {
    //Lorsqu'on clique sur un element p ou que la souris
    //survol l'element p
    $("p").on("click mouseover", function () {
        //Modifie le texte sur l'element p cliqué
        $(this).text("Paragraphe cliqué");
    });
});
```

Nous avons aussi la possibilité de le faire de la manière suivante. Cela permet la délégation, de sorte que si vous ajoutez plus d'éléments avec le même sélecteur dans votre page HTML. Lorsqu'un sélecteur est fourni, le gestionnaire d'événements est appelé delegated. Les gestionnaires d'événements délégués ont l'avantage de pouvoir traiter les événements des éléments descendants qui sont ajoutés au document ultérieurement. En sélectionnant un élément dont la présence est garantie au moment où le gestionnaire d'événements délégué est attaché, vous pouvez utiliser des gestionnaires d'événements délégués pour éviter d'avoir à attacher et supprimer fréquemment des gestionnaires d'événements.

```js
$(document).on('click', '.selecteur', function () {
    //Cacher l'element cliqué sur la classe .selecteur
    $(this).hide();
});
```

## Propagation des événements et délégation

Une fois l'événement déclenché, il traversera le DOM jusqu'à ce qu'il rencontre le gestionnaire responsable de l'événement. Cet événement est également appelé "propagation" dans le DOM.

Pour être précis, l'événement se déroule en 3 étapes différentes:

- Une étape, appelée étape de «capture», dans cette étape, l'événement commence à partir de l'élément racine et se poursuit jusqu'à l'élément qui a déclenché l'événement (Capturing)
- La phase «cible» correspondant au moment où l'événement atteint l'élément (Target)
- L'étape de "bouillonnement", dans laquelle les événements propagent le DOM vers la racine (Bubbling)

Dans la plupart des cas, le gestionnaire d'événements est configuré pour traiter les événements pendant la phase de bouillonnement, de sorte que la phase de capture nous est généralement invisible.

Ce concept de propagation signifie que nous n'avons pas à accrocher les gestionnaires d'événements aux déclencheurs: nous pouvons également choisir de l'attacher à l'élément parent de l'élément. Au fur et à mesure que l'événement se propage, il se produira éventuellement sur le nœud parent, il sera donc traité à ce moment-là.

Dans les situations où nous avons de nombreux éléments pouvant déclencher le même événement (qui sera géré de la même manière à chaque fois), cette technique de délégation peut être très utile: pour chaque élément, un gestionnaire unique peut être attaché à l'élément parent de ces éléments.

## La gestion des événements avec jQuery

jQuery simplifie la gestion des événements en nous fournissant une série de méthodes pouvant être utilisées pour gérer les événements.

Ces méthodes seront nommées en fonction des événements auxquels elles réagissent : click(), mouseenter(), keyup(), change(), etc. Et c'est en fait une représentation simplifiée de la méthode jQuery on(), qui nous permet de gérer plusieurs événements dans la même fonction de gestionnaire d'événements.

La fonction de gestionnaire d'événements sera une fonction anonyme, et nous la passerons comme paramètre de méthode. Il sera appelé lorsqu'un événement se produit.

Par exemple, lorsqu'un événement se produit, nous pouvons gérer l'événement de clic du paragraphe en modifiant le texte du paragraphe :

```js
$(document).ready(function(){
    $("p").on("click", function () {
        $(this).text("Paragraphe cliqué");
    });
});
```