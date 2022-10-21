Grâce à la structure DOM, le JavaScript permet également de réagir à des évènements.

## Réagir à des événements

Un code JavaScript peut être exécuté lorsqu’un événement se produit, par exemple, lorsque l’utilisateur clique sur un élément.

La syntaxe ci-dessous permet d’exécuter un code lorsque l’utilisateur clique sur un élément :

```js
onclick=JavaScript
```

Exemple :

```js
<!DOCTYPE html>
<html>
<body>

<h1 onclick="this.innerHTML = 'Ooops!'">Click on this text!</h1>

</body>
</html>
```

Dans cet exemple, le texte du titre ```h1``` est modifié lorsque l’utilisateur clique dessus.

## Les attributs HTML d’événement

Pour créer un événement directement dans le code HTML d’un élément, il est possible d’utiliser les attributs d’événement.

Exemple :

```js
<button onclick="displayDate()">Try it</button>
```

Dans cet exemple, la fonction ```displayDate()``` est  exécutée lorsque l’utilisateur clique sur le bouton.

## Créer un événement grâce au DOM

Grâce au DOM, il est possible de créer un événement directement en JavaScript.

Exemple :

```js
<script>
    document.getElementById("myBtn").onclick = displayDate;
</script>
```

Le code de cet exemple permet d’exécuter la fonction ```displayDate``` lorsque l’utilisateur clique sur le bouton portant l’id ```myBtn```.

### Les événements onload et onunload

Ces événements sont déclenchés lorsque l’utilisateur arrive sur la page ou lorsqu’il quitte la page. Ils permettent également de gérer les cookies.

Exemple :

```js
<body onload="checkCookies()">
```

### L’événement onchange

Cet événement est principalement utilisé avec les champs de saisie d’un formulaire, afin de vérifier le contenu du champ lorsque celui-ci est modifié. 

Exemple :

```js
<input type="text" id="fname" onchange="upperCase()">
```

Ici, la fonction ```upperCase()``` est appelée lorsque le contenu du champ est modifié. 