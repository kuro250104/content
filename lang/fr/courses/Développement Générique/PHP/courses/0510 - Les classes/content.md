Une classe est un modèle pour les objets et un objet est une instance de classe.

## Cas de POO

Supposons que nous ayons une classe nommée Fruit. Un fruit peut avoir des propriétés telles que le nom, la couleur, le poids, etc. Nous pouvons définir des variables telles que ```$name```, ```$color``` et ```$weight``` pour contenir les valeurs de ces propriétés.

Lorsque les objets individuels (pomme, banane, etc.) sont créés, ils héritent de toutes les propriétés et comportements de la classe, mais chaque objet aura des valeurs différentes pour les propriétés.

## Définir une classe

Une classe est définie en utilisant le mot-clé ```class```, suivi du nom de la classe et d'une paire d'accolades (```{}```). Toutes ses propriétés et méthodes vont à l'intérieur des accolades.

syntaxe :

```php
<?php
class Fruit {
  // code 
}
?>
```

Ci-dessous, nous déclarons une classe nommée "Fruit" composée de deux propriétés (```$name``` et ```$color```) et de deux méthodes ```set_name()``` et ```get_name()``` pour définir et obtenir la propriété ```$name``` :

```php
<?php
class Fruit {
  // Propriétés
  public $name;
  public $color;

  // Méthodes
  function set_name($name) {
    $this->name = $name;
  }
  function get_name() {
    return $this->name;
  }
}
?>
```

## Définir des objets

Nous pouvons créer plusieurs objets à partir d'une classe. Chaque objet possède toutes les propriétés et méthodes définies dans la classe, mais elles auront des valeurs de propriété différentes.

Les objets d'une classe sont créés à l'aide du mot-clé ```new```.

Dans l'exemple ci-dessous, ```$apple``` et ```$banana``` sont des instances de la classe ```Fruit``` :

```php
<?php
class Fruit {
  // Properties
  public $name;
  public $color;

  // Methods
  function set_name($name) {
    $this->name = $name;
  }
  function get_name() {
    return $this->name;
  }
}

$apple = new Fruit();
$banana = new Fruit();
$apple->set_name('Apple');
$banana->set_name('Banana');

echo($apple->get_name());
echo("<br>");
echo($banana->get_name());
?>
```

Dans cet exemple, le résultat renvoyé est :

```php
Apple
Banana
```

## Le mot clé this

Le mot-clé ```$this``` fait référence à l'objet courant et n'est disponible qu'à l'intérieur des méthodes.

exemple :

```php
<?php
class Fruit {
  public $name;
}
$apple = new Fruit();
?>
```

Alors, où pouvons-nous changer la valeur de la propriété” $name” ? Il y a deux manières :

1 - Dans la classe (en ajoutant une méthode ```set_name()``` et en utilisant ```$this```) :

```php
<?php
class Fruit {
  public $name;
  function set_name($name) {
	$this->name = $name;
  }
}
$apple = new Fruit();
$apple->set_name("Apple");

echo($apple->name);
?>
```

Dans cet exemple, le résultat renvoyé est :

```php
Apple
```

2 - En dehors de la classe (en modifiant directement la valeur de la propriété) :

```php
<?php
class Fruit {
  public $name;
}
$apple = new Fruit();
$apple->name = "Apple";

echo($apple->name);
?>
```

Dans cet exemple, le résultat renvoyé est :

```
Apple
```

## Instance of

Vous pouvez utiliser le mot-clé ```instanceof``` pour vérifier si un objet appartient à une classe spécifique :

```php
<?php
$apple = new Fruit();
var_dump($apple instanceof Fruit);
?>
```

Dans cet exemple, le résultat renvoyé est :

```php
bool(true);
```