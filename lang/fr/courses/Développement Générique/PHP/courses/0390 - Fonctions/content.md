La vraie puissance de PHP vient de ses fonctions. PHP a plus de 1000 fonctions intégrées, et en plus vous pouvez créer vos propres fonctions personnalisées.

## Fonctions intégrées

PHP a plus de 1000 fonctions intégrées qui peuvent être appelées directement, à partir d'un script, pour effectuer une tâche spécifique.

Veuillez consulter notre référence PHP pour un aperçu complet des fonctions intégrées de PHP.

Lien : https://www.php.net/manual/fr/indexes.functions.php

## Fonctions définies par l’utilisateur

Outre les fonctions PHP intégrées, il est possible de créer vos propres fonctions.

- Une fonction est un bloc d'instructions qui peut être utilisé à plusieurs reprises dans un programme.
- Une fonction ne s'exécutera pas automatiquement lors du chargement d'une page.
- Une fonction sera exécutée par un appel à la fonction.

## Créer une fonction définie par l’utilisateur

Une déclaration de fonction définie par l'utilisateur commence par le mot ```function``` :

syntaxe :

``` php
function functionName() {
  // code
}
```

exemple :

``` php
<?php
function writeMsg() {
  echo "Hello world!";
}

writeMsg(); // appel de la fonction
?>
```

## Arguments de fonction

Les informations peuvent être transmises aux fonctions via des arguments. Un argument est comme une variable.

Les arguments sont spécifiés après le nom de la fonction, à l'intérieur des parenthèses. Vous pouvez ajouter autant d'arguments que vous le souhaitez, séparez-les simplement par une virgule.

L'exemple suivant a une fonction avec un argument (```$fname```). Lorsque la fonction ```familyName()``` est appelée, nous passons également un nom (par exemple Marie), et le nom est utilisé à l'intérieur de la fonction, qui génère plusieurs prénoms différents, mais un nom de famille égal :

``` php
<?php
function familyName($fname) {
    echo "$fname Dupont.<br>";
}

familyName("Marie");
familyName("Pierre");
familyName("Paul");
familyName("Louis");
familyName("Emma");
?>
```

L'exemple suivant a une fonction avec deux arguments ($fname et $year) :

``` php
<?php
function familyName($fname, $year) {
    echo "$fname Dupont. Né en $year <br>";
}

familyName("Marie", "1975");
familyName("Pierre", "1978");
familyName("Louis", "1983");
?>
```

## Arguments par référence

En PHP, les arguments sont généralement transmis par valeur, ce qui signifie qu'une copie de la valeur est utilisée dans la fonction et que la variable qui a été transmise à la fonction ne peut pas être modifiée.

Lorsqu'un argument de fonction est passé par référence, les modifications apportées à l'argument modifient également la variable qui a été transmise. Pour transformer un argument de fonction en référence, l'opérateur & est utilisé :

``` php
<?php
function add_five(&$value) {
    $value += 5;
}

$num = 2;
add_five($num);
echo $num;
?>
```

## Argument par défaut 

L'exemple suivant montre comment utiliser un paramètre par défaut. Si nous appelons la fonction ```setHeight()``` sans arguments, elle prend la valeur par défaut comme argument :

``` php
<?php 
declare(strict_types=1);
function setHeight(int $minheight = 50) {
    echo "The height is : $minheight <br>";
}

setHeight(350);
setHeight();
setHeight(135);
setHeight(80);
?>
```

## Typer les fonctions

Dans l'exemple ci-dessus, notez que nous n'avons pas eu à dire à PHP quel type de données est la variable.

PHP associe automatiquement un type de données à la variable, en fonction de sa valeur. Étant donné que les types de données ne sont pas définis au sens strict, vous pouvez faire des choses comme ajouter une chaîne à un entier sans provoquer d'erreur.

En PHP 7, les déclarations de type ont été ajoutées. Cela nous donne la possibilité de spécifier le type de données attendu lors de la déclaration d'une fonction, et en ajoutant la déclaration strict, cela générera une "Erreur fatale" si le type de données ne correspond pas.

Dans l'exemple suivant, nous essayons d'envoyer à la fois un nombre et une chaîne à la fonction sans utiliser ```strict``` :

exemple :

``` php
<?php
function addNumbers(int $a, int $b) {
    return $a + $b;
}
echo addNumbers(5, "5 days");
?>
```

Pour spécifier, ```strict``` nous devons définir ```declare(strict_types=1)```. Cela doit être sur la toute première ligne du fichier PHP.

Dans l'exemple suivant, nous essayons d'envoyer à la fois un nombre et une chaîne à la fonction, mais ici nous avons ajouté la ```strict``` déclaration strict :

``` php
<?php declare(strict_types=1);

function addNumbers(int $a, int $b) {
    return $a + $b;
}
echo addNumbers(5, "5 days");
?>
```

## Déclaration du type de retour

PHP 7 prend également en charge les déclarations de type pour l'instruction ```return```. Comme avec la déclaration de type pour les arguments de fonction, en activant l'exigence stricte, une "erreur fatale" sera générée en cas de non-concordance de type.

Pour déclarer un type pour le retour de la fonction, ajoutez deux points (:) et le type juste avant l'accolade ouvrante ( {) lors de la déclaration de la fonction.

Dans l'exemple suivant, nous spécifions le type de retour ```float``` pour la fonction :

``` php
<?php declare(strict_types=1); 
function addNumbers(float $a, float $b) : float {
  return $a + $b;
}
echo addNumbers(1.2, 5.2);
?>
```