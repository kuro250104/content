Cet opérateur est disponible depuis la version 7.0 de PHP. Il a la même capacité que la fonction ```inset()``` et renvoie la variable spécifiée si elle existe, sinon c’est la valeur précisée après les deux points d’interrogation (**??**) qui est renvoyée.

De plus, cet opérateur peut être utilisé plusieurs fois de suite. 

## Utilisation

Les différents exemples ci-dessous permettent d’illustrer l’utilisateur de cet opérateur :

``` php
$variable = NULL;
$seconde_variable = $variable ?? "Hello"; // Retourne Hello

$variable = "Voiture";
$seconde_variable = $variable ?? "Camion"; // Retourne Voiture

$variable = NULL;
$seconde_variable = "Pomme";
$variable_finale = $variable ?? $seconde_variable ?? "Fraise"; // Retourne Pomme
```