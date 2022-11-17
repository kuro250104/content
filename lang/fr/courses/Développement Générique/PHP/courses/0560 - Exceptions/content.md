PHP a une gestion des exceptions similaire à ce qu'offrent les autres langages de programmation. Une exception peut être lancée ("throw") et attrapée ("catch") dans PHP. Le code devra être entouré d'un bloc “try” pour faciliter la saisie d'une exception potentielle. Chaque “try” doit avoir au moins un bloc “catch” ou “finally” correspondant.
Si une exception est lancée et que la portée courante de la fonction n'a pas de bloc “catch”, l'exception "remontera" la pile d'appel de la fonction appelante jusqu'à trouver un bloc “catch” correspondant. Tous les blocs “finally” rencontrés seront exécutés. Si la pile d'appels est déroulée jusqu'à la portée globale sans rencontrer de bloc “catch” correspondant, le programme sera terminé avec une erreur fatale sauf si un gestionnaire global d'exception a été défini.

L'objet lancé doit être une instance de la classe Exception ou d'une sous-classe de la classe Exception. Tenter de lancer un objet qui ne correspond pas à cela résulte en une erreur fatale émise par PHP.

À partir de PHP 8.0.0, le mot clé “throw” est une expression et peut être utilisé dans n'importe quel contexte d'expressions. Dans les versions antérieures, c'était une déclaration qui devait être sur sa propre ligne.

## Catch

Un bloc ```catch``` définit comment réagir à une exception qui a été lancée. Un bloc ```catch``` définit un ou plusieurs types d'exceptions ou erreurs qu'il peut gérer, et optionnellement une variable dans laquelle assigner l'exception. (Cette variable était requise dans les versions antérieures à PHP 8.0.0) Le premier bloc ```catch``` qu'une exception ou erreur lancée rencontre et qui correspond au type de l'objet lancé gérera l'objet.

Plusieurs blocs ```catch``` peuvent être utilisés pour attraper différentes classes d'exceptions. L'exécution normale (lorsque aucune exception n'est lancée dans le bloc ```try```) continue après le dernier bloc ```catch``` défini dans la séquence. Les exceptions peuvent être lancées (```throw```) ou relancées dans un bloc ```catch```. Sinon, l'exécution continuera après le bloc ```catch``` qui a été déclenché.

Lorsqu'une exception est lancée, le code suivant le traitement ne sera pas exécuté et PHP tentera de trouver le premier bloc ```catch``` correspondant. Si une exception n'est pas attrapée, une erreur fatale issue de PHP sera envoyée avec un message "Uncaught Exception ..." indiquant que l'exception n'a pu être attrapée à moins qu'un gestionnaire d'exceptions ne soit défini avec la fonction ```set_exception_handler()```.

À partir de PHP 7.1, un bloc ```catch``` peut spécifier plusieurs exceptions à l'aide du caractère pipe (```|```). Ceci est utile lorsque différentes exceptions de hiérarchies de classes différentes sont traitées de la même manière.

À partir de PHP 8.0.0, le nom de variables pour l'exception attrapée est optionnel. Si non spécifié, le bloc catch sera toujours exécuté, mais n'aura pas accès à l'objet lancé.

## Finally

Un bloc ```finally``` peut aussi être spécifié après des blocs ```catch```. Le code à l'intérieur du bloc ```finally``` sera toujours exécuté après les blocs ```try``` et ```catch```, indépendamment du fait qu'une exception a été lancée, avant de continuer l'exécution normale.
Une interaction notable est entre un bloc ```finally``` et une déclaration ```return```. Si une déclaration ```return``` est rencontrée à l'intérieur des blocs ```try``` ou ```catch```, le bloc ```finally``` sera quand même exécuté. De plus, la déclaration ```return``` est évaluée quand elle est rencontrée, mais le résultat sera retourné après que le bloc ```finally``` est exécuté. Additionnellement, si le bloc ```finally``` contient aussi une déclaration ```return``` la valeur du bloc ```finally``` est retournée.

## Global exception handler

Si une exception est autorisée à remonter jusqu'à la portée globale, elle peut être attrapée par un gestionnaire d'exceptions global s'il a été défini. La fonction ```set_exception_handler()``` peut définir une fonction qui sera appelée à la place d'un bloc ```catch``` si aucun autre bloc n'est invoqué. L'effet est essentiellement identique à entourer le programme entier dans un bloc ```try-catch``` avec cette fonction en tant que ```catch```.

## Exemples

Exemple 1 : Lancer une exception 

```php
<?php
function inverse($x) {
    if (!$x) {
        throw new Exception('Division par zéro.');
    }
    return 1/$x;
}

try {
    echo(inverse(5) . "\n");
    echo(inverse(0) . "\n");
} catch (Exception $e) {
    echo('Exception reçue : ',  $e->getMessage(), "\n");
}

// Continue execution
echo("Bonjour tout le monde !\n");
?>
```

L'exemple ci-dessus va afficher :

```php
0.2
Exception reçue : Division par zéro.
Bonjour tout le monde !
```

Exemple 2 : Gestion de l'exception avec un bloc finally

```php
<?php
function inverse($x) {
    if (!$x) {
        throw new Exception('Division par zéro.');
    }
    return 1/$x;
}

try {
    echo(inverse(5) . "\n");
} catch (Exception $e) {
    echo('Exception reçue : ',  $e->getMessage(), "\n");
} finally {
    echo("Première fin.\n");
}

try {
    echo(inverse(0) . "\n");
} catch (Exception $e) {
    echo('Exception reçue : ',  $e->getMessage(), "\n");
} finally {
    echo("Seconde fin.\n");
}

// On continue l'exécution
echo("Bonjour tout le monde !\n");
?>
```

L'exemple ci-dessus va afficher :

```php
0.2
Première fin.
Exception reçue : Division par zéro.
Seconde fin.
Bonjour tout le monde !
```

Exemple 3 : Interaction entre le bloc finally et return

```php
<?php

function test() {
    try {
        throw new Exception('foo');
    } catch (Exception $e) {
        return 'catch';
    } finally {
        return 'finally';
    }
}

echo(test());
?>
```

L'exemple ci-dessus va afficher :

```php
finally
```

Exemple 4 : Héritage d’une exception

```php
<?php

class MyException extends Exception { }

class Test {
    public function testing() {
        try {
            try {
                throw new MyException('foo!');
            } catch (MyException $e) {
                // on la relance
                throw $e;
            }
        } catch (Exception $e) {
            var_dump($e->getMessage());
        }
    }
}

$foo = new Test;
$foo->testing();

?>
```

L'exemple ci-dessus va afficher :

```php
string(4) "foo!"
```

Exemple 5 : Gestions des exceptions de capture multiple

```php
<?php

class MyException extends Exception { }

class MyOtherException extends Exception { }

class Test {
    public function testing() {
        try {
            throw new MyException();
        } catch (MyException | MyOtherException $e) {
            var_dump(get_class($e));
        }
    }
}

$foo = new Test;
$foo->testing();

?>
```

L'exemple ci-dessus va afficher :

```php
string(11) "MyException"
```

Exemple 6 : Omettre la variable attrapée (PHP 8.0.0 ou supérieur)

```php
<?php

class SpecificException extends Exception {}

function test() {
    throw new SpecificException('Oopsie');
}

try {
    test();
} catch (SpecificException) {
    print "A SpecificException was thrown, but we don't care about the details.";
}
?>
```

Exemple 7 : Throw en tant qu’expression (PHP 8.0.0 ou supérieur)

```php
<?php

class SpecificException extends Exception {}

function test() {
    do_something_risky() or throw new Exception('It did not work');
}

try {
    test();
} catch (Exception $e) {
    print $e->getMessage();
}
?>
```