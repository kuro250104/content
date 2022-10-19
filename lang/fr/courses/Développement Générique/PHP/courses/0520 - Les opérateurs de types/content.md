Les opérateurs de types sont utilisés pour déterminer si une variable est un objet instancié d’une certaine classe. Pour réaliser cela on utilise ```instanceof```.

Exemple 1. instanceof avec des classes :

``` php
<?php
class MaClasse
{
}
class CeciNestPasMaClasse
{
}
$a = new MaClasse;

var_dump($a instanceof MaClasse);
var_dump($a instanceof CeciNestPassMaClasse);
?>
```

Dans cet exemple, le premier ```var_dump()``` renvoi vrai (true) alors que le second ```var_dump()``` renvoi faux (false).

Exemple 2. instanceof avec des classes héritées :

``` php
<?php
class ClassParent
{
}
class MaClass extends ParentClass
{
}
$a = new MaClass;

var_dump($a instanceof MaClass);
var_dump($a instanceof ClassParent);
?>
```

Dans cet exemple, le premier ```var_dump()``` renvoi vrai (true) et le second ```var_dump()``` renvoi vrai (true) aussi.

Exemple 3. instanceof pour vérifier que l’objet n’est pas une instance de la classe :

``` php
<?php
class MaClass
{
}
$a = new MaClass;
var_dump(!($a instanceof stdClass));
?>
```

Dans cet exemple, le ```var_dump()``` renvoi vrai (true).

Exemple 4. instanceof pour une interface :

``` php
<?php
interface MonInterface
{
}
class MaClass implements MonInterface
{
}
$a = new MaClass;

var_dump($a instanceof MaClass);
var_dump($a instanceof MonInterface);
?>
```

Dans cet exemple, les deux ```var_dump()``` renvoient vrai (true).

Exemple 5 : instanceof pour d’autres types :

``` php
<?php
$a = 1;
$b = NULL;
var_dump($a instanceof stdClass);
var_dump($b instanceof stdClass);
var_dump(FALSE instanceof stdClass);
?>
```

L’exemple du dessus donne le résultat suivant :

``` php
bool(false)
bool(false)
bool(false)
PHP Fatal error:  instanceof expects an object instance, constant given
```