Une fonction anonyme est une fonction sans nom défini par l'utilisateur. Une telle fonction est également appelée **closure** ou fonction **lambda**. Parfois, vous pouvez vouloir une fonction pour un usage unique. La fermeture est une fonction anonyme qui se ferme sur l'environnement dans lequel elle est définie. L'utilisation la plus courante de la fonction anonyme est la création d'une fonction de rappel en ligne.

## Syntaxe

``` php
$var=function ($arg1, $arg2) { return $val; }
```

- Il n'y a pas de nom de fonction entre le mot-clé function et la parenthèse ouvrante.
- Il y a un point-virgule après la définition de la fonction, car les définitions de fonctions anonymes sont des expressions.
- La fonction est assignée à une variable, et appelée plus tard en utilisant le nom de la variable.
- Lorsqu'elle est transmise à une autre fonction qui peut l'appeler ultérieurement, elle est appelée "callback".
- La fonction est retournée depuis une fonction externe afin qu'elle puisse accéder aux variables de la fonction externe. C'est ce qu'on appelle une fermeture.

## Exemple de fonction anonyme

### Exemple

``` php
<?php
$var = function ($x) {return pow($x,3);};
echo "cube of 3 = " . $var(3);
?>
```

### Réponse

``` php
cube of 3 = 27
```

## Fonction anonyme callback

Dans l'exemple suivant, une fonction anonyme est utilisée comme argument pour une fonction intégrée ```usort()```. La fonction ```usort()``` trie un tableau donné en utilisant une fonction de comparaison.

### Exemple

``` php
<?php
$arr = [10,3,70,21,54];
usort ($arr, function ($x , $y) {
    return $x > $y;
});
foreach ($arr as $x){
    echo $x . "\n";
}
?>
```

### Réponse

``` php
3
10
21
54
70
```

## Fonction anonyme closure

Closure est également une fonction anonyme qui peut accéder à des variables en dehors de sa portée à l'aide du mot-clé use.

### Exemple

``` php
<?php
$maxmarks=300;
$percent=function ($marks) use ($maxmarks) {return $marks*100/$maxmarks;};
echo "marks=285 percentage=". $percent(285);
?>
```

### Réponse

``` php
marks=285 percentage=95
```