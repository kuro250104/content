L'opérateur de résolution de portée (aussi appelé Paamayim Nekudotayim) ou, en termes plus simples, le symbole "double deux-points" (::), fournit un moyen d'accéder aux membres static ou constant, ainsi qu'aux propriétés ou méthodes surchargées d'une classe.

Lorsque vous référencez ces éléments en dehors de la définition de la classe, utilisez le nom de la classe.

Depuis PHP 5.3.0, il est possible de référencer une classe en utilisant une variable. La valeur de la variable ne peut être un mot-clé (e.g. self, parent et static).

Paamayim Nekudotayim pourrait au premier abord sembler être un choix étrange pour nommer un double deux-points. Cependant, au moment de l'écriture du Zend Engine 0.5 (qui faisait fonctionner PHP 3), c'est le nom qui a été choisi par l'équipe Zend. En fait, cela signifie un double deux-points en hébreu.

Exemple 1 : en dehors de la définition de la classe

``` php
<?php
class MyClass {
	const CONST_VALUE = 'Une valeur constante';
}
 
$classname = 'MyClass';
echo $classname::CONST_VALUE; // Depuis PHP 5.3.0
 
echo MyClass::CONST_VALUE;
```

Trois mots-clés spéciaux, self, parent, et static sont utilisés pour accéder aux propriétés ou aux méthodes depuis la définition de la classe.

Exemple 2 : depuis la définition de la classe

``` php
<?php
class OtherClass extends MyClass
{
	public static $my_static = 'variable statique';
 
	public static function doubleColon() {
		echo parent::CONST_VALUE . "\n";
		echo self::$my_static . "\n";
	}
}
 
$classname = 'OtherClass';
echo $classname::doubleColon(); // Depuis PHP 5.3.0
 
OtherClass::doubleColon();
?>
```

Lorsqu'une classe héritant d'une autre redéfinit une méthode de sa classe parente, PHP n'appellera pas la méthode de la classe parente. Il appartient à la méthode dérivée d'appeler la méthode d'origine en cas de besoin. Cela est également valable pour les définitions des constructeurs et destructeurs, la surcharge, et les définitions de méthodes magiques.

Exemple 3 : appel d’une méthode parent

``` php
<?php
class MyClass
{
	protected function myFunc() {
 		echo "MyClass::myFunc()\n";
       }
}
 
class OtherClass extends MyClass
{
	// Surcharge de la définition parente
	public function myFunc() {
 
	  // Mais appel de la méthode parente
	  parent::myFunc();
	  echo "OtherClass::myFunc()\n";
       }
}
 
$class = new OtherClass();
$class->myFunc();
?>
```