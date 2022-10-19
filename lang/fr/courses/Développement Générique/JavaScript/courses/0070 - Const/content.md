Comme le mot-clé ```let```, permettant de déclarer des variables, ```const``` a également été introduit en 2015.

Ce mot-clé permet aussi de déclarer des variables et à, tout comme ```let```, ses propres particularités et restrictions.

## Ne peut pas être réassignée

Le mot-clé ```const``` ne permet pas de réassigner une valeur à une variable.

Exemple :

``` js
const PI = 3.141592653589793;
PI = 3.14;
PI = PI + 10;
```

Cet exemple retourne une erreur, car la variable ```PI``` est déclarée et initialisée avec une valeur, mais une autre valeur lui est assignée aux deux lignes suivantes. 

## Doit être assignée

Lors de la déclaration d’une variable avec ```const```, une valeur **doit** lui être assignée, sinon le programme retourne une erreur. 

Exemple :

``` js
const PI;
PI = 3.14159265359;
```

Cet exemple retourne une erreur, car aucune valeur n’est assignée à la variable ```PI``` au moment de sa déclaration. 

## Quand utiliser const ?

Il est conseillé de toujours déclarer une variable avec ```const``` à moins que sa valeur change à un moment donné. 

De plus, il faut toujours utiliser const lorsqu’un des types de variable suivant est déclaré :

- Un array
- Un objet
- Une fonction

## Objets, arrays et const

Le mot-clé ```const``` est un peu trompeur. En effet, contrairement à son utilisation dans d’autres langages, en Javascript ```const``` ne déclare pas une valeur constante, mais une référence constante à une valeur.

De cela, en utilisant ce mot-clé, il est impossible de :

- Réassigner une valeur constante
- Réassigner un array constant
- Réassigner un objet constant

Cependant, avec ```const```, il est possible de :

- Changer un array constant
- Changer un objet constant

### Array constant

Il est possible de modifier les entrées d’un tableau constant, mais il est impossible de réassigner cet array.

Exemple :

``` js
const cars = ["Saab", "Volvo", "BMW"];

cars[0] = "Toyota";

cars.push("Audi");
```

Dans cet exemple, un array constant est créé avec quelques entrées. Le premier index du tableau est modifié, passant de **Saab** à **Toyota**, et une entrée est ajoutée à la fin du tableau : **Audi**. Le mot-clé ```const``` autorise toutes ces opérations sur un array.

Exemple :

``` js
const cars = ["Saab", "Volvo", "BMW"];

cars = ["Toyota", "Volvo", "Audi"];
```

En revanche, cet exemple retourne une erreur, car ```const``` ne permet pas de réassigner un tableau constant. 

### Objet constant

Comme pour les tableaux, avec ```const```, il est possible de modifier les valeurs contenues dans les propriétés de l’objet, mais il n’est pas possible de réassigner cet objet. 

Exemple :

``` js
const car = {type:"Fiat", model:"500", color:"white"};
car.color = "red";
car.owner = "Johnson";
```

Cet exemple ne retourne pas d’erreur, parce que toutes les opérations faites sur l’objet constant sont autorisées par le mot-clé ```const```.

## Porté bloc

Tout comme ```let```, ```const``` a une portée bloc, ce qui signifie que lorsqu’une variable constante est déclarée entre accolades, il n’est pas possible de récupérer sa valeur ailleurs que dans ce bloc. 

Exemple :

``` js
{
   const x = 6;
}
const x = 4; // Ce x est différent de celui entre accolades
```

## Const et hoisting

Les variables déclarées avec ```const``` sont également hoistées, mais ne sont pas initialisées. Ainsi, utiliser une variable constante avant de l’avoir déclarée retourne une ```ReferenceError```.

Exemple :

``` js
alert (carName);
const carName = "Volvo";
```