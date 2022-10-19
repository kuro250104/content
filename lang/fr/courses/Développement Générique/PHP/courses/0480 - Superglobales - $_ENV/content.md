```$_ENV``` est une autre superglobale en PHP. Elle stocke les variables d'environnement disponibles pour le script courant. ```$HTTP_ENV_VARS``` contient également les mêmes informations, mais ce n'est pas une superglobale, et elle est maintenant obsolète.

Les variables d'environnement sont importées dans l'espace de noms global. La plupart de ces variables sont fournies par le shell sous lequel le parseur PHP est exécuté. Par conséquent, la liste des variables d'environnement peut être différente sur différentes plateformes.

Ce tableau inclut par ailleurs les variables CGI dans le cas où PHP est exécuté en tant que module serveur ou processeur CGI.

## getenv

La bibliothèque PHP possède la fonction ```getenv()``` pour récupérer la liste de toutes les variables d'environnement ou la valeur d'une variable d'environnement spécifique.

Le script suivant affiche les valeurs de toutes les variables d'environnement disponibles :

``` php
<?php
$arr=getenv();
foreach ($arr as $key=>$val)
echo "$key=>$val
";
?>
```

Pour obtenir la valeur d'une variable spécifique, utilisez son nom comme argument pour la fonction ```getenv()```.

### Exemple

``` php
<?php
echo "Chemin : " . getenv("PATH");
?>
```

### Réponse

``` php
Chemin : /usr/bin:/bin
```

## putenv

PHP dispose également de la fonction ```putenv()``` pour créer une nouvelle variable d'environnement. La variable d'environnement n'existera que pour la durée de la requête en cours.

La modification de la valeur de certaines variables d'environnement doit être évitée. Par défaut, les utilisateurs ne pourront définir que les variables d'environnement qui commencent par ```PHP_``` (par exemple, ```PHP_FOO=BAR```).

La directive ```safe_mode_protected_env_vars``` du php.ini contient une liste de variables d'environnement délimitées par des virgules, que l'utilisateur final ne pourra pas modifier en utilisant putenv().

### Exemple

``` php
<?php
putenv("PHP_TEMPUSER=INVITE");
echo "Utilisateur temporaire : " . getenv("PHP_TEMPUSER");
?>
```

### Réponse

Le navigateur affichera le résultat suivant :

``` php
Utilisateur temporaire : INVITE
```