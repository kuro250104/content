Les opérateurs combinés permettent d’utiliser la valeur d’une variable dans une expression et d’affecter le résultat de cette expression à cette variable.

Liste des opérateurs combinés et de leurs équivalents :

- ```$a += expression```, est équivalent à, ```$a = $a + expression``` 
- ```$a -= expression```, est équivalent à, ```$a = $a - expression```
- ```$a *= expression```, est équivalent à, ```$a = $a * expression```
- ```$a /= expression```, est équivalent à, ```$a = $a / expression```
- ```$a %= expression```, est équivalent à, ```$a = $a % expression```
- ```$a .= expression```, est équivalent à, ```$a = $a . expression```

Exemple :

```php
<?php
$a = 2;
$a += 10; 
// affecte la valeur 12 à la variable $a ce qui correspond à l’expression '$a = $a + 10'
$b = "Bonjour ";
$b .= "Martin";  
// affecte la valeur "Bonjour Martin" à la variable $b ce qui correspond à l’expression $b = $b . " Martin"
?>
```