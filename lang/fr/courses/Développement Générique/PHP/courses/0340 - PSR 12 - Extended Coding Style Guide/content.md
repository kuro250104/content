L’objectif du PSR 12 est d’étendre et remplacer le PSR 2, le guide de style de codage exige le respect du PSR 1, la norme de codage de base. Comme le PSR 2, cette spécification permet de réduire les frictions cognitives lors de la numérisation du code de différents auteurs. Le PSR 12 vise à fournir une manière définie que les outils de style de codage peuvent mettre en œuvre, les projets peuvent déclarer leur adhésion et les développeurs peuvent facilement s’identifier entre différents projets. Lorsque plusieurs développeurs collaborent sur plusieurs projets, il est utile de définir un ensemble de directives à utiliser pour ces projets. Ainsi, l'intérêt de ce PSR n’est pas dans les règles de style, mais dans le partage de ces règles.

En résumé, le PSR 12 cherche à clarifier le contenu du PSR 2 dans un contexte plus moderne avec de nouvelles fonctionnalités disponibles.

Exemple :

``` php
<?php

declare(strict_types=1);

namespace Vendor\Package;

use Vendor\Package\{ClassA as A, ClassB, ClassC as C};
use Vendor\Package\SomeNamespace\ClassD as D;

use function Vendor\Package\{functionA, functionB, functionC};

use const Vendor\Package\{ConstantA, ConstantB, ConstantC};

class Foo extends Bar implements FooInterface
{
    public function sampleFunction(int $a, int $b = null): array
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // méthode
    }
}
?>
```

## Norme de codage de base

Le code doit suivre les règles décrites dans le PSR-1. Le terme “StudlyCaps” dans le PSR-1 doit être interprété comme PascalCase où la première lettre de chaque mot est en majuscule. y compris la toute première lettre

## Les fichiers

Tous les fichiers en PHP doivent utiliser uniquement la fin de ligne Unix LF (linefeed). Tous les fichiers PHP doivent se terminer par une ligne non vide, terminée par un seul LF. La balise ```?>``` de fermeture doit être omise des fichiers contenant seulement du PHP.

## Les Lignes

Il ne doit pas y avoir de limite stricte sur la longueur de la ligne. La limite souple sur la longueur de ligne doit être de 120 caractères. Les lignes ne devraient pas dépasser 80 caractères ; les lignes plus longues devraient être divisées en plusieurs lignes suivantes de 80 caractères chacune au maximum. Il ne doit pas y avoir d'espace à la fin des lignes. Des lignes vierges peuvent être ajoutées pour améliorer la lisibilité et pour indiquer les blocs de code associés, sauf là où cela est explicitement interdit. Il ne doit pas y avoir plus d'une instruction par ligne.

## Les Indentations

Le code DOIT utiliser un retrait de 4 espaces pour chaque niveau de retrait et NE DOIT PAS utiliser de tabulations pour le retrait.

## Les mots-clés et types

Tous les mots-clés et types doivent être en minuscules. Tous les nouveaux types et mots-clés ajoutés aux futures versions de PHP doivent être en minuscules.

La forme courte des mots-clés de type doit être utilisée, c'est "bool"-à dire au lieu de boolean, “int” au lieu de “integer”, etc.

## Les déclarations de déclarations, espace de noms et déclarations d’importation

L'en-tête d'un fichier PHP peut être constitué de plusieurs blocs différents. S'il est présent, chacun des blocs ci-dessous doit être séparé par une seule ligne vierge, et ne doit pas contenir de ligne vierge. Chaque bloc doit être dans l'ordre indiqué ci-dessous, bien que les blocs qui ne sont pas pertinents puissent être omis.

- Balise ```<?php``` d'ouverture.
- Docblock au niveau du fichier.
- Une ou plusieurs déclarations.
- La déclaration d'espace de noms du fichier.
- Une ou plusieurs “useinstructions” d'importation basée sur les classes.
- Une ou plusieurs “useinstructions” d'importation basée sur des fonctions.
- Une ou plusieurs “useinstructions” d'importation basée sur des constantes.
- Le reste du code dans le fichier.

Lorsqu'un fichier contient un mélange de HTML et de PHP, l'une des sections ci-dessus peut toujours être utilisée. Si c'est le cas, ils doivent être présents en haut du fichier, même si le reste du code consiste en une balise PHP de fermeture puis en un mélange de HTML et de PHP.

Lorsque la balise d'ouverture ```<?php``` est sur la première ligne du fichier, elle doit être sur sa propre ligne sans aucune autre instruction, à moins qu'il ne s'agisse d'un fichier contenant un balisage en dehors des balises d'ouverture et de fermeture PHP.

Les instructions d'importation ne doivent jamais commencer par une barre oblique inverse, car elles doivent toujours être pleinement qualifiées.

Exemple :

``` php
<?php

/**
 * Ce fichier contient un exemple de coding styles.
 */

declare(strict_types=1);

namespace Vendor\Package;

use Vendor\Package\{ClassA as A, ClassB, ClassC as C};
use Vendor\Package\SomeNamespace\ClassD as D;
use Vendor\Package\AnotherNamespace\ClassE as E;

use function Vendor\Package\{functionA, functionB, functionC};
use function Another\Vendor\functionD;

use const Vendor\Package\{CONSTANT_A, CONSTANT_B, CONSTANT_C};
use const Another\Vendor\CONSTANT_D;

/**
 * FooBar est un exemple de classe
 */
class FooBar
{
    // ... PHP code ...
}
```

Les espaces de noms composés avec une profondeur de plus de deux ne doivent pas être utilisés. Par conséquent, la profondeur de composition maximale autorisée est la suivante :

Exemple :

``` php
<?php

use Vendor\Package\SomeNamespace\{
    SubnamespaceOne\ClassA,
    SubnamespaceOne\ClassB,
    SubnamespaceTwo\ClassY,
    ClassZ,
};
```

Et ce qui suit ne serait pas autorisé :

Exemple :

``` php
<?php

use Vendor\Package\SomeNamespace\{
    SubnamespaceOne\AnotherNamespace\ClassA,
    SubnamespaceOne\ClassB,
    ClassZ,
};
```

Lorsque vous souhaitez déclarer des types stricts dans des fichiers contenant un balisage en dehors des balises d'ouverture et de fermeture PHP, la déclaration doit être sur la première ligne du fichier et inclure une balise PHP d'ouverture, la déclaration des types stricts et la balise de fermeture.

Exemple :

``` php
<?php declare(strict_types=1) ?>
<html>
<body>
    <?php
        // ... PHP code ...
    ?>
</body>
</html>
```

Les déclarations de déclaration ne doivent contenir aucun espace et doivent être exactement ```declare(strict_types=1)``` (avec un point-virgule facultatif de fin).

Les déclarations de bloc sont autorisées et doivent être formatées comme ci-dessous. Notez la position des accolades et l'espacement :

``` php
declare(ticks=1) {
    // code
}
```

## Les classes, propriété et méthodes

Le terme « classe » fait référence à toutes les classes, interfaces et traits.

Aucune accolade fermante ne doit être suivie d'un commentaire ou d'une déclaration sur la même ligne.

Lors de l'instanciation d'une nouvelle classe, les parenthèses doivent toujours être présentes même lorsqu'il n'y a pas d'arguments passés au constructeur.

``` php
new Foo();
```

## Extends et implements

Les mots clés “extends” et “implements” doivent être déclarés sur la même ligne que le nom de la classe. L'accolade ouvrante pour la classe doit aller sur sa propre ligne ; l'accolade fermante de la classe doit aller sur la ligne suivante après le corps. Les accolades ouvrantes doivent être sur leur propre ligne et ne doivent pas être précédées ou suivies d'une ligne vide. Les accolades fermantes doivent être sur leur propre ligne et ne doivent pas être précédées d'une ligne vide.

Exemple :

``` php
<?php

namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

Les listes de “implements” et, dans le cas des interfaces, “extends” peuvent être réparties sur plusieurs lignes, où chaque ligne suivante est indentée une fois. Ce faisant, le premier élément de la liste doit être sur la ligne suivante, et il doit n'y avoir qu'une seule interface par ligne.

``` php
<?php

namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

## Utilisation des traits

Le mot-clé ```use``` utilisé à l'intérieur des classes pour implémenter les traits doit être déclaré sur la ligne suivante après l'accolade ouvrante.

Exemple :

``` php
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;

class ClassName
{
    use FirstTrait;
}
```

Chaque trait individuel importé dans une classe doit être inclus une par ligne et chaque inclusion doit avoir sa propre déclaration d'importation.

``` php
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;
use Vendor\Package\SecondTrait;
use Vendor\Package\ThirdTrait;

class ClassName
{
    use FirstTrait;
    use SecondTrait;
    use ThirdTrait;
}
```

Lorsque la classe n'a rien après l'instruction use, l'accolade fermante de classe doit être sur la ligne suivante après l'instruction use.

``` php
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;

class ClassName
{
    use FirstTrait;
}
```

Sinon, il doit avoir une ligne vide après l'instruction use.

``` php
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;

class ClassName
{
    use FirstTrait;

    private $property;
```

Lorsque vous utilisez les opérateurs “insteadof” et “as” ils doivent être utilisés comme suit en tenant compte de l'indentation, de l'espacement et des nouvelles lignes.

``` php
<?php

class Talker
{
    use A;
    use B {
        A::smallTalk insteadof B;
    }
    use C {
        B::bigTalk insteadof C;
        C::mediumTalk as FooBar;
    }
}
```

## Les propriétés et constantes

La visibilité doit être déclarée sur toutes les propriétés. La visibilité doit être déclarée sur toutes les constantes si la version minimale de PHP de votre projet prend en charge les visibilités constantes (PHP 7.1 ou version ultérieure). Le mot-clé “var” ne doit pas être utilisé pour déclarer une propriété. Il ne doit pas y avoir plus d'une propriété déclarée par instruction. Les noms de propriété ne doivent pas être précédés d'un seul trait de soulignement pour indiquer une visibilité protégée ou privée. C'est-à-dire qu'un préfixe de soulignement n'a explicitement aucune signification. Il doit y avoir un espace entre la déclaration de type et le nom de la propriété. Une déclaration de propriété ressemble à ce qui suit :

``` php
<?php

namespace Vendor\Package;

class ClassName
{
    public $foo = null;
    public static int $bar = 0;
}
```

## Les méthodes et fonctions

La visibilité doit être déclarée sur toutes les méthodes. Les noms de méthode ne doivent pas être précédés d'un seul trait de soulignement pour indiquer une visibilité protégée ou privée. C'est-à-dire qu'un préfixe de soulignement n'a explicitement aucune signification.

Les noms de méthode et de fonction ne doivent pas être déclarés avec un espace après le nom de la méthode. L'accolade ouvrante doit aller sur sa propre ligne et l'accolade fermante doit aller sur la ligne suivante après le corps. Il ne doit pas y avoir d'espace après la parenthèse ouvrante, et il ne doit pas y avoir d'espace avant la parenthèse fermante.

Une déclaration de méthode ressemble à ce qui suit. Notez l'emplacement des parenthèses, des virgules, des espaces et des accolades :

``` php
<?php

namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

Une déclaration de fonction ressemble à ce qui suit. Notez l'emplacement des parenthèses, des virgules, des espaces et des accolades :

``` php
<?php

function fooBarBaz($arg1, &$arg2, $arg3 = [])
{
    // function body
}
```

## Les arguments de méthode et de fonction

Dans la liste des arguments, il ne doit pas y avoir d'espace avant chaque virgule, et il doit y avoir un espace après chaque virgule.

Les arguments de méthode et de fonction avec des valeurs par défaut doivent aller à la fin de la liste d'arguments.

Exemple :

``` php
<?php

namespace Vendor\Package;

class ClassName
{
    public function foo(int $arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

Les listes d'arguments peuvent être divisées sur plusieurs lignes, où chaque ligne suivante est indentée une fois. Ce faisant, le premier élément de la liste doit être sur la ligne suivante, et il doit n'y avoir qu'un seul argument par ligne.

Lorsque la liste d'arguments est divisée sur plusieurs lignes, la parenthèse fermante et l'accolade ouvrante doivent être placées ensemble sur leur propre ligne avec un espace entre elles.

``` php
<?php

namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```

Lorsque vous avez une déclaration de type de retour présente, il doit y avoir un espace après les deux points suivis de la déclaration de type. Les deux points et la déclaration doivent être sur la même ligne que la parenthèse fermante de la liste d'arguments sans espace entre les deux caractères.

``` php
<?php

declare(strict_types=1);

namespace Vendor\Package;

class ReturnTypeVariations
{
    public function functionName(int $arg1, $arg2): string
    {
        return 'foo';
    }

    public function anotherFunction(
        string $foo,
        string $bar,
        int $baz
    ): string {
        return 'foo';
    }
}
```

Dans les déclarations de type nullable, il ne doivent pas y avoir d'espace entre le point d'interrogation et le type.

``` php
<?php

declare(strict_types=1);

namespace Vendor\Package;

class ReturnTypeVariations
{
    public function functionName(?string $arg1, ?int &$arg2): ?string
    {
        return 'foo';
    }
}
```

Lorsque vous utilisez l'opérateur de référence “&” avant un argument, il ne doit pas y avoir d'espace après celui-ci, comme dans l'exemple précédent.
Il ne doit pas y avoir d'espace entre l'opérateur variadique à trois points et le nom de l'argument :

``` php
public function process(string $algorithm, ...$parts)
{
    // code
}
```

Lors de la combinaison de l'opérateur de référence et de l'opérateur variadique à trois points, il ne doit pas  y avoir d'espace entre les deux :

``` php
public function process(string $algorithm, &...$parts)
{
    // code
}
```

## Abstract, final et static

Lorsqu'elles sont présentes, les déclarations ```abstract``` et ```final``` doivent précéder la déclaration de visibilité.

Lorsqu'elle est présente, la déclaration ```static``` doit venir après la déclaration de visibilité.

``` php
<?php

namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // method body
    }
}
```

## Les appels de méthode et de fonction

Lors d'un appel de méthode ou de fonction, il ne doit pas y avoir d'espace entre le nom de la méthode ou de la fonction et la parenthèse ouvrante, il ne doit pas y avoir d'espace après la parenthèse ouvrante, et il ne doit pas y avoir d'espace avant la parenthèse fermante. Dans la liste des arguments, il ne doit pas y avoir d'espace avant chaque virgule, et il doit y avoir un espace après chaque virgule.

Exemple :

``` php
<?php

bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

Les listes d'arguments peuvent être divisées sur plusieurs lignes, où chaque ligne suivante est indentée une fois. Ce faisant, le premier élément de la liste doit être sur la ligne suivante, et il doit n'y avoir qu'un seul argument par ligne. Un seul argument divisé sur plusieurs lignes (comme cela pourrait être le cas avec une fonction ou un tableau anonyme) ne constitue pas une division de la liste d'arguments elle-même.

``` php
<?php

$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);

<?php

somefunction($foo, $bar, [
  // ...
], $baz);

$app->get('/hello/{name}', function ($name) use ($app) {
    return 'Hello ' . $app->escape($name);
});
```

## Les structures de contrôle

Les règles générales de style pour les structures de contrôle sont les suivantes :

- Il doit y avoir un espace après le mot-clé de la structure de contrôle
- Il ne doit pas  y avoir d'espace après la parenthèse ouvrante
- Il ne doit pas y avoir d'espace avant la parenthèse fermante
- Il doit y avoir un espace entre la parenthèse fermante et l'accolade ouvrante
- Le corps de la structure doit être indenté une fois
- Le corps doit être sur la ligne suivante après l'accolade d'ouverture
- L'accolade fermante doit être sur la ligne suivante après le corps

Le corps de chaque structure doit être entouré d'accolades. Cela standardise l'apparence des structures et réduit la probabilité d'introduire des erreurs lorsque de nouvelles lignes sont ajoutées au corps.

## If, elseif, else

Une structure “if” ressemble à ce qui suit. Notez le placement des parenthèses, des espaces et des accolades ; et que “else” et “elseif” sont sur la même ligne que l'accolade de fermeture du corps plus tôt.

Exemple :

``` php
<?php

if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```

Le mot-clé ```elseif``` devrait être utilisé à la place de ```else if``` pour que tous les mots-clés de contrôle ressemblent à des mots simples.

Les expressions entre parenthèses peuvent être réparties sur plusieurs lignes, chaque ligne suivante étant indentée au moins une fois. Ce faisant, la première condition doit être sur la ligne suivante. La parenthèse fermante et l'accolade ouvrante doivent être placées ensemble sur leur propre ligne avec un espace entre elles. Les opérateurs booléens entre les conditions doivent toujours être au début ou à la fin de la ligne, pas un mélange des deux.

``` php
<?php

if (
    $expr1
    && $expr2
) {
    // if body
} elseif (
    $expr3
    && $expr4
) {
    // elseif body
}
```

## Switch, case

Une structure ```switch``` ressemble à ce qui suit. Notez le placement des parenthèses, des espaces et des accolades. La déclaration ```case``` doit être indentée une fois de ```switch```, et le mot - clé (ou d'autres mots-clés de fin) ```break``` doit être indenté au même niveau que le ```case``` corps. Il doit y avoir un commentaire tel que ```// no “break”``` lorsque la chute est intentionnelle.

Exemple :

``` php
<?php

switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```

Les expressions entre parenthèses peuvent être réparties sur plusieurs lignes, chaque ligne suivante étant indentée au moins une fois. Ce faisant, la première condition doit être sur la ligne suivante. La parenthèse fermante et l'accolade ouvrante doivent être placées ensemble sur leur propre ligne avec un espace entre elles. Les opérateurs booléens entre les conditions doivent toujours être au début ou à la fin de la ligne, pas un mélange des deux.

``` php
<?php

switch (
    $expr1
    && $expr2
) {
    // structure body
}
```

## While, do while

Une déclaration ```while``` ressemble à ce qui suit. Notez le placement des parenthèses, des espaces et des accolades.

Exemple :

``` php
<?php

while ($expr) {
    // code
}
```

Les expressions entre parenthèses peuvent être réparties sur plusieurs lignes, chaque ligne suivante étant indentée au moins une fois. Ce faisant, la première condition doit être sur la ligne suivante. La parenthèse fermante et l'accolade ouvrante doivent être placées ensemble sur leur propre ligne avec un espace entre elles. Les opérateurs booléens entre les conditions doivent toujours être au début ou à la fin de la ligne, pas un mélange des deux.

``` php
<?php

while (
    $expr1
    && $expr2
) {
    // code
}
```

De même, une déclaration ```do while``` ressemble à ce qui suit. Notez le placement des parenthèses, des espaces et des accolades.

``` php
<?php

do {
    // code
} while ($expr);
```

Les expressions entre parenthèses peuvent être réparties sur plusieurs lignes, chaque ligne suivante étant indentée au moins une fois. Ce faisant, la première condition doit être sur la ligne suivante. Les opérateurs booléens entre les conditions doivent toujours être au début ou à la fin de la ligne, pas un mélange des deux.

``` php
<?php

do {
    //code
} while (
    $expr1
    && $expr2
);
```

## For

Une déclaration ```for``` ressemble à ce qui suit. Notez le placement des parenthèses, des espaces et des accolades.

Exemple :

``` php
<?php

for ($i = 0; $i < 10; $i++) {
    // code
} 
```

Les expressions entre parenthèses peuvent être réparties sur plusieurs lignes, chaque ligne suivante étant indentée au moins une fois. Ce faisant, la première expression doit être sur la ligne suivante. La parenthèse fermante et l'accolade ouvrante doivent être placées ensemble sur leur propre ligne avec un espace entre elles.

``` php
<?php

for (
    $i = 0;
    $i < 10;
    $i++
) {
    // code
}
```

## Foreach

Une déclaration ```foreach``` ressemble à ce qui suit. Notez le placement des parenthèses, des espaces et des accolades.

Exemple :

``` php
<?php

foreach ($iterable as $key => $value) {
    // code
}
```

## Try, catch, finally

Un bloc ```try-catch-finally``` ressemble à ce qui suit. Notez le placement des parenthèses, des espaces et des accolades.

Exemple :

``` php
<?php

try {
    // try code
} catch (FirstThrowableType $e) {
    // catch code
} catch (OtherThrowableType | AnotherThrowableType $e) {
    // catch code
} finally {
    // finally code
}
```

## Les opérateurs

Les règles de style pour les opérateurs sont regroupées par arité (le nombre d'opérandes qu'elles prennent). Lorsque l'espace est autorisé autour d'un opérateur, plusieurs espaces peuvent être utilisés à des fins de lisibilité. Tous les opérateurs non décrits ici ne sont pas définis.

### Les opérateurs unaires

Les opérateurs d'incrémentation/décrémentation ne doivent pas avoir d'espace entre l'opérateur et l'opérande.

``` php
$i++;
++$j;
```

Les opérateurs de transtypage ne doivent pas avoir d'espace entre les parenthèses :

``` php
$intValue = (int) $input;
```

### Les opérateurs binaires

Tous les opérateurs binaires arithmétiques, de comparaison, d'affectation, au niveau du bit, logiques, de chaîne et de type doivent être précédés et suivis d'au moins un espace :

``` php
if ($a === $b) {
    $foo = $bar ?? $a ?? $b;
} elseif ($a > $b) {
    $foo = $a + $b * $c;
}
```

### Les opérateurs ternaires

L'opérateur conditionnel, également connu simplement sous le nom d'opérateur ternaire, doit être précédé et suivi d'au moins un espace autour des caractères “?” et “:” :

``` php
$variable = $foo ? 'foo' : 'bar';
```

Lorsque l'opérande du milieu de l'opérateur conditionnel est omis, l'opérateur doit suivre les mêmes règles de style que les autres opérateurs de comparaison binaire :

``` php
$variable = $foo ?: 'bar';
```

## Les fermetures

Les fermetures doivent être déclarées avec un espace après le mot - clé ```function```, et un espace avant et après le mot - clé ```use```. L'accolade ouvrante doit aller sur la même ligne et l'accolade fermante doit aller sur la ligne suivante après le corps. Il ne doit pas y avoir d'espace après la parenthèse ouvrante de la liste d'arguments ou de la liste de variables, et il ne doit pas y avoir d'espace avant la parenthèse fermante de la liste d'arguments ou de la liste de variables. Dans la liste des arguments et la liste des variables, il ne doit pas y avoir d'espace avant chaque virgule, et il doit y avoir un espace après chaque virgule.

Les arguments de fermeture avec les valeurs par défaut doivent aller à la fin de la liste des arguments. Si un type de retour est présent, il doit suivre les mêmes règles qu'avec les fonctions et méthodes normales ; si le mot-clé ```use``` est présent, les deux points doivent suivre la liste des parenthèses fermantes sans espace entre les deux caractères.

Une déclaration de clôture ressemble à ce qui suit. Notez l'emplacement des parenthèses, des virgules, des espaces et des accolades :

``` php
<?php

$closureWithArgs = function ($arg1, $arg2) {
    // code
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // code
};

$closureWithArgsVarsAndReturn = function ($arg1, $arg2) use ($var1, $var2): bool {
    // code
};
```

Les listes d'arguments et les listes de variables peuvent être divisées sur plusieurs lignes, où chaque ligne suivante est indentée une fois. Ce faisant, le premier élément de la liste doit être sur la ligne suivante, et il doit n'y avoir qu'un seul argument ou variable par ligne. Lorsque la liste de fin (qu'il s'agisse d'arguments ou de variables) est divisée sur plusieurs lignes, la parenthèse fermante et l'accolade ouvrante doivent être placées ensemble sur leur propre ligne avec un espace entre elles. Voici des exemples de fermetures avec et sans listes d'arguments et de listes de variables réparties sur plusieurs lignes.

``` php
<?php

$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // code
};

$noArgs_longVars = function () use (
    $longVar1,
    $longer Var2,
    $muchLongerVar3
) {
   // code
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // code
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // code
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // code
};
```

Notez que les règles de formatage s'appliquent également lorsque la fermeture est utilisée directement dans un appel de fonction ou de méthode en tant qu'argument.

``` php
<?php

$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // code
    },
    $arg3
);
```

## Les classes anonymes

Les classes anonymes doivent suivre les mêmes directives et principes que les fermetures de la section ci-dessus.

``` php
<?php

$instance = new class {};
```

L'accolade ouvrante peut être sur la même ligne que le mot - clé “class” tant que la liste des interfaces “implements” n'est pas bouclée. Si la liste des interfaces s'enroule, l'accolade doit être placée sur la ligne suivant immédiatement la dernière interface.

Exemple :

``` php
<?php

$instance = new class extends \Foo implements \HandleableInterface {
    // Class code
};

$instance = new class extends \Foo implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // Class code
};
```