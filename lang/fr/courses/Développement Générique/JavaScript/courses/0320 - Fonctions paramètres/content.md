Les fonctions JavaScript n’effectuent pas de vérifications sur les valeurs des paramètres.

## Paramètres et arguments d’une fonction

Dans un cours antérieur, il a été expliqué que les fonctions peuvent avoir des paramètres. La syntaxe est la suivante :

```js
function maFonction(parametre1, parametre2) {
    // Code à exécuter
}
```

Pour rappel, et afin de clarifier la chose :

- Les **paramètres** sont les noms listés dans la définition de la fonction.
- Les **arguments** sont les valeurs réelles passées à - et reçues par - la fonction.

## Règles concernant les paramètres

En JavaScript, les définitions de fonctions ne précisent pas le type de données reçues en paramètres.

Les fonctions n’effectuent pas de vérification concernant le type des données passées en arguments.

Les fonctions ne vérifient pas le nombre d’arguments reçus.

## Paramètres par défaut

Si une fonction est appelée, mais qu’il manque des arguments - dans le sens où il y a moins d’arguments envoyés que de paramètres déclarés -, ces valeurs sont initialisées à **undefined**.

Parfois, cela ne pose pas de problème, mais de manière générale, il est toujours recommandé d’attribuer une valeur par défaut à un paramètre. 

Exemple :

```js
function myFunction(x, y) {
    if (y === undefined) {
        y = 2;
    }
}
```

Dans cet exemple, si l’argument **y** est manquant (donc que sa valeur vaut **undefined**), là valeur 2 lui est assignée par défaut. 

Depuis 2015, il est possible de raccourcir le code ci-dessus en donnant la valeur par défaut d’une variable, directement dans la définition de la fonction. 

Exemple :

```js
function (x, y = 2) {
    // Code
}
```

## Les arguments d’objet

Les fonctions ont un objet intégré appelé **argument**. Ce dernier contient un tableau des arguments utilisés lorsque la fonction a été invoquée.

Exemple :

```js
x = findMax(1, 123, 500, 115, 44, 88);

function findMax() {
    let max = -Infinity;
    for (let i = 0; i < arguments.length; i++) {
        if (arguments[i] > max) {
            max = arguments[i];
        }
    }
    return max;
}
```

Ce code permet de trouver le nombre le plus grand parmi la liste de nombre passée en arguments. Cela peut se faire grâce à l’objet **argument** qui crée un tableau contenant les arguments passés à l’appel de la fonction.

Remarque : Si une fonction est appelée avec trop d’arguments - plus que de paramètres définis -, ces arguments en trop peuvent être “atteints” grâce à l’objet **argument**.

## Les arguments sont passés par valeur

Lors de l’appel de la fonction, les paramètres sont les arguments. En JavaScript, les arguments sont envoyés par **valeur**, non pas par la location de l’argument. Par conséquent, une fonction change la valeur d’un argument, mais pas la valeur originale du paramètre. 

**Les changements de valeur d’un argument ne sont pas visibles en dehors de la fonction.**

## Les objets sont passés par référence

En JavaScript, les références d’objet sont les valeurs. En conséquence de cela, les objets agissent comme s’ils sont passés par **référence** : cela signifie que si une fonction modifie la propriété d’un objet, cela change la valeur originale.

**Les changements effectués sur les propriétés d’objet sont visibles en dehors de la fonction.**