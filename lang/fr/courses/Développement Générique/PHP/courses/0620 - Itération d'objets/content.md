Depuis PHP 5, il est possible d'itérer dans la liste de tous les éléments visibles d'un objet. L'itération peut être effectuée en utilisant la boucle foreach ainsi que l'interface iterator. Il existe également une interface IteratorAggregate en PHP, qui peut être utilisée dans ce but.

## Utilisation de la boucle foreach

### Exemple

``` php
<?php
class myclass{
   private $var;
   protected $var1;
   public $x, $y, $z;
   public function __construct(){
      $this->var="private variable";
      $this->var1=TRUE;
      $this->x=100;
      $this->y=200;
      $this->z=300;
   }
   public function iterate(){
      foreach ($this as $key => $value) {
         print "$key => $value\n";
      }
   }
}
$obj = new myclass();
foreach($obj as $key => $value) {
   print "$key => $value\n";
}
echo "\n";
$obj->iterate();
?>
```

### Réponse

La réponse est la suivante :

``` php
x => 100
y => 200
z => 300

var => private variable
var1 => 1
x => 100
y => 200
z => 300
```

## Utilisation de l'interface Iterator

Cette interface définit les méthodes abstraites suivantes qui seront implémentées dans l'exemple suivant :

``` php
abstract public current ( void ) : mixed
abstract public key ( void ) : scalar
abstract public next ( void ) : void
abstract public rewind ( void ) : void
abstract public valid ( void ) : bool
```

- ```Iterator::current``` : Retourne l'élément courant
- ```Iterator::key``` : Retourne la clé de l'élément courant
- ```Iterator::next``` : Passer à l'élément suivant
- ```Iterator::rewind``` : Rembobine l’itérateur jusqu'au premier élément
- ```Iterator::valid``` : Vérifie si la position actuelle est valide

L'exemple suivant démontre l'itération d'objets en implémentant l'interface Iterator.

### Exemple

``` php
<?php
class myclass implements Iterator{
   private $arr = array('a','b','c');
   public function rewind(){
      echo "rewinding\n";
      reset($this->arr);
   }
   public function current(){
      $var = current($this->arr);
      echo "current: $var\n";
      return $var;
   }
   public function key() {
      $var = key($this->arr);
      echo "key: $var\n";
      return $var;
   }
   public function next() {
      $var = next($this->arr);
      echo "next: $var\n";
      return $var;
   }
   public function valid(){
      $key = key($this->arr);
      $var = ($key !== NULL && $key !== FALSE);
      echo "valid: $var\n";
      return $var;
   }
}
$obj = new myclass();
foreach ($obj as $k => $v) {
   print "$k: $v\n";
}
?>
```

### Réponse

Le code ci-dessus produit le résultat suivant :

``` php
rewinding
valid: 1
current: a
key: 0
0: a
next: b
valid: 1
current: b
key: 1
1: b
next: c
valid: 1
current: c
key: 2
2: c
next:
valid:
```