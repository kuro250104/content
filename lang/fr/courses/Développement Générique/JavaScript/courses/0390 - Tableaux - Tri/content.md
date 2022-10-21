Afin de pouvoir organiser les données stockées dans un tableau, JavaScript met à disposition des fonctions de tri. 

## Trier dans l’ordre alphabétique

La fonction ```sort()``` permet de trier les données d’un tableau dans l’ordre alphabétique.

Exemple :

```js
var carBrands = ["Renault", "Toyota", "Tesla", "Peugeot", "Citroen", 0390 - "Nissan"];
carBrands.sort();
```

Cet exemple retourne le résultat suivant : ```["Citroen", "Nissan", "Peugeot", "Renault", "Tesla", "Toyota"]```. Les entrées du tableau, ici, sont bien retournées dans l’ordre alphabétique.

## Inverser les éléments dans un array

Il est également possible de trier les éléments en partant de la dernière entrée. Pour ce faire, la fonction ```reverse()``` doit être utilisée.

Exemple :

```js
var carBrands = ["Renault", "Toyota", "Tesla", "Peugeot", "Citroen", "Nissan"];
carBrands.reverse();
```

Cet exemple retourne le résultat suivant : ```["Toyota", "Tesla", "Renault", "Peugeot", "Nissan", "Citroen"]```. Par rapport à l’exemple du point précédent, les données ont bien été triées dans l’ordre inverse. 

## Trier des nombres

Par défaut, la fonction ```sort()``` ne fonctionne qu’avec des chaînes de caractères. Si cette fonction est utilisée pour trier des nombres, des résultats inattendus peuvent être retournés. 

Ainsi la question suivante se pose : comment trier des nombres au sein d’un tableau ?

Cela peut être fait en utilisant une fonction de comparaison. 

Exemple :

```js
const points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a - b});
```

L’exemple ci-dessus retourne le résultat suivant : ```[1, 5, 10, 25, 40, 100]```. 

### La fonction de comparaison

Dans l’exemple précédent, une fonction de comparaison est utilisée afin de créer un ordre de tri “alternatif” utilisable avec les nombres. Cette fonction doit retourner une valeur négative, zéro ou une valeur positive, en fonction des arguments passés.

Pour rappel, la fonction de comparaison est la suivante :

```js
function(a, b){return a - b}
```

Lorsque la fonction ```sort()``` est appelée, elle envoi les valeurs du tableau à la fonction de comparaison. Cette dernière trie les données et les retourne en fonction de la valeur retournée. 

Ainsi, si le résultat est négatif, ```a``` est trié avant ```b``` ; tandis que si le résultat est positif, ```b``` est trié avant ```a```.

## Trier un tableau dans un ordre au hasard

Pour trier un tableau dans un ordre au hasard, une fonction de comparaison est utilisée, en combinaison avec la fonction ```random()``` de l’objet JavaScript ```Math```.

Exemple :

```js
const points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return 0.5 - Math.random()});
```

Dans cet exemple, grâce à la fonction ```Math.random()```, les valeurs sont retournées dans un ordre aléatoire.

### La méthode Fisher Yates

La méthode utilisée dans le point précédent pour trier les données dans un ordre aléatoire n’est pas correcte, car ```Math.random()``` favorise, en fait, certains nombres par rapport à d’autres. 

C’est pourquoi il est plus judicieux d’utiliser le mélange Fisher Yates. 

En informatique, ce “mélange” est traduit de la manière suivante :

```js
for (let i = points.length -1; i > 0; i--) {
    let j = Math.floor(Math.random() * i)
    let k = points[i]
    points[i] = points[j]
    points[j] = k
}
```

## Trouver la plus grande ou la plus petite valeur dans un tableau

En JavaScript, il n’existe pas de fonction native permettant de trouver la plus grande ou la plus petite valeur dans un tableau. Néanmoins, une fois que le tableau a été trié, il est possible d’utiliser les index pour définir la valeur minimum et maximum.

Exemple :

```js
const points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a - b});
points[0]; // Retourne la plus petite valeur du tableau : 1
points[points.length - 1]; // Retourne la plus grande valeur du tableau : 100 
```

__Remarque__ : Trier un *array* entier pour simplement trouver la plus grande ou la plus petite valeur dans le tableau est une manière de faire assez inefficace. 

### Utiliser Math.max() avec un tableau

Pour trouver la valeur maximum dans un tableau, la fonction suivante peut-être utilisée :

```js
function myArrayMax(arr) {
    return Math.max.apply(null, arr);
}
```

### Utiliser Math.min() sur un tableau

De même, pour trouver la valeur minimum dans un tableau, la méthode suivante peut-être utilisée :

```js
function myArrayMin(arr) {
    return Math.min.apply(null, arr);
}
```

## Trier des objets contenus dans un array

Les tableaux JavaScript contiennent très souvent des objets. 

Exemple :

```js
const cars = [
    {type:"Volvo", year:2016},
    {type:"Saab", year:2001},
    {type:"BMW", year:2010}
];
```

Bien que le tableau contient des propriétés ayant différents types de données, la fonction ```sort()``` est tout de même utilisable. Pour ce faire, une fonction de comparaison est utilisée.

Exemple :

```js
cars.sort(function(a, b){return a.year - b.year});
```

L’exemple ci-dessus trie les années de la plus éloignée à la plus proche, grâce à la fonction de comparaison, dans laquelle l’appel à la propriété ```year``` du tableau est effectué de la manière suivante : ```a.year``` et ```b.year```.