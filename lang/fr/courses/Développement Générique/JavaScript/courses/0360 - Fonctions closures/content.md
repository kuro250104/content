Les variables globales peuvent être rendues locales grâce aux closures.

## Variables globales

Les fonctions peuvent accéder à toutes les variables créées **dans** la fonction.

Exemple :

```js
function myFunction() {
    let a = 4;
    return a * a;
}
```

Et une fonction peut également accéder à une variable créée **en dehors** de la fonction.

Exemple :

```js
let a = 4;
function myFunction() {
    return a * a;
}
```

Dans ce dernier exemple, la variable ```a``` a une portée globale. De là, elle appartient à l’objet global window et peut être modifiée par n’importe quel script de la page courante. 

__Remarque__ : Les variables déclarées sans les mots-clés ```var```, ```let``` ou ```const``` ont obligatoirement une portée globale, même si elles sont déclarées au sein d’une fonction.

## Durée de vie d’une variable

Les variables globales durent jusqu’à ce que la page soit changée, lorsque l’utilisateur change de page, par exemple.

Les variables locales, quant à elles, ont une durée de vie très courte. Elles sont créées lorsque la fonction est invoquée et est détruite lorsque le programme sort de la fonction.

## Les fonctions nichées

Toutes les fonctions ont accès à la portée globale. En fait, en JavaScript, toutes les fonctions ont accès à la portée “au-dessus” d’elles. 

Ainsi, pour une fonction nichée, cette dernière a également accès aux variables de la fonction dans laquelle elle est nichée, car c’est la portée “au-dessus”.

Exemple :

```js
function add() {
    let counter = 0;
    function plus() {counter += 1;}
    plus();   
    return counter;
}
```

Dans cet exemple, la fonction ```plus()``` est nichée dans la fonction ```add()```. Grâce à ça, la fonction ```plus()``` a accès aux variables de la portée “au-dessus”, donc à celles de la fonction ```add()```.

Malgré tout, le problème suivant se pose : comment atteindre la fonction ```plus()``` depuis l’extérieur ?

Le moyen de résoudre ce problème est d’utiliser les closures.

## Closures

Pour utiliser une closure et résoudre le problème cité au point précédent, il faut utiliser une fonction qui s’auto-invoque.

Exemple :

```js
const add = (function () {
    let counter = 0;
    return function () {counter += 1; return counter}
})();

add();
add();
add(); // Ici, counter vaut maintenant 3
```

Voici comment fonctionne le code ci-dessus :

La variable ```add()``` est assignée à la valeur de retour de la fonction qui s’auto-invoque. Cette dernière ne s’exécute qu’une fois, initialise le compteur à 0 et retourne une expression de fonction.

De cette façon, ```add``` devient une fonction et a, par conséquent, désormais accès au compteur dans la portée “parente”. C’est une ```closure``` et cela rend possible, pour une fonction, le fait d’avoir des variables “privées”.

Le compteur est protégé par la portée de la fonction anonyme et peut être seulement modifié en utilisant la fonction ```add()```.

Pour conclure, une closure est une fonction qui continue d’avoir accès à la portée parente, même après que la fonction parente ait été fermée.