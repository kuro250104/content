La superglobale ```$_GET``` est une variable qui est utilisée pour récupérer des données d’un formulaire HTML soumis avec une méthode get, de plus par défaut un formulaire est en méthode get. ```$_GET``` permet aussi de récupérer des informations contenues dans l’URL.

Exemple :

``` html
<a href="get.php?theme=js&route=microlead.fr">Test méthode get</a>
```

Si l’utilisateur clique sur le lien, les paramètres ```theme``` et ```route``` sont envoyés à ```get.php```, on peut donc récupérer ces valeurs avec ```$_GET```.

``` php
<?php
echo "theme " . $_GET['theme'] . "+" . $_GET['route'];
?>
```

Ce code nous renvoie :

``` php
theme js + microlead.fr
```