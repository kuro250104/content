Un des piliers de la POO de PHP est le fait que les "objets sont passés par référence par défaut". Ce n'est pas complètement vrai. Cette section rectifie cette généralisation avec quelques exemples.

Une référence PHP est un alias, qui permet à deux variables différentes de représenter la même valeur. Dans PHP, une variable objet ne contient plus l'objet en lui-même comme valeur. Elle contient seulement un identifiant d'objet, qui permet aux accesseurs d'objets de trouver cet objet. Lorsque l'objet est utilisé comme argument, retourné par une fonction, ou assigné à une autre variable, les différentes variables ne sont pas des alias : elles contiennent des copies de l'identifiant, qui pointent sur le même objet.

exemple :

``` php
<?php
class A {
    public $foo = 1;
}  

$a = new A;
$b = $a;     // $a et $b sont des copies du même identifiant
             // ($a) = ($b) = <id>
$b->foo = 2;
echo $a->foo."\n";


$c = new A;
$d = &$c;    // $c et $d sont des références
             // ($c,$d) = <id>

$d->foo = 2;
echo $c->foo."\n";


$e = new A;

function foo($obj) {
    // ($obj) = ($e) = <id>
    $obj->foo = 2;
}

foo($e);
echo $e->foo."\n";

?>
```

L'exemple ci-dessus va afficher :

``` php
2
2
2
```