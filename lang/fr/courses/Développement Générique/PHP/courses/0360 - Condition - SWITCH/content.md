La boucle ```switch``` permet d’économiser du code, car elle évite au développeur d’écrire plusieurs répétitions de ```else if```. Cependant, cette boucle est l’équivalent de plusieurs instructions ```if``` et permet de comparer une variable avec plusieurs possibilités de valeurs différentes et d’exécuter du code correspondant à une valeur précise. 

## Utilisation

### Syntaxe

La boucle ```switch``` s’écrit de la manière suivante :

``` php
switch(variable) {
    case 1: 
    // Code à exécuter
    break;

    case 2:
    // Code à exécuter
    break;

    default :
    // Code à exécuter
}
```

#### case

Le mot-clé ```case``` permet de préciser une valeur. En d’autres termes, ```case 1``` signifie “**si la valeur de la variable est 1**”, alors il faut exécuter le code qui suit. Il passe ensuite au ```case``` suivant.

#### break

Ce mot-clé permet de sortir de la boucle lorsque la valeur du ```case``` correspond à celle de la variable. Le programme exécute le code et quitte la boucle. 

L’oubli d’un ```break``` aura pour conséquence de faire passer le programme au case suivant, quand bien même la valeur correspond à celle de la variable. 

*Remarque : Le ```break``` est inutile pour la dernière instruction de la boucle, car le programme sortira de la boucle quoi qu’il arrive.*

#### default

Ce mot-clé permet d’exécuter un morceau de code “par défaut” si aucune des valeurs ne correspond à celle de la variable. 

De manière générale, pour des raisons de logique et de lisibilité du code, le bloc ```default``` est placé comme dernière instruction dans la boucle ; cependant, il sera exécuté correctement même s’il est placé en premier.

## Exemples

Ci-dessous, quelques exemples afin d’illustrer l’utilisation de la boucle ```switch``` :

``` php
$variable = "Voiture"
switch ($variable) {
    case "Camion":
        echo "$variable est un camion.";
    break;
    case "Voiture":
        echo "$variable est une voiture.";
    break;
} // Retourne "$variable est une voiture."

$variable = "Tomate"
switch ($variable) {
case "Courgette":
    echo "$variable est une courgette.";
break;
case "Carotte":
    echo "$variable est une carotte.";
break;
case "Champignon":
    echo "$variable est un champignon.";
break;
case "Tomate":
    echo "$variable est une tomate.";
break;
case "Radis":
    echo "$variable est un radis.";
break;
} // Retourne $variable est une tomate.
```