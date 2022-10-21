Grâce à une fonction intégrée, le JavaScript permet d’écrire une méthode qui peut s’utiliser avec plusieurs objets.

## La méthode apply()

L’utilisation de cette méthode est similaire à ```call()```.

Exemple :

```js
const person = {
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
}

const person1 = {
    firstName: "Mary",
    lastName: "Doe"
}

// Retourne "Mary Doe":
person.fullName.apply(person1);
```

Dans cet exemple, la méthode ```fullName``` de l’objet ```person``` est appliquée à ```person1```.

## La différence entre call() et apply()

Voici la différence entre ces deux méthodes :

- La méthode ```call()``` prend les arguments séparément
- La méthode ```apply()``` prend les arguments comme un tableau

De manière générale, la méthode ```apply()``` est très utile si un tableau doit être utilisé plutôt qu’une liste d’arguments.

## La méthode apply() avec des arguments

Cette méthode accepte des arguments sous forme d’array. 

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

person.fullName.apply(person1, ["Oslo", "Norway"]);
```

## Mode strict

En mode strict, si le premier argument passé à la méthode ```apply()``` n’est pas un objet, cet argument devient malgré tout l’objet propriétaire de la fonction invoquée, tandis qu’en mode normal, il devient l’objet global.