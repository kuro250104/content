Le code situé à l’intérieur d’une fonction n’est pas exécuté lorsque la fonction est **définie**, mais simplement lorsque la fonction est **invoquée**.

Le terme “**appeler une fonction**” est plus communément utilisé qu’“**invoquer une fonction**”. Certains développeurs disent également “démarrer une fonction” ou encore “exécuter une fonction”.

## Invoquer une fonction comme une fonction

La syntaxe ci-dessous est communément utilisée pour appeler une fonction :

```js
maFonction(argument1, argument2);
```
Une fonction invoquée de cette manière est en fait appelée par l’objet HTML global ```window```. Cet objet représente le navigateur. 

Ainsi, il est également possible d’écrire un appel à une fonction de cette manière :

```js
window.maFonction(argument1, argument2);
```

__Remarque__ : Invoquer une fonction de cette manière est monnaie courante, mais pas forcément une bonne pratique. En effet, les variables globales, méthodes globales ou fonctions peuvent facilement créer des conflits de noms et des bugs dans l’objet global.

## Le mot-clé this

En JavaScript, le mot-clé ```this``` représente l’objet qui “possède” le code écrit. 

Utilisé avec une fonction, ce mot-clé représente l’objet qui “possède” la fonction.

__Remarque__ : Le mot-clé ```this``` n’est pas une variable, il est donc impossible de changer sa valeur.

## L’Objet global

Lorsqu’une fonction est appelée sans objet “propriétaire”, la valeur de ```this``` devient l’objet global.

Dans un navigateur web, l’objet global est la fenêtre du navigateur (*window*, en anglais).

Exemple :

```js
let x = myFunction(); // x sera l'objet global window

function myFunction() {
    return this;
}
```

__Remarque__ : Utiliser l’objet global ```window``` comme une variable peut facilement faire planter un programme.

## Invoquer une fonction comme une méthode

En JavaScript, il est également possible d’invoquer une fonction comme une méthode d’objet. Dans un tel cas, le mot-clé ```this``` fait référence au propriétaire de la fonction, c’est-à-dire à l’objet lui-même.

Exemple :

```js
const myObject = {
    firstName:"John",
    lastName: "Doe",
    fullName: function () {
        return this.firstName + " " + this.lastName;
    }
}
myObject.fullName(); // Retourne"John Doe"
```

Dans cet exemple, ```this``` vaut ```myObject```.

## Invoquer une fonction avec un constructeur

Si l’invocation de la fonction est précédée du mot-clé ```new```, alors c’est un constructeur qui est appelé. Cette manière de faire peut laisser à penser qu’une nouvelle fonction est créée ; cependant, les fonctions étant des objets, en JavaScript, c’est donc bien un nouvel objet qui est créé. Par conséquent, le nouvel objet hérite des propriétés et méthodes du constructeur. 

__Remarque__ : Le mot-clé ```this```, dans le constructeur n’a, en soit, aucune valeur. Il fera ensuite, lorsqu’un nouvel objet sera créé lors de l’invocation de la fonction, référence à ce nouvel objet.

Exemple :

```js
// Ceci est un constructeur de fonction
function myFunction(arg1, arg2) {
    this.firstName = arg1;
    this.lastName  = arg2;
}

// Ici, un nouvel objet est créé
const myObj = new myFunction("John", "Doe");

// Retourne "John"
myObj.firstName;
```