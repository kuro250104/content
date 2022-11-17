Les conditions ternaires permettent l’exécution d’une partie d’un code. Bien qu’un tant soit peu difficiles à comprendre au début, et pas forcément très lisibles au premier rapport, le principal avantage d’une condition ternaire est de raccourcir certaines instructions if.

## Utilisation

L’utilité principale d’une condition ternaire est d’économiser des lignes de codes - et, par conséquent, de gagner du temps - en raccourcissant au maximum l’écriture d’une condition ```if```.

### Syntaxe

Voici comment s’écrit une condition ```if``` traditionnelle :

```php
if({IF}) {
    $var = {IF};
} else {
    $var = 1;
}
```

Cette condition if est parfaitement lisible, mais un peu longue à écrire pour le peu d’instructions qu’elle a à exécuter.

Ainsi est-il possible de raccourcir cette condition en utilisant l’écriture ternaire, dont voici la syntaxe :

```php
$var = {IF} ? {THEN} : {ELSE};
```

Depuis la version 5.3 de PHP, il est possible de raccourcir davantage cette écriture :

```php
$var = {IF} ?: {ELSE};
```

## Exemple

Ci-dessous, un exemple utilisant d’abord une condition ```if```, puis l’écriture **ternaire**, puis l’écriture ternaire de la version 5.3 de PHP :

### En utilisant l’instruction IF

```php
$variable = "Camion";
if($variable == "Voiture") {
    $seconde_variable = $variable;
} else {
    $seconde_variable = "Avion";
}
// Retourne Avion
```

### Écriture ternaire

```php
$variable = "Camion";
$seconde_variable = $variable == "Voiture" ? $variable : "Avion";
// Retourne Avion
```

### Écriture ternaire avec la version 5.3 de PHP

```php
$variable = "Camion";
$seconde_variable = $variable == "Voiture" ?: "Avion";
// Retourne Avion
```