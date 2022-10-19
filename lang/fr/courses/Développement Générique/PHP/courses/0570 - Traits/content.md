Depuis PHP 5.4.0, PHP supporte une manière de réutiliser le code appelée Traits.
Les traits sont un mécanisme de réutilisation de code dans un langage à héritage simple tel que PHP. Un trait tente de réduire certaines limites de l'héritage simple, en autorisant le développeur à réutiliser un certain nombre de méthodes dans des classes indépendantes. La sémantique entre les classes et les traits réduit la complexité et évite les problèmes typiques de l'héritage multiple et des Mixins.

Un trait est semblable à une classe, mais il ne sert qu'à grouper des fonctionnalités d'une manière intéressante. Il n'est pas possible d'instancier un Trait en lui-même. C'est un ajout à l'héritage traditionnel, qui autorise la composition horizontale de comportements, c'est-à-dire l'utilisation de méthodes de classe sans besoin d'héritage.

exemple : 

``` php
<?php
trait ezcReflectionReturnInfo {
	function getReturnType() { /*1*/ }
	function getReturnDescription() { /*2*/ }
}
 
class ezcReflectionMethod extends ReflectionMethod {
	use ezcReflectionReturnInfo;
	/* ... */
}
 
class ezcReflectionFunction extends ReflectionFunction {
	use ezcReflectionReturnInfo;
	/* ... */
}
?>
```

## Précédence

Une méthode héritée depuis une classe mère est écrasée par une méthode issue d'un Trait. L'ordre de précédence fait en sorte que les méthodes de la classe courante écrasent les méthodes issues d'un Trait, elles-mêmes surchargeant les méthodes héritées.

Exemple :

``` php
<?php
class Base {
	public function sayHello() {
		echo 'Hello ';
	}
}
 
trait SayWorld {
	public function sayHello() {
		parent::sayHello();
		echo 'World!';
	}
}
 
class MyHelloWorld extends Base {
	use SayWorld;
}
 
$o = new MyHelloWorld();
$o->sayHello();
?>
```

``` php
<?php
trait HelloWorld {
	public function sayHello() {
		echo 'Hello World!';
	}
}
 
class TheWorldIsNotEnough {
	use HelloWorld;
	public function sayHello() {
		echo 'Hello Universe!';
	}
}
 
$o = new TheWorldIsNotEnough();
$o->sayHello();
?>
```

``` php
<?php
trait Hello {
	public function sayHello() {
		echo 'Hello ';
	}
}
```

``` php
trait World {
	public function sayWorld() {
		echo 'World';
	}
}
 
class MyHelloWorld {
	use Hello, World;
	public function sayExclamationMark() {
		echo '!';
	}
}
 
$o = new MyHelloWorld();
$o->sayHello();
$o->sayWorld();
$o->sayExclamationMark();
?>
```

``` php
<?php
trait A {
	public function smallTalk() {
		echo 'a';
	}
	public function bigTalk() {
		echo 'A';
	}
}
 
trait B {
	public function smallTalk() {
		echo 'b';
	}
	public function bigTalk() {
		echo 'B';
	}
}
 
class Talker {
	use A, B {
		B::smallTalk insteadof A;
		A::bigTalk insteadof B;
	}
}
 
class Aliased_Talker {
	use A, B {
		B::smallTalk insteadof A;
		A::bigTalk insteadof B;
		B::bigTalk as talk;
	}
}
?>
```

## Changer la visibilité des méthodes

En utilisant la syntaxe “as”, vous pouvez aussi ajuster la visibilité de la méthode dans la classe qui l'utilise.

Exemple :

``` php
<?php
trait HelloWorld {
	public function sayHello() {
		echo 'Hello World!';
	}
}
 
// Modification de la visibilité de la méthode sayHello
class MyClass1 {
	use HelloWorld { sayHello as protected; }
}
 
// Utilisation d'un alias lors de la modification de la visibilité
// La visibilité de la méthode sayHello n'est pas modifiée
class MyClass2 {
	use HelloWorld { sayHello as private myPrivateHello; }
}
?>
```

## Traits composés depuis d’autres traits

Tout comme les classes peuvent utiliser des traits, d'autres traits le peuvent aussi. Un trait peut donc utiliser d'autres traits et hériter de tout ou d'une partie de ceux-ci.

Exemple :

``` php
<?php
trait Hello {
	public function sayHello() {
		echo 'Hello ';
	}
}
 
trait World {
	public function sayWorld() {
		echo 'World!';
	}
}
 
trait HelloWorld {
	use Hello, World;
}
 
class MyHelloWorld {
	use HelloWorld;
}
 
$o = new MyHelloWorld();
$o->sayHello();
$o->sayWorld();
?>
```

``` php
<?php
trait Hello {
	public function sayHelloWorld() {
		echo 'Hello'.$this->getWorld();
	}
	abstract public function getWorld();
}
 
class MyHelloWorld {
	private $world;
	use Hello;
	public function getWorld() {
		return $this->world;
	}
	public function setWorld($val) {
		$this->world = $val;
	}
}
?>
```

## Attributs statiques dans les traits

Des variables statiques peuvent être utilisées dans les méthodes d'un trait, mais ne peuvent être définies dans le trait. Les traits peuvent par contre déclarer des méthodes statiques pour la classe sous-jacente.

Exemple 1 :

``` php
<?php
trait Counter {
	public function inc() {
		static $c = 0;
		$c = $c + 1;
		echo "$c\n";
	}
}
 
class C1 {
	use Counter;
}
 
class C2 {
	use Counter;
}
 
$o = new C1(); $o->inc(); // echo 1
$p = new C2(); $p->inc(); // echo 1
?>
```

Exemple 2 :

``` php
<?php
trait StaticExample {
	public static function doSomething() {
		return 'Doing something';
	}
}
 
class Example {
	use StaticExample;
}
 
Example::doSomething();
?>
```

## Propriétés

Les traits peuvent aussi définir des propriétés.

Exemple 1 :

``` php
<?php
trait PropertiesTrait {
	public $x = 1;
}
 
class PropertiesExample {
	use PropertiesTrait;
}
 
$example = new PropertiesExample;
$example->x;
?>
```

Si un trait définit une propriété, alors la classe ne peut pas définir une propriété du même nom ; sinon, une erreur sera levée. Il s'agira d'une erreur de type ```E_STRICT``` si la définition dans la classe est compatible (même visibilité et valeur initiale), et d'une erreur fatale dans les autres cas.

Exemple 2 :

``` php
<?php
trait PropertiesTrait {
	public $same = true;
	public $different = false;
}
 
class PropertiesExample {
	use PropertiesTrait;
	public $same = true; // Strict Standards
	public $different = true; // Fatal error
}
?>
```