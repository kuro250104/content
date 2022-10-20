Le langage JavaScript a trois types de fenêtres popup : les popups d’alerte, les popups de confirmation et les popups de saisie de texte.

## Les popups d’alerte

Ce type de popup est souvent utilisé pour s’assurer qu’une information est bien transmise à l’utilisateur. 

Lorsqu’un popup d’alerte s’affiche à l’écran de l’utilisateur, ce dernier doit cliquer sur “OK” avant de pouvoir continuer à naviguer sur le site.

### Syntaxe

Voici la syntaxe à utiliser pour utiliser un popup d’alerte :

```js
window.alert("Texte à afficher");
```

__Remarque__ : Il n’y a pas besoin d’utiliser le préfixe ```Windows``` pour pouvoir utiliser ```alert()```.

Exemple :

```js
alert("Je suis une popup de type alert");
```

Dans cet exemple, lorsque la fenêtre de popup s’affiche avec le texte “Je suis un popup de type alert”, l’utilisateur doit cliquer sur OK pour pouvoir continuer sa navigation.

## Popup de confirmation

Les popups de confirmation sont souvent utilisées afin de vérifier l’exactitude de quelque chose. Lorsque ce type de popup est utilisé, l’utilisateur doit soit cliquer sur “OK”, soit sur “Cancel” pour pouvoir continuer.

Par conséquent, lorsque l’utilisateur clique sur OK, la fenêtre retourne **true**, sinon elle retourne **false**.

### Syntaxe

Voici la syntaxe pour créer un popup de confirmation :

```js
window.confirm("Texte");
```

__Remarque__ : Là encore, il n’est pas obligatoire d’utiliser le préfixe ```Windows```.

Exemple :

```js
if (confirm("Êtes-vous sûr de vouloir quitter cette page ?")) {
    txt = "À bientôt.";
} else {
    txt = "Vous avez annulé";
}
```

Dans cet exemple, lorsque le programme arrive dans la condition, il lance le popup de confirmation et regarde le résultat retourné. Si **true** est retourné - donc si l’utilisateur a cliqué sur OK -, le message “À bientôt s’affiche”. Sinon, c’est “Vous avez annulé” qui s’affiche.

## Popup de saisie de texte

Cette popup est communément utilisée lorsque l’utilisateur doit saisir une information avant de pouvoir accéder à une page. Lorsqu’un popup de saisie de texte est utilisé, l’utilisateur à la possibilité de cliquer sur “OK” ou “Cancel” après avoir saisi l’information demandée.

S’il clique sur “OK”, la valeur saisie est retournée. Sinon, c’est ```null``` qui est renvoyé.

### Syntaxe

Voici la syntaxe pour utiliser un popup de saisie de texte :

```js
window.prompt("sometext","defaultText");
```

__Remarque__ : Encore une fois, le préfixe ```Windows``` n’est pas obligatoire.

Exemple :

```js
let person = prompt("Merci de saisir votre nom", "Kévin");
let text;
if (person == null || person == "") {
    text = "L'utilisateur a annulé l'opération.";
} else {
    text = "Bonjour " + person + " ! Comment ça va ?";
}
```

Dans cet exemple, le popup de saisie de texte est contenu dans la variable ```person```. Il est important de noter que le deuxième paramètre envoyé à la fonction ```prompt()``` permet de définir une valeur par défaut.

## Retour à la ligne dans un popup

Pour afficher un retour à la ligne dans un popup, il faut utiliser le backslash (\) suivi du caractère **n**.

Exemple :

```js
alert("Bonjour\nComment ça va ?");
```

Le texte de l’exemple ci-dessus est affiché sur deux lignes dans le popup.