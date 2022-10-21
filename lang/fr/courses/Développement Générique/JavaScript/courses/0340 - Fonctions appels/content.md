En JavaScript, il est possible d’utiliser une méthode avec plusieurs objets. Pour ce faire, la méthode ```call()``` est invoquée. 

## Toutes les fonctions sont des méthodes

En JavaScript, toutes les fonctions sont des méthodes d’objet. Ainsi, même si une fonction n’est pas une méthode d’objet, cette fonction appartient bien à l’objet global ```window```.

Exemple :

```js
const myObject = {
    firstName:"John",
    lastName: "Doe",
    fullName: function () {
        return this.firstName + " " + this.lastName;
    }
}

// Retourne "John Doe":
myObject.fullName();
```

## La méthode call()

Cette méthode est intégrée à JavaScript. Elle peut être utilisée pour invoquer une méthode et prend en paramètre l’objet propriétaire de la méthode. 

__Remarque__ : Avec cette méthode, il est possible d’appeler une méthode appartenant à un autre objet. 

Exemple :

```js
const person = {
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
}
const person1 = {
    firstName:"John",
    lastName: "Doe"
}

// Retourne "John Doe":
person.fullName.call(person1);
```

## La méthode call() avec des arguments

Cette méthode accepte les arguments. 

Exemple :

```js
const person = {
    fullName: function(city, country) {
        return this.firstName + " " + this.lastName + "," + city + "," + country;
    }
}

const person1 = {
    firstName:"John",
    lastName: "Doe"
}

person.fullName.call(person1, "Oslo", "Norway");
```