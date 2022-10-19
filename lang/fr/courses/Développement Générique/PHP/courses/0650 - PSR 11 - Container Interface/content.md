## Objectif du PSR 11

L’objectif du PSR 11 est de créer une interface commune pour les conteneurs d’injection de dépendances et de standardiser la façon dont les frameworks et les librairies l’utilisent. Le conteneur de dépendances est utilisé pour obtenir des objets en paramètre d’entrée d'une fonction.

L’```implementor``` dans ce cours doit être interprété comme quelque chose qui implémente le ```ContainerInterface``` dans une librairie ou framework. Les utilisateurs de conteneur d’injection de dépendances (DIC) sont appelés “user”.

## Identifiant d’entrée

Un identifiant d’entrée est une chaîne d’au moins 1 caractère qui identifie de manière unique un élément dans un conteneur. Un identifiant d’entrée est une chaîne opaque, donc les appelants ne devraient pas supposer que la structure de la chaîne porte une quelconque signification sémantique.

## Lecture d’un conteneur

Le ```Psr\Container\ContainerInterface``` expose 2 méthodes qui sont ```get``` et ```has```.

```get``` prend un identifiant d’entrée en paramètre, qui doit être une chaîne de caractère, ```get``` peut renvoyer n’importe quelle valeur ou lancer une ```NotFoundExeptionInterface``` si l'identifiant connu du conteneur fait 2 appels successifs à ```get``` avec le même identifiant, ce qui devrait retourner la même valeur. Cependant, selon l’```implementor``` conception et/ou la “user” configuration, des valeurs différentes peuvent être retournées, donc “user” ne doit pas compter sur l’obtention de la même valeur sur 2 appels successifs.

```has``` prend un identifiant d’entrée en paramètre, qui doit être une chaîne de caractère, ```has``` retourne “true” si l'identifiant d’entrée est connu de conteneur ou alors ```has``` renvoie “false” s’il ne l’est pas. Si ```has($id)``` renvoie false alors ```get($id)``` lance une ```NotFoundExceptionInterface```.

## Les exceptions

Les exceptions directement levées par le conteneur implémente le ```PSR\Container\ContainerExceptionInterface```. Un appel à la méthode ```get``` avec un identifiant existant doit lancer un ```Psr\Container\NotFoundExceptionInterface```.

## Les packages

Les interfaces et les classes ainsi que les exceptions sont fournies dans le cadre du package ```psr/container```. Les packages qui fournissent une implémentation de conteneur PSR doivent déclarer qu’ils fournissent des fichiers ```psr/container-implementation 1.0.0```.

## Les interfaces

Le ```Psr\Container\ContainerInterface``` :

``` php
<?php
namespace Psr\Container;

/**
 * Décrit l’interface d’un container
 */
interface ContainerInterfaces
{
    /**
     * Recherche une entrée du container par son identifiant et la renvoie
     *
     * @param string $id Identifiant de l’entrée à rechercher
     *
     * @throws NotFoundExceptionInterface Aucune entrée trouvée
     * @throws ContainerExceptionInterface Erreur lors de la récupération de l’entrée
     *
     * @return mixed Entry.
     */
    public function get($id);

    /**
     * Returns true Si le container peut retourner une entrée pour l’identifiant donné
     * Returns false autrement
     *
     * `has($id)` retourne true ne signifie pas que `get($id)` ne lèvera pas d'exception
     * Cela signifie que `get($id)` ne lancera pas une `NotFoundExceptionInterface`.
     *
     * @param string $id Identifiant de l’entrée à rechercher
     *
     * @return bool
     */
    public function has($id);
}
?>
```

Le ```Psr\Container\ContainerExceptionInterface``` :

``` php
<?php
namespace Psr\Container;

/**
 * Interface de base représentant une exception générique dans un container
 */
interface ContainerExceptionInterface
{
}
```

Le ```Psr\Container\NotFoundExceptionInterface``` :

``` php
<?php
namespace Psr\Container;

/**
 * Aucune entrée n’a été trouvé dans le container
 */
interface NotFoundExceptionInterface extends ContainerExceptionInterface
{
}
```