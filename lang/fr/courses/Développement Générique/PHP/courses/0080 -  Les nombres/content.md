Les nombres sont composés d’un ou plusieurs chiffres allant de 0 à 9. Un nombre peut être entier ou à virgule. En informatique, un nombre à virgule est appelé un nombre flottant ou *float*, en anglais. 

## Les nombres dans du code PHP

En PHP, il existe principalement deux types de nombres : les nombres entiers (ou *integer*, en anglais), et les nombres décimaux, également appelés flottants (ou *float* en anglais).

### Les nombres entiers

Les nombres entiers sont des nombres n’ayant pas de virgules. En anglais, ils sont appelés *integer*, et sont, dans les différents langages informatiques existants, raccourcis sous le nom de **int**.

Par exemple, le nombre 20 est considéré comme un **int** par PHP.

### Les nombres décimaux

Les nombres à virgules, appelés par leur nom anglais *float* représentent tous les nombres décimaux existants. 

Par exemple, 20.6 est un float.

__Remarque__ : En PHP, comme pour beaucoup d’autres langages, lorsqu’un nombre décimal est écrit, le point est utilisé comme virgule. Ainsi, 20.6 est reconnu par PHP, tandis que 20,6 ne l’est pas.

### Conversions

Il y a des situations dans lesquelles un **int** a besoin d’être converti en **float**, et inversement. Le langage PHP permet cela en mettant à disposition les deux fonctions suivantes : 

- ```intval()``` : cette fonction prend en paramètre le nombre décimal à convertir en nombre entier et retourne le résultat de la conversion
- ```floatval()``` : prend en paramètre le nombre entier à convertir en **float** et retourne le résultat de la conversion

Exemple :

``` php
intval(45.1); // Retourne 45
floatval(124); // Retourne 124.0
```