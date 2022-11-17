Un booléen est un type de donnée qui peut avoir seulement deux états : soit vrai (la valeur anglaise **true** est utilisée), soit faux (la valeur anglaise **false** est utilisée).

Avec les booléens, **true** vaut 1, tandis que **false** vaut 0.

## Les booléens dans du code PHP

### Les variables

Il est possible de créer des variables de type booléens. Pour ce faire, il suffit de passer la valeur **true** ou **false** à ces variables.

Exemple :

``` php
$var1 = true;
$var2 = false;
```

### Les conditions

Les conditions **if**, **else if**, ou encore **else** retournent, d’une manière ou d’une autre, toutes un booléen, car leur but est de tester si une condition est vraie ou fausse. 

Exemple :

``` php
$var1 = true;
if($var1 == true){
    echo("Oui");
}else{
    echo("Non");
}
```

L’exemple ci-dessus retourne oui, puisque ```$var1``` vaut **true**.