La superglobale ```$GLOBALS``` est utilisée pour créer une variable qui sera accessible depuis n’importe quel script PHP. PHP par défaut dans un tableau appelé ```$GLOBALS[index]```. L’index est simplement le nom de la variable.

Exemple :

``` php
<?php
$a = 75;
$b = 25;
 
function somme() {
  $GLOBALS['c'] = $GLOBALS['a'] + $GLOBALS['b'];
}
 
somme();
echo $c;
?>
```

Dans cet exemple, ```$c``` est une variable présente dans le tableau ```$GLOBALS```, elle est donc accessible depuis l'extérieur de la fonction.