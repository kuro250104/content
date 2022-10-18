L’opération d’assignation est le signe ```=```. Contrairement à ce que l’on peut penser, ce signe ne veut pas dire “égale à”, il signifie que l’opérande de gauche est affectée par la valeur de l’expression de droite qui est située après le signe ```=```.

Exemple :

``` php
<?php
$a = ($b = 2) + 3;
// $a est maintenant égal à 5, et $b vaut 2.
```

Il est également possible d’assigner simplement une valeur, afin de la réutiliser par la suite : 

``` php
<?php
$maVariable = "Hello World !";
// $maVariable peut être modifiée par la suite, ou bien utilisée simplement pour afficher son contenu.
```

Chaque affectation de valeur remplacera la précédente, de telle sorte que : 

``` php
<?php
$a = 3;
// $a vaut 3
$a = 4;
// $a vaut 4;
```