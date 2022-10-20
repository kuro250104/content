Tous les objets JavaScript héritent des propriétés et méthodes d’un prototype.

En informatique, “hériter” signifie que tous les objets ou classes enfants bénéficient de ce prototype. En JavaScript, lorsqu’un nouvel objet est créé, celui-ci hérite du prototype de cet objet.

## Héritage du prototype

Tous les objets JavaScript héritent d’un prototype :

- L’objet ```Date``` hérite de ```Date.prototype```
- L’objet ```Array``` hérite de ```Array.prototype```
- L’objet ```Person``` hérite de ```Person.prototype```

```Object.prototype``` est placé en haut de la chaîne d’héritage. Ainsi, les objets ```Date```, ```Array```, et ```Person``` héritent tous de ```Object.prototype```.

## Utiliser la propriété prototype

En JavaScript, la propriété permet d’ajouter une nouvelle propriété à un constructeur. 

Exemple :

```js
function Person(first, last, age, eyecolor) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
    this.eyeColor = eyecolor;
}

Person.prototype.nationality = "English";
```

Cette propriété permet également d’ajouter une nouvelle méthode à un constructeur.

Exemple :

```js
function Person(first, last, age, eyecolor) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
    this.eyeColor = eyecolor;
}

Person.prototype.name = function() {
    return this.firstName + " " + this.lastName;
};
```

## Avertissement

Il ne faut JAMAIS modifier les prototypes des objets natifs de JavaScript.