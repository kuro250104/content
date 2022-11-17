La priorité des opérateurs est l’ordre dans lequel les valeurs dans un script vont s'exécuter. Exemple, l’expression 2 + 8 * 3, le résultat est 26 et non 30, car comme en mathématique la multiplication à une priorité supérieur par rapport à une addition. Dans l’exemple ci-dessus, si on utilise des parenthèses la priorité va être forcé. Exemple, (2 + 8) *3 cette fois-ci le résultat est 30 et non 26.

Les opérateurs, dont la priorité est égale, qui ne sont pas associatifs, ne peuvent pas être utilisés entre eux. Exemple, 2 < 3 > 2 n’est pas autorisée en PHP, à l'inverse 2 <= 2 == 2 est autorisée, l’opérateur == a une précédence inférieur que l’opérateur <=.

L’utilisation des parenthèses dans une expression même si elles ne sont pas obligatoires peuvent permettre d’avoir une meilleure compréhension du code.

Exemple 1. Associativité :

```php
<?php
// (3 * 3) % 5 = 4
$a = 3 * 3 % 5;
// (true ? 0 : true) ? 1 : 2 = 2
$a = true ? 0 : true ? 1 : 2;

$a = 1;
$b = 2;
// $a = ($b += 3) -> $a = 5, $b = 5
$a = $b += 3;
?>
```

La priorité et l’association de l’opérateur ne déterminent que la façon dont les expressions sont regroupées. Dans cet exemple, les parenthèses permettent de définir la priorité d’exécution d’une expression.

Exemple 2. Ordre non défini

```php
<?php
$a = 5;
// affiche 6 ou 7
echo($a + $a++);
?>
```