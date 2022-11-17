Avant de comprendre le concept d'**encapsulation**, il est important de comprendre le concept de **spécificateur d'accès**. Les spécificateurs d'accès définissent le type d'accès des membres (propriétés et méthodes) de la classe et il existe trois types de spécificateurs d'accès en PHP.

- ```public``` : les membres de la classe sont accessibles de partout. C'est aussi le spécificateur d'accès par défaut.
- ```protected``` : les membres de la classe sont accessibles à l'intérieur de la classe et par les classes dérivées.
- ```private``` : les membres de la classe ne sont accessibles QUE dans la classe.

## Exemple

Dans l'exemple ci-dessous, une classe appelée *person* est créée et possède une propriété privée appelée name. Lorsqu'on accède à cette propriété dans le programme, une exception est levée car il s'agit d'une propriété privée à laquelle on ne peut accéder en dehors de la classe dans laquelle elle est définie.

```php
<?php
class person {
  private $name = "John";
};

$p1 = new person();
echo($p1->name);
?>
```

La réponse du code ci-dessus sera :

```php
PHP Fatal error:  Uncaught Error: Cannot access private property person::$name
```

## Encapsulation

L'**encapsulation** est un processus consistant à lier les propriétés et les méthodes dans une seule unité appelée classe. Elle a pour but d'empêcher l'accès direct aux propriétés et n'est disponible que par le biais des méthodes de la classe. L'encapsulation des données a conduit à l'important concept de dissimulation des données dans la programmation orientée objet, également connu sous le nom d'**abstraction des données**. L'abstraction de données est un mécanisme qui permet de n'exposer que les interfaces et de cacher les détails de la mise en œuvre à l'utilisateur.

Étapes de l'encapsulation des données :

- Déclarez chaque propriété privée.
- Créez une méthode publique set pour chaque propriété afin de définir les valeurs des propriétés.
- Créez une méthode publique get pour chaque propriété afin de récupérer les valeurs des propriétés.

Dans l'exemple ci-dessous, des méthodes publiques set et get sont créées pour accéder aux propriétés privées nom et âge de la classe *person*.

```php
<?php
class person {
  private $Name;
  private $Age;
  // méthode pour définir la valeur du nom
  public function setName($name) {
    $this->Name = $name;
  }
  // méthode pour récupérer la valeur du nom
  public function getName() {
    return $this->Name;
  }
  // méthode pour définir la valeur de âge
  public function setAge($age) {
    $this->Age = $age;
  }
  // méthode pour récupérer la valeur de âge
  public function getAge() {
    return $this->Age;
  }
};

$p1 = new person();

// définir le nom et l'âge
$p1->setName("Patrick");
$p1->setAge(64);
// obtenir le nom et l'âge
echo($p1->getName()." a ".$p1->getAge()." ans.");
?>
```

La réponse du code ci-dessus sera :

```php
Patrick a 64 ans.
```