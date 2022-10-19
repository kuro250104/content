Les interfaces vous permettent de spécifier les méthodes qu'une classe doit implémenter.

Les interfaces facilitent l'utilisation d'une variété de classes différentes de la même manière. Lorsqu'une ou plusieurs classes utilisent la même interface, on parle de « polymorphisme ».

Les interfaces sont déclarées avec le mot-clé ```interface``` :

syntaxe :

``` php
<?php
interface InterfaceName {
  public function someMethod1();
  public function someMethod2($name, $color);
  public function someMethod3() : string;
}
?>
```

## Interface vs Classes abstraites

L'interface est similaire aux classes abstraites. Les différences entre les interfaces et les classes abstraites sont :

- Les interfaces ne peuvent pas avoir de propriétés, tandis que les classes abstraites peuvent
- Toutes les méthodes d'interface doivent être publiques, tandis que les méthodes de classe abstraites sont publiques ou protégées
- Toutes les méthodes d'une interface sont abstraites, elles ne peuvent donc pas être implémentées dans le code et le mot-clé abstract n'est pas nécessaire
- Les classes peuvent implémenter une interface tout en héritant d'une autre classe en même temps

## Utilisation des interfaces

Pour implémenter une interface, une classe doit utiliser le “implements” mot - clé.
Une classe qui implémente une interface doit implémenter toutes les méthodes de l'interface.

Exemple :

``` php
<?php
interface Animal {
  public function makeSound();
}

class Cat implements Animal {
  public function makeSound() {
    echo "Meow";
  }
}

$animal = new Cat();
$animal->makeSound();
?>
```

Dans cet exemple, le résultat renvoyé est :

``` php
Meow
```

A partir de l'exemple ci-dessus, disons que nous aimerions écrire un logiciel qui gère un groupe d'animaux. Il y a des actions que tous les animaux peuvent faire, mais chaque animal le fait à sa manière.

En utilisant des interfaces, nous pouvons écrire du code qui peut fonctionner pour tous les animaux même si chaque animal se comporte différemment :

``` php
<?php
interface Animal {
  public function makeSound();
}

class Cat implements Animal {
  public function makeSound() {
    echo " Meow ";
  }
}

class Dog implements Animal {
  public function makeSound() {
    echo " Bark ";
  }
}

class Mouse implements Animal {
  public function makeSound() {
    echo " Squeak ";
  }
}

$cat = new Cat();
$dog = new Dog();
$mouse = new Mouse();
$animals = array($cat, $dog, $mouse);

foreach($animals as $animal) {
  $animal->makeSound();
}
?>
```

Dans cet exemple, le résultat renvoyé est :

``` php
Meow Bark Squeak
```

Chat, Chien et Souris sont toutes des classes qui implémentent l'interface Animal, ce qui signifie qu'elles sont toutes capables de faire un son en utilisant la ```makeSound()``` méthode. Pour cette raison, nous pouvons parcourir tous les animaux et leur dire de faire un son même si nous ne savons pas de quel type d'animal il s'agit.

Comme l'interface ne dit pas aux classes comment implémenter la méthode, chaque animal peut émettre un son à sa manière.
