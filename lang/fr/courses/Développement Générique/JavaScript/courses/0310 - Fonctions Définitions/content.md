Le but de ce cours est de détailler un peu plus la définition des fonctions ainsi que leur utilisation.

Une fonction est définie grâce au mot-clé ```function```. Ensuite, il est possible d’utiliser une fonction soit par déclaration, soit par une expression. 

## Déclaration d’une fonction

Voici la syntaxe pour déclarer une fonction :

```js
function functionName(parameters) {
  // Code
}
```

Une fonction ainsi déclarée n’est pas utilisée de suite, mais est en fait “sauvegardée” pour une utilisation ultérieure - lorsqu’elle est appelée par le programme.

## Expression de fonction

Le langage JavaScript permet également de définir une fonction en utilisant une expression. Une expression de fonction peut-être sauvegardée dans une variable.

Exemple :

```js
const x = function (a, b) {return a * b};
```

Par la suite, cette fonction est appelée en utilisant le nom de la variable. 

Exemple :

```js
let z = x(4, 3);
```

__Remarque__ : La fonction ci-dessus est une fonction dite **anonyme**, car elle n’a pas de nom à proprement parler. En fait, une fonction stockée dans une variable n’a pas besoin de nom, car c’est le nom de la variable qui est utilisé pour appeler la fonction.

## Le constructeur Function()

Ce point est simplement évoqué à titre informatif, afin de faire savoir à l’étudiant qu’une telle méthode existe. Cependant, cette utilisation n’est pas recommandée. 

Le JavaScript permet également de déclarer une fonction en utilisant son constructeur. 

Exemple :

```js
const myFunction = new Function("a", "b", "return a * b");

let x = myFunction(4, 3);
```

## Hoisting d’une fonction

Le **hoisting**, en JavaScript, s’applique également à la déclaration d’une fonction. C’est pour cela qu’il est aussi possible - lorsque le mode strict est désactivé -, d’utiliser une fonction avant même de l’avoir déclarée. 

Exemple :

```js
myFunction(5);

function myFunction(y) {
  return y * y;
}
```

__Remarque__ : Les expressions de fonctions ne sont pas hoistées.

## Les fonctions qui s’appellent elles-mêmes

Les fonctions peuvent s’écrire de telle manière qu’elles s’appellent elles-mêmes. En d’autre terme, ces fonctions sont invoquées - c’est-à-dire appelées - par elles-mêmes, sans avoir besoin d’être appelées plus loin dans le code. 

Pour ce faire, les parenthèses **()** doivent être utilisées.

Les fonctions déclarées, en revanche, ne peuvent pas s’invoquer toutes seules. Seules peuvent le faire les expressions de fonction, si elles sont suivies par des parenthèses vides **()**.

Exemple :

```js
(function () {
  let x = "Hello!!"; // La fonction s'invoque elle-même
})();
```

## Les fonctions peuvent s’utiliser comme des valeurs

Les fonctions JavaScript peuvent s’utiliser comme valeur de variable. 

Exemple :

```js
function myFunction(a, b) {
  return a * b;
}

let x = myFunction(4, 3);
```

Les fonctions JavaScript peuvent également s’utiliser dans des expressions. 

Exemple :

```js
function myFunction(a, b) {
    return a * b;
}

let x = myFunction(4, 3) * 2;
```

## Les fonctions sont des objets

Les fonctions, en JavaScript, sont des objets ; elles ont à la fois des **propriétés** et des **méthodes**. Par conséquent, il est possible d’utiliser quelques méthodes afin d’obtenir des informations.

### arguments.length

Cette méthode retourne le nombre d’arguments reçus lorsque la fonction a été invoquée.

Exemple :

```js
function myFunction(a, b) {
  return arguments.length;
}
```

Cet exemple retourne 2, car c’est le nombre d’arguments reçus par la fonction lorsqu’elle a été invoquée.

### toString()

Cette méthode retourne la fonction comme chaîne de caractères. 

Exemple :

```js
function myFunction(a, b) {
  return a * b;
}

let text = myFunction.toString();
```

## Les fonctions fléchées

Les fonctions fléchées permettent d’écrire une expression de fonction avec une syntaxe plus courte. En effet, il n’y a ni besoin des mot-clés ```function``` et ```return```, ni des accolades.

Exemple :

```js
var x = function(x, y) {
  return x * y;
} // Syntaxe normale

const x = (x, y) => x * y; // Syntaxe fléchée
```

## Informations supplémentaires

Il est important de savoir que les fonctions fléchées n’ont pas leur propre ```this```. La raison est simple : vu que c’est une fonction anonyme, le programme ne sait pas par quoi il doit remplacer le ```this```. De plus, il n’est pas recommandé de les utiliser pour définir des méthodes d’objets

Les fonctions fléchées ne sont pas hostées et doivent donc être définies avant d’être utilisées.

Utiliser ```const``` plutôt que ```var``` est recommandé, car une expression de fonction n’est pas censée pouvoir être modifiée.

Il est possible d'omettre le ```return``` et les accolades seulement lorsqu’il n’y a qu’une seule expression au sein de la fonction. C’est donc une bonne habitude de continuer à les utiliser malgré tout. 

Exemple :

```js
const x = (x, y) => { return x * y };
```