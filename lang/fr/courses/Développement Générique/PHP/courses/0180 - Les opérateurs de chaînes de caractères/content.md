Les 2 opérateurs de chaînes de caractères (*string*) sont :

- ```.``` : cet opérateur retourne la concaténation de ces deux arguments,
- ```.=``` : cet opérateur et l’opérateur d’affectation concaténant.

Exemple :

``` php
<?php
$a = "Prénom : ";
$b = $a . "Elon"; 

$a = "Nom : ";
$a .= "Musk"; 
?>
```

Dans cet exemple, la variable ```$b``` contient “**Prénom : Elon**” et la variable ```$a``` contient “**Nom : Musk**”.

Exemple 2 :

``` php
<?php
$nom = "Besos";
$prenom = "Jeff";
$a = "Prénom : " . $prenom . " et nom : " . $nom;
?>
```

Dans cet exemple, la variable ```$a``` contient “**Prénom : Jeff et nom : Besos**”.