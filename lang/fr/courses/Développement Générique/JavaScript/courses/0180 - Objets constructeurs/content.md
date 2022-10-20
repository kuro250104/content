Un constructeur est une méthode qui est appelée automatiquement en premier à la création d’un nouvel objet.

## Types d’objets (blueprints et classes)

Tous les exemples des cours précédents sur les objets étaient limités, car ils ne permettaient de créer qu’un seul objet.

Parfois, il y a besoin d’un “**blueprint**” pour créer plusieurs objets du même type. Le moyen de créer un type d’objet est d’utiliser un constructeur. 

Les objets de même type sont créés en appelant le constructeur grâce au mot-clé ```new```.

Exemple :

```js
const myFather = new Person("John", "Doe", 50, "blue");
const myMother = new Person("Sally", "Rally", 48, "green");
```

## Le mot-clé this

Lorsqu’il est utilisé avec un objet, ```this``` a pour valeur l’objet lui-même. 

Dans un constructeur, ```this``` n’a pas de valeur. En fait, il sert de substitut pour le nouvel objet. Dans un constructeur, donc, la valeur de ```this``` deviendra le nouvel objet lorsque celui-ci sera créé. 

__Remarque__ : ```this``` n’est pas une variable, mais un mot-clé. Il est donc **impossible** de modifier sa valeur. 

## Ajouter une propriété à un objet

Ajouter une nouvelle propriété est plutôt facile.

Exemple :

```js
myFather.nationality = "English";
```

Dans cet exemple, la nouvelle propriété ```nationality``` est seulement ajoutée à l’objet ```myFather```, et à aucun autre objet de type ```person```.

## Ajouter une méthode à un objet

Ajouter une méthode à un objet est tout aussi facile. 

Exemple :

```js
myFather.name = function () {
    return this.firstName + " " + this.lastName;
};
```

De même que pour l’ajout d’une nouvelle propriété à un objet, ici la méthode ```name``` est seulement ajoutée à l’objet **myFather** et aucun autre objet de type ```person```.

## Ajouter une propriété à un constructeur

Il n’est pas possible d’ajouter une propriété à un constructeur comme cela a été fait auparavant. Ainsi l’exemple ci-dessous ne fonctionne-t-il pas :

```js
Person.nationality = "English";
```

De ce fait, pour ajouter une propriété à un constructeur, il faut l’ajouter directement au sein de la fonction. 

Exemple :

```js
function Person(first, last, age, eyecolor) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
    this.eyeColor = eyecolor;
    this.nationality = "English";
}
```

L’avantage de faire comme cela est que les propriétés peuvent ainsi avoir des valeurs par défaut.

## Ajouter une méthode à un constructeur

Comme pour les variables, il n’est pas non plus possible d’ajouter une méthode à un constructeur comme cela serait fait pour un objet existant. 

Là encore, la méthode doit être ajoutée directement au sein du constructeur. 

Exemple :

```js
function Person(firstName, lastName, age, eyeColor) {
    this.firstName = firstName; 
    this.lastName = lastName;
    this.age = age;
    this.eyeColor = eyeColor;
    this.changeName = function (name) {
        this.lastName = name;
    };
}
```

## Constructeur intégré à JavaScript

JavaScript met à disposition des constructeurs intégrés pour les objets natifs :

- ```new String()``` : créer un objet de type chaîne de caractères
- ```new Number()``` : créer un objet de type nombre
- ```new Boolean()``` : créer un objet de type booléen
- ```new Object()``` : créer un objet de type Objet
- ```new Array()``` : créer un objet de type array
- ```new RegExp()``` : créer un objet de type expression régulière
- ```new Function()``` : créer un objet de type fonction
- ```new Date()``` : créer un objet de type date

__Remarque__ : Bien qu’il soit possible de créer des objets de type nombre, string, etc, il est recommandé, pour des raisons de performances, de ne pas le faire, mais de plutôt utiliser les valeurs primitives.
