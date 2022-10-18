Le PSR 01, “Basic Coding Standard” (fr: *norme de codage de base*), a pour but de définir des règles génériques de base sur la manière de coder un script ou un programme en PHP. Ces règles concernent des généralités, des normes concernant l’architecture de dossiers et de fichiers, des normes d’encodage, ou encore des normes liées à la programmation orientée objet.

## Généralités

le PSR 01 énonce en premier lieu des généralités qu’il conviendra de respecter en toutes circonstances : 

- Les fichiers PHP doivent **impérativement** et **uniquement** utiliser les balises ```<?php``` et ```<?=```. Aucune autre possibilité ne doit être utilisée.
- Les fichiers PHP ne doivent être encodés qu’en **UTF-8 sans BOM**. Aucun autre encodage n’est autorisé dans le cadre d’une conformité PSR 01.
- Les fichiers doivent autant que possible soit déclarer des symboles (classes, fonctions, constantes…),  soit provoquer des effets secondaires (affichages divers, modifications des paramètres, etc.), mais **pas les deux**. Nous développerons davantage ce point au titre 3.
- Les namespaces et les classes doivent obligatoirement suivre le PSR d’autoloading (PSR 04)
- Les noms de classe doivent obligatoirement être déclarés en “**StudlyCaps**”. C’est-à-dire que tous les mots qui composent le nom doivent être collés, et chacun doit commencer par une majuscule.
- Les constantes de classe doivent obligatoirement être déclarées entièrement en majuscule. Si son nom est composé de plusieurs mots, alors ils devront être séparés par des “**underscore**” (**_**).
- Les noms de méthodes doivent obligatoirement être déclarés en “**camelCase**”. Cette convention d’écriture consiste en l’écriture de tous les mots, sans espace (entièrement attachés), avec les premières lettres de chaque mot en majuscule à l’exception du premier.

## Les effets secondaires

Les fichiers doivent autant que possible soit déclarer des symboles (classes, fonctions, constantes…),  soit provoquer des effets secondaires (affichages divers, modifications des paramètres, etc.), mais **pas les deux**.

Le terme “effet secondaire” fait référence à l’exécution d’une logique qui n’est pas directement liée à la déclaration d’une classe, d’une fonction, d’une constante (etc.). Ainsi, tout effet secondaire ne doit pas - dans la mesure du possible - être présent dans les mêmes fichiers que les déclarations effectuées.

Les “effets secondaires” peuvent par exemple être (liste non exhaustive) : 

- une génération de contenu
- une utilisation explicite de “**require**” ou “**include**”
- une connexion à un service externe
- une modification des fichiers de configuration
- une émission d’erreur ou d’exception
- une modification de variable globale ou statique
- une lecture ou une écriture de fichier
- ...

Voici un exemple d’un fichier contenant des effets secondaires, ainsi qu’une déclaration :

``` php
<?php
// modification d'un paramètre : effet secondaire
ini_set('error_reporting', ALL);

// inclusion d'un fichier : effet secondaire
include "file.php";

// génération d'un affichage : effet secondaire
echo "<html>\n";

// déclaration
function foo()
{
    // contenu de la fonction
}
```

Dans l’exemple ci-dessus, la déclaration ne fait pas partie des “effets secondaires”. Ainsi, sa présence entraîne une non-conformité à la PSR 01. Si cette fonction ```foo()``` était enlevée, alors la conformité PSR 01 serait validée.

Voici à présent un exemple de code ne contenant que des déclarations, et donc sans effets secondaires : 

``` php
<?php

// déclaration d'une fonction
function foo()
{
    // contenu de la fonction
}

// la condition de déclaration d'une fonction n'est pas
// un effet secondaire
if (!function_exists('bar'))
{
    function bar()
    {
        // contenu de la fonction
    }
}
```

## Les namespaces et noms de classes

Les namespaces et les classes doivent impérativement suivre la PSR 04 “autoloading”. Ceci incluant :

- Chaque classe doit être dans un fichier homonyme
- Chaque classe doit être dans un namespace d’au moins 1 niveau
- Les noms de classe doivent être déclarés en “StudlyCaps”

Attention, la déclaration des namespaces dépend de la version PHP utilisée. À partir de la version 5.3 (et suivantes), les namespaces doivent être déclarés de manière formelle : 

``` php
<?php


// formal namespace example PHP >= 5.3
namespace Vendor\Model;

class Foo
{
    // class code here
}
```

Concernant les versions antérieures à PHP 5.3 (à partir de la 5.2), les namespaces n’existants pas, il faut dans la mesure du possible nommer les classes en préfixant leur nom de leur chemin, en séparant chaque niveau par un “underscore” :

``` php
<?php

// class name declaration PHP <= 5.2
class Vendor_Model_Foo
{
    // class code here
}
```

## Les constantes de classe, propriétés et méthodes

### Constantes de classe

Les constantes de classe doivent impérativement être déclarées entièrement en majuscule en séparant chaque mot par des underscores ( _ ).

``` php
<?php

namespace Vendor\Model;

class Foo
{
    const VERSION = "1.0";
    const DATE_APPROVED = "01/01/2020";
}
```

### Propriétés

Contrairement aux idées reçues, la PSR 01 ne définit aucun formalisme particulier concernant le nommage des propriétés au sein d’une classe. Cependant, trois formalismes sont évoqués :

- Le **StudlyCaps**
- Le **camelCase**
- Le **snake_case**

Si la majorité des développeurs s’accordent aujourd’hui pour favoriser le camelCase, la PSR 01 indique uniquement qu’il devrait à minima être instauré un seul formalisme en fonction d’un scope (le plus large étant le mieux). Par exemple, l’utilisation du **camelCase** dans l’ensemble d’un namespace, à défaut dans l’ensemble d’une classe, à défaut dans une méthode.

### Méthodes

La PSR 01 se termine sur les méthodes, en spécifiant que leurs noms doivent impérativement être déclarés en **camelCase**.

