L’opérateur de contrôle d’erreur est le symbole ```@```. Quand cet opérateur est ajouté en préfixe d’une expression, les diagnostics d’erreurs qui peuvent être générés par cette expression seront ignorés.

Si ```set_error_handler()``` est défini comme gestionnaire d’erreur personnalisé, alors il sera quand même appelé même si le diagnostic a été ignoré. Le gestionnaire d’erreur personnalisé doit appeler ```error_reporting()``` et vérifier que l’opérateur ```@``` est utilisé.

exemple :

``` php
<?php
function my_error_handler($err_no, $err_msg, $filename, $linenum) {
    if (!(error_reporting() & $err_no)) {
        return false; // Ignoré
    }
}
?>
```

Les messages d’erreurs générés par l’expression sont disponibles dans l’élément “message” du tableau retourné par la fonction ```error_get_last()```. Le résultat de la fonction change à chaque erreur.

exemple :

``` php
<?php
/* Erreur voulu (ce fichier n'existe pas): */
$mon_fichier = @file ('non_persistent_file') or
    die ("Impossible d'ouvrir le fichier : L'erreur est : '" . error_get_last()['message'] . "'");

?>
```

L’opérateur ```@``` ne fonctionne qu’avec les expressions (exemples : devant les variables, les appels de fonctions, etc), il ne fonctionne pas fonctionner devant les définitions de fonctions ou de classes, ou de structure conditionnelle (exemples : if, foreach,...).
