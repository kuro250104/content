Parcourir une grande collection de données en utilisant une construction en boucle telle que FOREACH nécessiterait une grande mémoire et un temps de traitement considérable. Avec les **générateurs**, il est possible d'itérer sur un ensemble de données sans ces frais généraux. Une fonction de générateur est similaire à une fonction normale. Toutefois, au lieu de l'instruction return dans une fonction, le générateur utilise le mot-clé ```yield``` pour être exécuté de manière répétée afin de fournir des valeurs à itérer.

Le mot-clé ```yield``` est le cœur du mécanisme du générateur. Même si son utilisation semble être semblable à celle de return, il n'arrête pas l'exécution de la fonction. Il fournit la valeur suivante pour l'itération et met en pause l'exécution de la fonction.

## Valeur de yield

Une boucle FOR qui donne chaque valeur de la variable de bouclage est utilisée dans une fonction de générateur.

### Exemple 1 

``` php
<?php
function squaregenerator(){
   for ($i=1; $i<=5; $i++){
      yield $i*$i;
   }
}
$gen=squaregenerator();
foreach ($gen as $val){
   echo $val . " ";
}
?>
```

La réponse est semblable à une boucle FOREACH normale.

### Réponse 1

``` php
1 4 9 16 25
```

La fonction ```range()``` de PHP retourne une liste d'entiers de début à fin avec un intervalle de ```$step``` entre chaque nombre. Le programme suivant implémente ```range()``` comme générateur.

### Example 2

``` php
<?php
function rangegenerator($start, $stop, $step){
   for ($i=$start; $i<=$stop; $i+=$step){
      yield $i;
   }
}
foreach (rangegenerator(2,10,2) as $val){
   echo $val . " ";
}
?>
```

### Réponse 2

La réponse est similaire à range(2,20,2).

``` php
2 4 6 8 10
```

Un tableau associatif peut aussi être implémenté comme générateur :

### Example 3

``` php
<?php
function arrgenerator($arr){
   foreach ($arr as $key=>$val){
      yield $key=>$val;
   }
}
$arr=array("one"=>1, "two"=>2, "three"=>3, "four"=>4);
$gen=arrgenerator($arr);
foreach ($gen as $key=>$val)
echo $key . "=>" . $val . "\n";
?>
```

### Réponse 3

``` php
one=>1
two=>2
three=>3
four=>4
```