La boucle FOREACH de PHP est une fonction native qui boucle un morceau de code pour chaque clé/valeur d'un tableau jusqu'à ce qu'elle atteigne le dernier élément du tableau. Elle ne fonctionne uniquement sur un tableau, donc elle ne fonctionne pas avec des expressions ou tout autre type de valeurs d'une variable autre que des tableaux.

Voici la syntaxe d'une boucle FOREACH :

``` php
foreach( $array as $var ){ 
    //code à exécuter
}
```

La principale différence entre l'instruction FOREACH et les boucles WHILE ou FOR est la suivante : les boucles WHILE et FOR continuent jusqu'à ce qu'une condition soit remplie. En revanche, la boucle FOREACH continuera jusqu'à ce qu'elle ait parcouru tous les éléments d'un tableau.

Pour chaque boucle, la valeur de la clé actuelle du tableau est affectée à $value et le pointeur du tableau est déplacé en interne vers la clé suivante jusqu'à ce que la dernière clé soit atteinte.

Voici un exemple simple qui illustre le fonctionnement de l'instruction FOREACH :

``` php
$season = array("été","printemps","hiver","automne"); 
foreach( $season as $value ){ 
    echo("La saison est: $value<br />");
}
```

Dans cet exemple, le résultat renvoyé est :

``` php
La saison est été
La saison est printemps
La saison est hiver
La saison est automne
```