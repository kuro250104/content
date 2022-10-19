Les objets dépendent souvent d'autres objets. Au lieu de créer la dépendance dans le constructeur, la dépendance doit être passée en paramètre dans le constructeur. Cela garantit qu'il n'y a pas de couplage étroit entre les objets et permet de modifier la dépendance lors de l'instanciation de la classe. Cela présente un certain nombre d'avantages, notamment celui de rendre le code plus facile à lire en rendant les dépendances explicites, ainsi que de simplifier les tests puisque les dépendances peuvent être changées et simulées plus facilement.

Dans l'exemple suivant, Component dépend d'une instance de Logger, mais il n'en crée pas. Il exige qu'une instance soit passée comme argument au constructeur.

``` php
interface Logger {
    public function log(string $message);
}

class Component {
    private $logger;

    public function __construct(Logger $logger) {
        $this->logger = $logger;
    }
}
```

Sans injection de dépendances, le code ressemblerait probablement à ceci :

``` php
class Component {
    private $logger;

    public function __construct() {
        $this->logger = new FooLogger();
    }
}
```

L'utilisation de new pour créer de nouveaux objets dans le constructeur indique que l'injection de dépendances n'a pas été utilisée (ou l'a été de manière incomplète), et que le code est étroitement couplé. C'est également un signe que le code est incomplètement testé ou qu'il peut avoir des tests fragiles qui font des hypothèses incorrectes sur l'état du programme.

Dans l'exemple ci-dessus, où nous utilisons plutôt l'injection de dépendances, nous pourrions facilement passer à un autre ```Logger``` si cela s'avérait nécessaire. Par exemple, nous pourrions utiliser une implémentation de ```Logger``` qui enregistre à un endroit différent, ou qui utilise un format d'enregistrement différent, ou qui enregistre dans la base de données plutôt que dans un fichier.

## Injection dans un conteneur

L'injection de dépendances (DI) dans le contexte de l'utilisation d'un conteneur d'injection de dépendances (DIC) peut être considérée comme un sur-ensemble de l'injection de constructeurs. Un DIC analysera généralement les indications de type du constructeur d'une classe et répondra à ses besoins, en injectant effectivement les dépendances nécessaires à l'exécution de l'instance.

L'implémentation exacte va bien au-delà de la portée de ce document, mais dans son essence même, un DIC repose sur l'utilisation de la signature d'une classe...

``` php
namespace Documentation;

class Example
{
    private $meaning;

    public function __construct(Meaning $meaning)
    {
        $this->meaning = $meaning;
    }
}
```

... pour l'instancier automatiquement, en s'appuyant la plupart du temps sur un système de chargement automatique.

``` php
// older PHP versions
$container->make('Documentation\Example');

// since PHP 5.5
$container->make(\Documentation\Example::class);
```

Dans ce cas, ```Documentation\Example``` sait qu'il a besoin d'un ```Meaning```, et un DIC instancierait à son tour un type de ```Meaning```. L'implémentation concrète ne doit pas dépendre de l'instance consommatrice.

Au lieu de cela, nous définissons des règles dans le conteneur, avant la création de l'objet, qui indiquent comment des types spécifiques doivent être instanciés si nécessaire.

Cela présente un certain nombre d'avantages, car un DIC peut

- partager des instances communes
- fournir un factory pour résoudre une signature de type
- Résoudre la signature d'une interface

Si nous définissons des règles sur la façon dont un type spécifique doit être géré, nous pouvons obtenir un contrôle fin sur les types qui sont partagés, instanciés ou créés à partir d'une usine.

## Injection de setter

Les dépendances peuvent également être injectées par des setters.

``` php
interface Logger {
    public function log($message);
}

class Component {
    private $logger;
    private $databaseConnection;

    public function __construct(DatabaseConnection $databaseConnection) {
        $this->databaseConnection = $databaseConnection;
    }

    public function setLogger(Logger $logger) {
        $this->logger = $logger;
    }

    public function core() {
        $this->logSave();    
        return $this->databaseConnection->save($this);
    }

    public function logSave() {
         if ($this->logger) {
            $this->logger->log('saving');
        }
    }
}
```

Ceci est particulièrement intéressant lorsque la fonctionnalité principale de la classe ne dépend pas de la dépendance pour fonctionner.

Ici, la seule dépendance nécessaire est la ```DatabaseConnection```, elle se trouve donc dans le constructeur. La dépendance ```Logger``` est facultative et n'a donc pas besoin de faire partie du constructeur, ce qui rend la classe plus facile à utiliser.

Notez que lorsque vous utilisez l'injection de setter, il est préférable d'étendre la fonctionnalité plutôt que de la remplacer. Lorsque vous définissez une dépendance, rien ne confirme que la dépendance ne changera pas à un moment donné, ce qui peut entraîner des résultats inattendus. Par exemple, un ```FileLogger``` pourrait être défini dans un premier temps, puis un ```MailLogger``` pourrait être défini. Cela brise l'encapsulation et rend les journaux difficiles à trouver, car nous remplaçons la dépendance.

Pour éviter cela, nous devons ajouter une dépendance avec injection de setter, comme suit :

``` php
interface Logger {
    public function log($message);
}

class Component {
    private $loggers = array();
    private $databaseConnection;

    public function __construct(DatabaseConnection $databaseConnection) {
        $this->databaseConnection = $databaseConnection;
    }

    public function addLogger(Logger $logger) {
        $this->loggers[] = $logger;
    }

    public function core() {
        $this->logSave();
        return $this->databaseConnection->save($this);
    }

    public function logSave() {
        foreach ($this->loggers as $logger) {
            $logger->log('saving');
        }
    }
}
```

Ainsi, chaque fois que nous utiliserons la fonctionnalité de base, elle ne sera pas interrompue même si aucune dépendance n'a été ajoutée au logger, et tout logger ajouté sera utilisé même si un autre logger aurait pu être ajouté. Nous étendons la fonctionnalité au lieu de la remplacer.