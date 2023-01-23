Un programme informatique est un ensemble d'instructions exécutées par un ordinateur. 

En langage informatique, ces instructions sont appelées des déclarations.

Un programme JavaScript est donc un ensemble de déclarations exécutées par les navigateurs web.

## Les déclarations JavaScript

En JavaScript, le terme déclaration désigne : les valeurs, les opérateurs, les expressions, les mots clés et les commentaires. En JavaScript, ces déclarations sont appelées “code JavaScript”.

La plupart des programmes contiennent beaucoup de déclarations. Ces dernières sont exécutées une par une par le navigateur, dans l’ordre dans lequel elles sont écrites. 

Exemple : 

``` js
var chiffre = 2;
```

## Les points-virgules

À la fin d’une déclaration JavaScript, il faut ajouter un point virgule afin que le navigateur web comprenne qu’il arrive au bout de la déclaration. Lorsqu’ils sont séparés par des points-virgules, il est possible d’écrire plusieurs déclarations sur une même ligne.

__Remarque__ : Les points-virgules en fin de déclaration ne sont pas obligatoires, mais sont tout de même utilisés par convention et pour des raisons de lisibilité du code. 

Exemple :

``` js
var a = 1; b = 2; c = 3;
```

## Les espaces en JavaScript

Le langage JavaScript ignore les espaces lorsqu’il est exécuté. Ainsi, pour des raisons de lisibilité, est-il recommandé d’aérer le code en ajoutant des espaces, particulièrement autour des opérateurs (* / + -).

Exemple :

``` js
var a = 1;
var b = 2;
var addition : a + b;
```

## Taille des lignes et retours à la ligne

Pour des raisons de lisibilité du code, les développeurs s’arrangent pour que leurs lignes de codes ne dépassent pas 80 caractères. (entre 79 et 129 en fonction des règles des entreprises dans lesquelles ils travaillent) 

Afin de respecter cette règle, le meilleur endroit pour faire un retour à la ligne est après un opérateur.

Exemple :

``` js
document.getElementById("hello").innerHTML =
"Hello World !";
```

## Les blocs de code

Les déclarations JavaScript peuvent être rassemblées au sein d’un bloc de code. Les déclarations seront donc entourées par des accolades ouvrantes et fermantes.

Le but des blocs de code est que les déclarations qui s’y trouvent soient exécutées ensemble. 

La plupart du temps, le principe de bloc de code est utilisé par les fonctions.

Exemple :

``` js
function addition() {
    var a = 1;
    var b = 2;
    var total = a + b;
    document.getElementById(total);
}
```
