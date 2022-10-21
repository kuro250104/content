Certains langages informatiques comme le langage JavaScript utilise le mot-clé this afin de faire référence à l’objet auquel il appartient. Sa valeur change en fonction de là où il est utilisé.

## This utilisé avec une méthode

Dans une méthode, ```this``` fait référence au “propriétaire” de la méthode.

Exemple :

```js
const person = {
    firstName: "John",
    lastName : "Doe",
    id   	: 5566,
    fullName : function() {
        return this.firstName + " " + this.lastName;
    }
};
```

Dans cet exemple, ```this``` fait référence au “propriétaire” de la fonction. Donc, ici, à “person”, car person est le propriétaire de la méthode ```fullname```.

## this tout seul

Lorsqu’il est utilisé tout seul, c’est-à-dire sans être placé dans une méthode ou un objet, ```this``` fait référence à l’objet global. 

Dans un navigateur, l’objet global est l’objet ```window```. 

```this``` seul fonctionne exactement de la même manière quand il est utilisé en mode strict. 

Exemple :

```js
let x = this;
```

Dans cet exemple, ```this``` fait donc référence à l’objet ```window```.

## This dans une fonction (default)

Dans une fonction, le propriétaire de la fonction est l’objet global. Donc lorsqu’il est utilisé au sein d’une fonction, ```this``` faire référence à ```window```.

Exemple :

```js
function myFunction() {
    return this;
}
```

## This dans une fonction et mode strict

Lorsqu’il est utilisé dans une fonction et que le code est exécuté en mode strict, ```this``` renvoie ```undefined```.

Exemple :

```js
"use strict";
function myFunction() {
    return this;
}
```

## this et les évènements

Lorsqu’il est utilisé avec un événement, ```this``` fait référence à l’élément HTML qui reçoit cet évènement.

Exemple :

```js
<button onclick="this.style.display='none'">
    Click to Remove Me!
</button>
```

Dans cet exemple, ```this``` fait référence à l’élément HTML ```<button>```.
