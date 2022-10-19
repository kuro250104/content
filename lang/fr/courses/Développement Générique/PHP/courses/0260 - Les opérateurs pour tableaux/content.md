En PHP, il existe de nombreux opérateurs qui fonctionnent sur plus d'un tableau, pour obtenir l'union de deux tableaux, pour vérifier l'identité, l'égalité, etc.

Les différents opérateurs pour les tableaux sont :

- ```$a + $b``` : type “Union”, fusionne ```$a``` et ```$b```,
- ```$a == $b``` : type "Égalité", renvoi vrai (true) si ```$a``` et ```$b``` ont les mêmes paires de valeurs,
- ```$a === $b``` : type “Identique”, renvoi vrai (true) si ```$a``` et ```$b``` ont les mêmes paires de valeurs et dans le même ordre et du même type,
- ```$a != $b``` : type “Inégalité”, renvoi vrai (true) si ```$a``` n’est pas égal à ```$b```,
- ```$a <> $b``` : type “Inégalité”, renvoi vrai (true) si ```$a``` n’est pas égal à ```$b```,
- ```$a !== $b``` : type “Non-identique”, renvoi vrai (true) si ```$a``` n’est pas identique a ```$b```.

Exemple 1 :

``` php
<?php
$a = array("a" => "abricot", "b" => "cerises");
$b = array("a" =>"poire", "b" => "banane", "c" => "orange");
 
$c = $a + $b; // type “Union”
var_dump($c);
 
$c = $b + $a; // type “Union”
var_dump($c);
?>
```

Dans cet exemple, le premier ```var_dump()``` renvoi :

``` php
array(3) {
    ["a"] => string(7) "abricot"
    ["b"] => string(7) "cerises"
    ["c"] => string(6) "orange"
}
```

Le second ```var_dump()``` renvoi :

``` php
array(3) {
    ["a"] => string(5) "poire"
    ["b"] => string(6) "banane"
    ["c"] => string(6) "orange"
}
```

Exemple 2 :

``` php
<?php
$a = array("fraise", "ananas");
$b = array(1 => "ananas", "0" => "fraise");
 
var_dump($a == $b);
var_dump($a === $b); 
?>
```

Dans cet exemple, le premier ```var_dump()``` renvoi vrai “true” et le deuxième ```var_dump()``` renvoi faux “false”.