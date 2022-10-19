Les méthodes magiques sont des méthodes spéciales qui écrase l'action par défaut de PHP quand certaines actions sont réalisées sur un objet.

Les méthodes suivantes sont considérées magiques : 

- ```__construct()```
- ```__destruct()```
- ```__call()```
- ```__callStatic()```
- ```__get()```
- ```__set()```
- ```__isset()```
- ```__unset()```
- ```__sleep()```
- ```__wakeup()```
- ```__serialize()```
- ```__unserialize()```
- ```__toString()```
- ```__invoke()```
- ```__set_state()```
- ```__clone()```
- ```__debugInfo()```

## Exemple __construct()

``` php
__construct(mixed ...$values = ""): void
```

PHP permet aux développeurs de déclarer des constructeurs pour les classes. Les classes qui possèdent une méthode constructeur appellent cette méthode à chaque création d'une nouvelle instance de l'objet, ce qui est intéressant pour toutes les initialisations dont l'objet a besoin avant d'être utilisé.

Exemple :

``` php
<?php
class BaseClass {
    function __construct() {
        print "Dans le constructeur de BaseClass\n";
    }
}

class SubClass extends BaseClass {
    function __construct() {
        parent::__construct();
        print "Dans le constructeur de SubClass\n";
    }
}

class OtherSubClass extends BaseClass {
    // Constructeur hérité de BaseClass
}

// Dans le constructeur de BaseClass
$obj = new BaseClass();

// Dans le constructeur de BaseClass
// Dans le constructeur de SubClass
$obj = new SubClass();

// Dans le constructeur de BaseClass
$obj = new OtherSubClass();
?>
```

Exemple : arguments dans le constructeur

``` php
<?php
class Point {
    protected int $x;
    protected int $y;

    public function __construct(int $x, int $y = 0) {
        $this->x = $x;
        $this->y = $y;
    }
}

$p1 = new Point(4, 5);
$p2 = new Point(4);
$p3 = new Point(y: 5, x: 4);
?>
```

## Exemple __destruct()

``` php
__destruct(): void
```

PHP possède un concept de destructeur similaire à celui d'autres langages orientés objet, comme le C++. La méthode destructeur est appelée dès qu'il n'y a plus de référence sur un objet donné, ou dans n'importe quel ordre pendant la séquence d'arrêt.

Exemple :

``` php
<?php

class MyDestructableClass 
{
    function __construct() {
        print "In constructor\n";
    }

    function __destruct() {
        print "Destroying " . __CLASS__ . "\n";
    }
}

$obj = new MyDestructableClass();
```

Tout comme le constructeur, le destructeur parent ne sera pas appelé implicitement par le moteur. Pour exécuter le destructeur parent, vous devez appeler explicitement la fonction ```parent::__destruct``` dans le corps du destructeur. Tout comme les constructeurs, une classe enfant peut hériter du destructeur du parent s'il n'en implémente pas un lui-même.

Le destructeur sera appelé même si l'exécution du script est stoppée en utilisant la fonction ```exit()```. Appeler la fonction ```exit()``` dans un destructeur empêchera l'exécution des routines d'arrêt restantes.

## Exemple __sleep() et __wakeup()

``` php
public __sleep(): array
public __wakeup(): void
```

```serialize()``` vérifie si la classe a une méthode avec le nom magique ```__sleep()```. Si c'est le cas, cette méthode sera exécutée avant toute linéarisation. Elle peut nettoyer l'objet, et elle est supposée retourner un tableau avec les noms de toutes les variables de l'objet qui doivent être linéarisées. Si la méthode ne retourne rien, alors “null” sera linéarisé, et une alerte de type ```E_NOTICE``` sera émise.

Le but avoué de ```__sleep()``` est de valider des données en attente ou d'effectuer des opérations de nettoyage. De plus, cette fonction est utile si un objet très large n'a pas besoin d'être sauvegardé dans sa totalité.

Réciproquement, la fonction ```unserialize()``` vérifie la présence d'une méthode dont le nom est le nom magique ```__wakeup()```. Si elle est présente, cette fonction peut reconstruire toute ressource que l'objet pourrait posséder.

Le but avoué de ```__wakeup()``` est de rétablir toute connexion de base de données qui aurait été perdue durant la linéarisation et d'effectuer des tâches de réinitialisation.

Exemple :

``` php
<?php
class Connection
{
    protected $link;
    private $dsn, $username, $password;
    
    public function __construct($dsn, $username, $password)
    {
        $this->dsn = $dsn;
        $this->username = $username;
        $this->password = $password;
        $this->connect();
    }

    private function connect()
    {
        $this->link = new PDO($this->dsn, $this->username, $this->password);
    }

    public function __sleep()
    {
        return array('dsn', 'username', 'password');
    }

    public function __wakeup()
    {
        $this->connect();
    }
}
?>
```

## Exemple __serialize() et __unserialize()

``` php
public __serialize(): array
public __unserialize(array $data): void
```

```serialize()``` vérifie si la classe a une méthode avec le nom magique ```__serialize()```. Si c'est le cas, cette méthode sera exécutée avant toute linéarisation. Elle doit construire et retourner un tableau associatif de paire clé/valeur qui représente la forme linéarisée de l'objet. Si aucun tableau n'est retournée une TypeError sera lancée.

L'utilisation prévue de ```_serialize()``` est de définir une représentation arbitraire de l'objet pour le linéariser facilement. Les éléments du tableau peuvent correspondre aux propriétés de l'objet mais ceci n'est pas requis.

Inversement, ```unserialize()``` vérifie la présence d'une fonction avec le nom magique ```__unserialize()```. Si présent, cette fonction sera passé le tableau restauré qui a été retournée depuis ```__serialize()```. Il peut alors restaurer les propriétés de l'objet depuis ce tableau comme approprié.

Exemple :

``` php
<?php
class Connection
{
    protected $link;
    private $dsn, $username, $password;

    public function __construct($dsn, $username, $password)
    {
        $this->dsn = $dsn;
        $this->username = $username;
        $this->password = $password;
        $this->connect();
    }

    private function connect()
    {
        $this->link = new PDO($this->dsn, $this->username, $this->password);
    }

    public function __serialize(): array
    {
        return [
          'dsn' => $this->dsn,
          'user' => $this->username,
          'pass' => $this->password,
        ];
    }

    public function __unserialize(array $data): void
    {
        $this->dsn = $data['dsn'];
        $this->username = $data['user'];
        $this->password = $data['pass'];

        $this->connect();
    }
}
?>
```

## Exemple __toString()

``` php
public __toString(): string
```

La méthode ```__toString()``` détermine comment l'objet doit réagir lorsqu'il est traité comme une chaîne de caractères. 

Exemple :

``` php
<?php
class ClasseTest
{
    public $foo;

    public function __construct($foo)
    {
        $this->foo = $foo;
    }

    public function __toString()
    {
        return $this->foo;
    }
}

$class = new ClasseTest('Bonjour');
echo $class;
?>
```

L'exemple ci-dessus va afficher : Bonjour

## Exemple __invoke()

``` php
__invoke( ...$values): mixed
```

La méthode ```__invoke()``` est appelée lorsqu'un script tente d'appeler un objet comme une fonction.

Exemple :

``` php
<?php
class CallableClass
{
    public function __invoke($x)
    {
        var_dump($x);
    }
}
$obj = new CallableClass;
$obj(5);
var_dump(is_callable($obj));
?>
```

L'exemple ci-dessus va afficher : ```int(5) bool(true)```

## Exemple __set_state()

``` php
static __set_state(array $properties): object
```

Cette méthode statique est appelée pour les classes exportées par la fonction ```var_export()```.

Le seul paramètre de cette méthode est un tableau contenant les propriétés exportées sous la forme ```['property' => value, ...]```.

Exemple :

``` php
class A
{
    public $var1;
    public $var2;

    public static function __set_state($an_array)
    {
        $obj = new A;
        $obj->var1 = $an_array['var1'];
        $obj->var2 = $an_array['var2'];
        return $obj;
    }
}

$a = new A;
$a->var1 = 5;
$a->var2 = 'foo';

$b = var_export($a, true);
var_dump($b);
eval('$c = ' . $b . ';');
var_dump($c);
?>
```

L’exemple ci-dessus va afficher :

``` php
string(60) "A::__set_state(array(
   'var1' => 5,
   'var2' => 'foo',
))"
object(A)#2 (2) {
  ["var1"]=>
  int(5)
  ["var2"]=>
  string(3) "foo"
}
```

## Exemple __debugInfo()

``` php
__debugInfo(): array
```

Cette méthode est appelée par ```var_dump()``` lors du traitement d'un objet pour récupérer les propriétés qui doivent être affichées. Si la méthode n'est pas définie dans un objet, alors toutes les propriétés publiques, protégées et privées seront affichées.

exemple :

``` php
<?php
class C {
    private $prop;

    public function __construct($val) {
        $this->prop = $val;
    }

    public function __debugInfo() {
        return [
            'propSquared' => $this->prop ** 2,
        ];
    }
}

var_dump(new C(42));
?>
```

L’exemple ci-dessus va afficher :

``` php
object(C)#1 (1) {
  ["propSquared"]=>
  int(1764)
}
```

## Exemple __call() et __callStatic()

``` php
public __call(string $name, array $arguments): mixed
public static __callStatic(string $name, array $arguments): mixed
```

- ```__call()``` est appelée lorsque l'on invoque des méthodes inaccessibles dans un contexte objet.
- ```__callStatic()``` est lancée lorsque l'on invoque des méthodes inaccessibles dans un contexte statique.

L'argument ```$name``` est le nom de la méthode appelée. L'argument ```$arguments``` est un tableau contenant les paramètres passés à la méthode ```$name```.

Exemple :

``` php
<?php
class MethodTest
{
    public function __call($name, $arguments)
    {
        // Note : la valeur de $name est sensible à la casse.
        echo "Appel de la méthode '$name' "
             . implode(', ', $arguments). "\n";
    }

    public static function __callStatic($name, $arguments)
    {
        // Note : la valeur de $name est sensible à la casse.
        echo "Appel de la méthode statique '$name' "
             . implode(', ', $arguments). "\n";
    }
}

$obj = new MethodTest;
$obj->runTest('dans un contexte objet');

MethodTest::runTest('dans un contexte static');
?>
```

L’exemple ci-dessus va afficher :

``` php
Appel de la méthode 'runTest' dans un contexte objet
Appel de la méthode statique 'runTest' dans un contexte static
```

## Exemple __get(), __set(), __iseet() et __unset()

``` php
public __set(string $name, mixed $value): void
public __get(string $name): mixed
public __isset(string $name): bool
public __unset(string $name): void
```

- ```__set()``` est sollicitée lors de l'écriture de données vers des propriétés inaccessibles (protégées ou privées) ou inexistantes.
- ```__get()``` est appelée pour lire des données depuis des propriétés inaccessibles (protégées ou privées) ou inexistantes.
- ```__isset()``` est sollicitée lorsque ```isset()``` ou ```empty()``` sont appelées sur des propriétés inaccessibles (protégées ou privées) ou inexistantes.
- ```__unset()``` est invoquée lorsque ```unset()``` est appelée sur des propriétés inaccessibles (protégées ou privées) ou inexistante.

L'argument ```$name``` est le nom de la propriété avec laquelle on interagit. L'argument ```$value``` de la méthode ```__set()``` spécifie la valeur à laquelle la propriété $name devrait être définie.

La surcharge de propriétés ne fonctionne que dans les contextes objets. Ces méthodes magiques ne seront pas lancées en contexte statique. Par conséquent, ces méthodes ne devraient pas être déclarées comme statiques. Un avertissement est levé si une des méthodes magiques est déclarée comme statique.

Exemple :

``` php
<?php
class PropertyTest
{
    /**  Variable pour les données surchargées.  */
    private $data = array();

    /**  La surcharge n'est pas utilisée sur les propriétés déclarées.  */
    public $declared = 1;

    /**  La surcharge n'est lancée que lorsque l'on accède à cette propriété depuis l'extérieur de la classe.  */
    private $hidden = 2;

    public function __set($name, $value)
    {
        echo "Définition de '$name' à la valeur '$value'\n";
        $this->data[$name] = $value;
    }

    public function __get($name)
    {
        echo "Récupération de '$name'\n";
        if (array_key_exists($name, $this->data)) {
            return $this->data[$name];
        }

        $trace = debug_backtrace();
        trigger_error(
            'Propriété non-définie via __get() : ' . $name .
            ' dans ' . $trace[0]['file'] .
            ' à la ligne ' . $trace[0]['line'],
            E_USER_NOTICE);
        return null;
    }

    public function __isset($name)
    {
        echo "Est-ce que '$name' est défini ?\n";
        return isset($this->data[$name]);
    }

    public function __unset($name)
    {
        echo "Effacement de '$name'\n";
        unset($this->data[$name]);
    }

    /**  Ce n'est pas une méthode magique, nécessaire ici que pour l'exemple.  */
    public function getHidden()
    {
        return $this->hidden;
    }
}


echo "<pre>\n";

$obj = new PropertyTest;

$obj->a = 1;
echo $obj->a . "\n\n";

var_dump(isset($obj->a));
unset($obj->a);
var_dump(isset($obj->a));
echo "\n";

echo $obj->declared . "\n\n";

echo "Manipulons maintenant la propriété privée nommée 'hidden' :\n";
echo "'hidden' est visible depuis la classe, donc __get() n'est pas utilisée...\n";
echo $obj->getHidden() . "\n";
echo "'hidden' n'est pas visible en dehors de la classe, donc __get() est utilisée...\n";
echo $obj->hidden . "\n";
?>
```

L’exemple ci-dessus va afficher :

``` php
Définition de 'a' à '1'
Récupération de 'a'
1

Est-ce que 'a' est défini ?
bool(true)
Effacement de 'a'
Est-ce que 'a' est défini ?
bool(false)

1

Manipulons maintenant la propriété privée nommée 'hidden' :
'hidden' est visible depuis la classe, donc __get() n'est pas utilisée...
2
'hidden' n'est pas visible en dehors de la classe, donc __get() est utilisée...
Récupération de 'hidden'


Notice: Propriété non définie via __get() : hidden dans <file> à la ligne 64 dans <file> à la ligne 28
```

## Exemple __clone()

Le fait de créer une copie d'un objet possédant exactement les mêmes propriétés n'est pas toujours le comportement que l'on souhaite. Un bon exemple pour illustrer le besoin d'un constructeur de copie : si vous avez un objet qui représente une fenêtre GTK et que l'objet contient la ressource représentant cette fenêtre GTK, lorsque vous créez une copie vous pouvez vouloir créer une nouvelle fenêtre avec les mêmes propriétés, mais que le nouvel objet contient une ressource représentant la nouvelle fenêtre.

Une copie d'objet est créée en utilisant le mot-clé ```clone``` (qui fait appel à la méthode ```__clone()``` de l'objet, si elle a été définie).

exemple :

``` php
<?php

$copie_d_objet = clone $objet;

?>
```

Lorsqu'un objet est cloné, PHP effectue une copie superficielle de toutes les propriétés de l'objet. Toutes les propriétés qui sont des références à d'autres variables demeureront des références.

``` php
__clone(): void
```

Une fois le clonage effectué, si une méthode ```__clone()``` est définie, la méthode ```__clone()``` du nouvel objet sera appelée, pour permettre à chaque propriété qui doit l'être d'être modifiée.

exemple :

``` php
<?php
class SubObject 
{
  static $instances = 0;
  public $instance;

  public function __construct() {
    $this->instance = ++self::$instances;
  }

  public function __clone() {
    $this->instance = ++self::$instances;
  }
}

class MyCloneable 
{
  public $objet1;
  public $objet2;

  function __clone() 
  {    
    // Force la copie de this->object, sinon
    // il pointera vers le même objet.
    $this->object1 = clone $this->object1;
  }
}

$obj = new MyCloneable();

$obj->object1 = new SubObject();
$obj->object2 = new SubObject();

$obj2 = clone $obj;


print("Objet original :\n");
print_r($obj);

print("Objet cloné :\n");
print_r($obj2);

?>
```

L’exemple ci dessus va afficher :

``` php
Object original :
MyCloneable Object
(
    [object1] => SubObject Object
        (
            [instance] => 1
        )

    [object2] => SubObject Object
        (
            [instance] => 2
        )

)
Object cloné :
MyCloneable Object
(
    [object1] => SubObject Object
        (
            [instance] => 3
        )

    [object2] => SubObject Object
        (
            [instance] => 2
        )

)
```