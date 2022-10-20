Les propriétés sont les éléments les plus importants d’un objet en JavaScript. Les propriétés sont les valeurs associées à un objet JavaScript. 

Un objet est donc un ensemble désordonné de propriétés. 

Certaines de ces propriétés peuvent être modifiées, ajoutées et/ou effacées, mais certaines sont également dites en “lecture seules”.

## Accéder aux propriétés JavaScript

Il existe trois syntaxes possibles pour accéder à une propriété d’objet :

- ```nomDeLObjet.propriete```
- ```nomDeLObjet[“propriete”]```
- ```nomDeLObjet[expression]```

Exemple :

```js
console.log(person.name); // Affiche "Joe"
console.log(person["name"]); // Affiche "Joe"
```

### La boucle for in

Cette boucle parcourt chaque propriété d’un objet et le code se trouvant entre accolades est exécuté pour chaque propriété.

Exemple :

```js
const person = {
  fname:" John",
  lname:" Doe",
  age: 25
};

for (let x in person) {
  txt += person[x];
}
```

 Dans cet exemple, la boucle parcourt chaque propriété de l’objet ```person``` et stocke la valeur dans la variable ```x```. Ensuite, pour chaque propriété rencontrée, la valeur contenue dans ```x``` est ajoutée à la variable ```x```.

## Ajouter de nouvelles propriétés

Il est possible d’ajouter une nouvelle propriété à un objet en lui attribuant simplement une valeur.

Exemple :

```js
person.city = "Paris";
```

Ici, la nouvelle propriété est ajoutée à l’objet ```person``` et contient la valeur “Paris”.

## Effacer des propriétés

Le mot-clé ```delete``` permet d’effacer une propriété. Ce mot-clé efface à la fois la valeur et la propriété elle-même.

Bien sûr, une fois effacée, la propriété ne peut plus être utilisée à moins qu’elle soit à nouveau ajoutée à l’objet en utilisant la méthode détaillée dans le point précédent. 

```delete``` a été créé de telle manière qu’il n’agisse que sur les propriétés d’objet. Il n’a donc aucun effet sur les variables et les fonctions.

Exemple :

```js
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};

delete person.age; // delete person["age"] est également utilisable
```

__Remarque__ : ```delete``` ne devrait pas être utilisé sur les propriétés prédéfinies, car cela risque de faire planter le programme.

## Objets “nichés”

Au sein d’un objet, les valeurs peuvent également être un autre objet. 

Exemple :

```js
myObj = {
    name:"John",
    age:30,
    cars: {
        car1:"Ford",
        car2:"BMW",
        car3:"Fiat"
    }
}
```

Pour accéder aux propriétés de cet objet “niché”, il y a deux possibilités : la notation pointée ou la notation entre crochets. 

Exemple :

```js
myObj.cars.car2;
```

Exemple :

```js
myObj.cars["car2"];
```

Exemple :

```js
myObj["cars"]["car2"];
```

## Objets et array nichés

Les valeurs d’un objet peuvent également être un array, et les valeurs de cet array peuvent être un objet. 

Exemple :

```js
const myObj = {
    name: "John",
    age: 30,
    cars: [
        {name:"Ford", "models":["Fiesta", "Focus", "Mustang"]},
        {name:"BMW", "models":["320", "X3", "X5"]},
        {name:"Fiat", "models":["500", "Panda"]}
    ]
}
```

Pour accéder à un tableau à l’intérieur d’un objet, il est possible d’utiliser la boucle for in.

Exemple :

```js
for (let i in myObj.cars) {
    x += "<h1>" + myObj.cars[i].name + "</h1>";
    for (let j in myObj.cars[i].models) {
        x += myObj.cars[i].models[j];
    }
}
```

## Les attributs de propriétés

Toute propriété porte un nom et a, en plus, une valeur. Cette valeur est l’un des attributs de la propriété. Les autres attributs possibles sont : **enumerable**, **configurable** et **writable**. Ces attributs permettent de définir la manière dont il est possible d’accéder à la variable. 

En JavaScript, tous les attributs peuvent être lus, mais seulement les valeurs peuvent être modifiées - si la propriété le permet.

## Prototype de propriétés

Les objets JavaScript héritent des propriétés de leurs prototypes.

Le mot-clé ```delete``` n’efface pas les propriétés héritées, mais si une propriété du prototype est effacée, cela affecte tous les objets hérités du prototype.