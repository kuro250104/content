Les méthodes, lorsque les objets sont utilisés, sont des fonctions qui vont principalement permettre d’obtenir ou de modifier la valeur des propriétés de l’objet.

Les méthodes sont des propriétés contenant la définition d’une fonction. Ce sont des fonctions stockées comme des propriétés de l’objet.

## Le mot-clé this

Dans une fonction normale, ```this``` fait référence au “propriétaire” de la fonction. 

Pour un objet, lorsque ```this``` est utilisé dans une méthode, cela fait référence à l’objet dans lequel est contenu la méthode.

Exemple :

```js
const person = {
    firstName: "John",
    lastName: "Doe",
    id: 5566,
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
};
```

Dans cet exemple, ```this``` fait référence à l’objet ```person```. En d’autres termes, ```this.firstName``` signifie “**la propriété de cet (*this*, en anglais) objet**”. 

En fait, cela équivaut à écrire ```person.firstName```.

## Accéder aux méthodes d’un objet

### Syntaxe

Les méthodes sont accessibles grâce avec la syntaxe suivante :

```js
objet.methode();
```

Lorsque la méthode est appelée avec les parenthèses, cela retourne le résultat de la fonction ; tandis que si elle est appelée sans les parenthèses, cela retourne la définition de la fonction.

Exemple :

```js
name = person.fullName();
```

Cet exemple retourne “John Doe”, car la méthode est appelée avec la parenthèse. 

Exemple :

```js
name = person.fullName;
```

Cet exemple retourne la définition de la définition, c'est-à-dire ```function() { return this.firstName + " " + this.lastName; }```, car la méthode est appelée sans les parenthèses.

## Ajouter une méthode

Pour ajouter une méthode à une fonction, il suffit d’utiliser la notation pointée puis d’écrire la définition de la fonction. 

Exemple :

```js
person.name = function () {
    return this.firstName + " " + this.lastName;
};
```