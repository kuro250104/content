L'héritage en POO c’est lorsqu'une classe dérive d'une autre classe.

La classe enfant héritera de toutes les propriétés et méthodes publiques et protégées de la classe parente. De plus, il peut avoir ses propres propriétés et méthodes.

Une classe héritée est définie à l'aide du mot-clé ```extends```.

exemple :

``` php
<?php
class Fruit {
  public $name;
  public $color;
  public function __construct($name, $color) {
	$this->name = $name;
	$this->color = $color;
  }
  public function intro() {
    echo "The fruit is {$this->name} and the color is {$this->color}.";
  }
}

class Strawberry extends Fruit {
  public function message() {
    echo "Am I a fruit or a berry? ";
  }
}
$strawberry = new Strawberry("Strawberry", "red");
$strawberry->message();
$strawberry->intro();
?>
```

Dans cet exemple, le résultat renvoyé est :

``` php
Am I a fruit or a berry? The fruit is Strawberry and the color is red.
```

La classe Fraise est héritée de la classe Fruit.

Cela signifie que la classe Strawberry peut utiliser les propriétés publiques ```$name``` et ```$color``` ainsi que les méthodes publiques ```__construct()``` et ```intro()``` de la classe Fruit en raison de l'héritage.

La classe Strawberry a aussi sa propre méthode : ```message()```.

## Héritage et modificateur d’accès protégé

Les propriétés ```protected``` ou les méthodes sont accessibles au sein de la classe et par les classes dérivées de cette classe. 

exemple :

``` php
<?php
class Fruit {
  public $name;
  public $color;
  public function __construct($name, $color) {
	$this->name = $name;
	$this->color = $color;
  }
  protected function intro() {
    echo "The fruit is {$this->name} and the color is {$this->color}.";
  }
}

class Strawberry extends Fruit {
  public function message() {
    echo "Am I a fruit or a berry? ";
  }
}


$strawberry = new Strawberry("Strawberry", "red"); 
$strawberry->message();
$strawberry->intro();
?>
```

Dans cet exemple, le résultat renvoyé est :

``` php
Am I a fruit or a berry?
```

Dans l'exemple ci-dessus, nous voyons que si nous essayons d'appeler une méthode ```protected``` (```intro()```) depuis l'extérieur de la classe, nous recevons une erreur. Les méthodes ```public``` fonctionnent bien !

## Remplacement des méthodes héritées

Les méthodes héritées peuvent être remplacées en définissant les méthodes (utiliser le même nom) dans la classe enfant.

L'exemple ci-dessous. Les méthodes ```__construct()``` et ```intro()``` de la classe enfant (Strawberry) remplaceront les méthodes ```__construct()``` et ```intro()``` de la classe parent (Fruit) :

``` php
<?php
class Fruit {
  public $name;
  public $color;
  public function __construct($name, $color) {
	$this->name = $name;
	$this->color = $color;
  }
  public function intro() {
    echo "The fruit is {$this->name} and the color is {$this->color}.";
  }
}

class Strawberry extends Fruit {
  public $weight;
  public function __construct($name, $color, $weight) {
	$this->name = $name;
	$this->color = $color;
	$this->weight = $weight;
  }
  public function intro() {
    echo "The fruit is {$this->name}, the color is {$this->color}, and the weight is {$this->weight} gram.";
  }
}

$strawberry = new Strawberry("Strawberry", "red", 50);
$strawberry->intro();
?>
```

Dans cet exemple, le résultat renvoyé est :

``` php
The fruit is Strawberry, the color is red, and the weight is 50 gram.
```

## Le mot clé final

Le mot-clé ```final``` peut être utilisé pour empêcher l'héritage de classe ou pour empêcher la substitution de méthode.

L'exemple suivant montre comment empêcher l'héritage de classe :

``` php
<?php
final class Fruit {
  // code
}

class Strawberry extends Fruit {
  // code
}
?>
```

L'exemple suivant montre comment empêcher le remplacement de méthode :

``` php
<?php
class Fruit {
  final public function intro() {
    // code
  }
}

class Strawberry extends Fruit {
  public function intro() {
    // code
  }
}
?>
```