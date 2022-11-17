La mise en cache est un moyen courant d'améliorer les performances de tout projet, ce qui fait des bibliothèques d'implémentation l'une des caractéristiques les plus courantes de nombreux frameworks et bibliothèques. Cela a conduit à une situation où de nombreuses bibliothèques utilisent leurs propres bibliothèques d'implémentation, avec différents niveaux de fonctionnalité. Ces différences obligent les développeurs à apprendre à utiliser plusieurs systèmes qui peuvent ou non fournir les fonctionnalités dont ils ont besoin. En outre, les développeurs de bibliothèques d'implémentation sont eux-mêmes confrontés à un choix entre la prise en charge d'un nombre limité de frameworks ou la création d'un grand nombre de classes d'adaptateurs.

Une interface commune pour les systèmes de mise en cache résoudra ces problèmes. Les développeurs de bibliothèques et de frameworks peuvent compter sur le fait que les systèmes de mise en cache fonctionnent comme ils l'espèrent, tandis que les développeurs de systèmes de mise en cache n'auront à mettre en œuvre qu'un seul ensemble d'interfaces plutôt qu'un assortiment complet d'adaptateurs.

## Objectif

L'objectif de ce PSR est de permettre aux développeurs de créer des bibliothèques compatibles avec le cache qui peuvent être intégrées dans des cadres et des systèmes existants sans qu'il soit nécessaire de procéder à un développement personnalisé.

## Définitions

- **Bibliothèque d'appel** - La bibliothèque ou le code qui a réellement besoin des services de cache. Cette bibliothèque utilisera les services de cache qui implémentent les interfaces de cette norme, mais n'aura autrement aucune connaissance de l'implémentation de ces services de cache.
- **Bibliothèque d'implémentation** - Cette bibliothèque est responsable de l'implémentation de cette norme afin de fournir des services de mise en cache à toute bibliothèque d'appel. La bibliothèque d'implémentation doit fournir des classes qui implémentent les interfaces Cache\CacheItemPoolInterface et Cache\CacheItemInterface. Les bibliothèques d'implémentation doivent au minimum prendre en charge la fonctionnalité TTL décrite ci-dessous avec une précision de granularité de l'ordre de la seconde.
- **TTL (The Time To Live)** - Le temps de vie d'un objet est le temps qui s'écoule entre le moment où cet objet est stocké et celui où il est considéré comme périmé. Le TTL est normalement défini par un entier représentant le temps en secondes, ou un objet DateInterval.
- **Expiration** - Le moment réel où un article est prêt à être périmé. Elle est généralement calculée en ajoutant le TTL à l'heure à laquelle un objet est stocké, mais peut également être explicitement définie avec l'objet DateTime. Un objet avec un TTL de 300 secondes stocké à 1:30:00 aura une expiration à 1:35:00. Les bibliothèques d'application peuvent faire expirer un article avant l'heure d'expiration demandée, mais doivent traiter un article comme expiré une fois que l'heure d'expiration est atteinte. Si une bibliothèque appelante demande qu'un document soit enregistré mais ne spécifie pas d'heure d'expiration, ou spécifie une heure d'expiration nulle ou TTL, une bibliothèque d'implémentation peut utiliser une durée par défaut configurée. Si aucune durée par défaut n'a été définie, la bibliothèque d'implémentation doit l'interpréter comme une demande de mise en cache de l'élément pour toujours, ou aussi longtemps que l'implémentation sous-jacente le permet.
- **Clé** - Une chaîne d'au moins un caractère qui identifie de manière unique un élément mis en cache. Les bibliothèques d'implémentation doivent prendre en charge les clés composées des caractères A-Z, a-z, 0-9, _, et . dans n'importe quel ordre en codage UTF-8 et d'une longueur maximale de 64 caractères. Les bibliothèques d'implémentation peuvent prendre en charge des caractères et des codages supplémentaires ou des longueurs plus importantes, mais doivent au moins prendre en charge ce minimum. Les bibliothèques sont responsables de leur propre échappement des chaînes de caractères clés selon le cas, mais doivent être en mesure de renvoyer la chaîne de caractères originale non modifiée. Les caractères suivants sont réservés aux extensions futures et ne doivent pas être pris en charge par les bibliothèques d'implémentation : {}()/\@:
- **Succès** - Un succès de cache se produit lorsqu'une bibliothèque appelante demande un article par clé et qu'une valeur correspondante est trouvée pour cette clé, et que cette valeur n'a pas expiré, et que la valeur n'est pas invalide pour une autre raison. Les bibliothèques appelantes doivent s'assurer de vérifier isHit() sur tous les appels à get().
- **Échec** - Un échec de cache est l'opposé d'un succès de cache. Un échec de cache se produit lorsqu'une bibliothèque appelante demande un élément par clé et que cette valeur n'a pas été trouvée pour cette clé, ou que la valeur a été trouvée, mais a expiré, ou que la valeur est invalide pour une autre raison. Une valeur expirée doit toujours être considérée comme un échec de cache.
- **Différé** - Une sauvegarde différée du cache indique qu'un élément du cache ne peut pas être persisté immédiatement par le groupe. Un objet du groupe peut retarder la persistance d'un élément de cache différé afin de tirer parti des opérations de groupage prises en charge par certains moteurs de stockage. Un groupe doit s'assurer que tout élément de cache différé est finalement persisté et que les données ne sont pas perdues, et peut les persister avant qu'une bibliothèque appelante ne demande qu'ils soient maintenus. Lorsqu'une bibliothèque appelante invoque la méthode commit(), tous les éléments différés en suspens doivent être maintenus. Une bibliothèque d'implémentation peut utiliser n'importe quelle logique appropriée pour déterminer quand persister les éléments différés, comme un destructeur d'objets, la persistance de tous les éléments lors de la sauvegarde, une vérification du délai d'attente ou du nombre maximum d'éléments ou toute autre logique appropriée. Les demandes pour un élément de cache qui a été reporté doivent obligatoirement renvoyer l'élément reporté, mais pas encore conservé.

## Données

Les bibliothèques implémentées doivent prendre en charge tous les types de données PHP sérialisables, y compris :

- **Chaînes** - Chaînes de caractères de taille arbitraire dans tout encodage compatible avec PHP.
- **Entiers** - Tous les entiers de toute taille pris en charge par PHP, jusqu'à 64 bits.
- **Nombre décimal** - Toutes les valeurs en nombre décimal.
- **Booléen** - Vrai et faux.
- **Null** - La valeur nulle.
- **Tableaux** - Tableaux indexés, associatifs et multidimensionnels de longueur arbitraire.
- **Objet** - Tout objet qui supporte la sérialisation et la désérialisation sans perte de manière que ```$o == unserialize(serialize($o))```. Les objets peuvent utiliser l'interface sérialisable de PHP, les méthodes magiques ```__sleep()``` ou ```__wakeup()```, ou des fonctionnalités similaires du langage si nécessaire.

Toutes les données transmises à la bibliothèque d'implémentation doivent être renvoyées exactement comme elles ont été transmises. Cela inclut le type de variable. C'est-à-dire que c'est une erreur de renvoyer (string) 5 si (int) 5 était la valeur sauvegardée. Les bibliothèques d'implémentation peuvent utiliser les fonctions ```serialize()``` et ```unserialize()``` de PHP en interne mais ne sont pas obligées de le faire. La compatibilité avec ces fonctions est simplement utilisée comme référence pour les valeurs d'objets acceptables.

S'il n'est pas possible de renvoyer la valeur exacte enregistrée pour une raison quelconque, les bibliothèques d'implémentation doivent répondre par un échec de cache plutôt que par des données corrompues.

## Concepts clés

### Groupe

Le Groupe représente une collection d'objets dans un système de mise en cache. Le groupe est un dépôt logique de tous les éléments qu'il contient. Tous les objets pouvant être mis en cache sont récupérés dans le groupe en tant qu'objet Item et toute interaction avec l'univers entier des objets mis en cache se fait par le biais du groupe.

### Éléments

Un élément représente une seule paire clé/valeur au sein d'un groupe. La clé est le principal identifiant unique d'un élément et doit être immuable. La valeur peut être modifiée à tout moment.

## Traitement des erreurs

Bien que la mise en cache soit souvent un élément important des performances des applications, elle ne devrait jamais être un élément critique de la fonctionnalité des applications. Ainsi, une erreur dans un système de cache ne doit pas entraîner l'échec d'une application. Pour cette raison, les bibliothèques de mise en œuvre ne doivent pas lancer d'exceptions autres que celles définies par l'interface, et doivent piéger toute erreur ou exception déclenchée par un magasin de données sous-jacent et ne pas leur permettre de faire des bulles.

Une bibliothèque d'implémentation devrait enregistrer ces erreurs ou les signaler à un administrateur, le cas échéant.

Si une bibliothèque appelante demande qu'un ou plusieurs éléments soient supprimés, ou qu'un groupe soit effacé, cela ne doit pas être considéré comme une condition d'erreur si la clé spécifiée n'existe pas. La postcondition est la même (la clé n'existe pas ou le groupe est vide), il n'y a donc pas de condition d'erreur.

## Interfaces

### CacheItemInterface

CacheItemInterface définit un élément à l'intérieur d'un système de cache. Chaque objet Item doit être associé à une clé spécifique, qui peut être définie en fonction du système d'implémentation et est généralement transmise par l'objet ```Cache\CacheItemPoolInterface```.

L'objet ```Cache\CacheItemInterface``` encapsule le stockage et la récupération des éléments du cache. Chaque ```Cache\CacheItemInterface``` est généré par un objet ```Cache\CacheItemPoolInterface```, qui est responsable de toute configuration requise ainsi que de l'association de l'objet à une clé unique. Les objets ```Cache\CacheItemInterface``` doivent être capables de stocker et de récupérer tout type de valeur PHP définie dans la section Données du présent document.

Les bibliothèques appelantes ne doivent pas instancier les objets Item eux-mêmes. Ils ne peuvent être demandés à un objet Pool que par la méthode ```getItem()```. Les bibliothèques appelantes ne doivent pas supposer qu'un élément créé par une bibliothèque d'implémentation est compatible avec un groupe d'une autre bibliothèque d'implémentation.

```php
<?php

namespace Psr\Cache;

/**
 * CacheItemInterface définit une interface permettant d'interagir avec des objets à l'intérieur d'un cache.
 */
interface CacheItemInterface
{
    /**
     * Renvoie la clé de l'élément de cache actuel.
     *
     * La clé est chargée par la bibliothèque d'implémentation, mais doit être disponible pour les appelants de niveau supérieur en cas de besoin.
     *
     * @return string
     *   La chaîne de la clé pour cet élément de la cache.
     */
    public function getKey();

    /**
     * Récupère la valeur de l'objet dans le cache associé à la clé de cet objet.
     *
     * La valeur retournée doit être identique à la valeur stockée à l'origine par set().
     *
     * Si isHit() renvoie false, cette méthode doit obligatoirement renvoyer null. Notez que null est une valeur légitime mise en cache, donc la méthode isHit() devrait être utilisée pour différencier la valeur "null a été trouvée" et "aucune valeur n'a été trouvée".
     *
     * @return mixed
     *   La valeur correspondant à la clé de cet élément de cache ou nulle si elle n'est pas trouvée.
     */
    public function get();

    /**
     * Confirme si la recherche d'éléments dans la mémoire cache a abouti à un résultat dans la mémoire cache.
     *
     * Note : Cette méthode ne doit pas avoir de condition préalable entre l'appel de isHit() et l'appel de get().
     *
     * @return bool
     *   Vrai si la demande a abouti à un résultat de cache. Faux dans le cas contraire.
     */
    public function isHit();

    /**
     * Définit la valeur représentée par cet élément de cache.
     *
     * L'argument $value peut être n'importe quel élément qui peut être sérialisé par PHP, bien que la méthode de sérialisation soit laissée à la bibliothèque d'implémentation.
     *
     * @param mixed $value
     *   La valeur sérialisable à stocker.
     *
     * @return static
     *   L'objet invoqué.
     */
    public function set($value);

    /**
     * Définit le délai d'expiration de cet élément.
     *
     * @param \DateTimeInterface|null $expiration
     *   Le moment après lequel le point doit être considéré comme expiré. Si la valeur null est passée explicitement, une valeur par défaut peut être utilisée. Si aucune valeur n'est définie, la valeur doit être stockée de manière permanente ou aussi longtemps que l'implémentation le permet.
     *
     * @return static
     *   L'objet appelé.
     */
    public function expiresAt($expiration);

    /**
     * Définit le délai d'expiration de cet élément.
     *
     * @param int|\DateInterval|null $time
     *   La période de temps à partir du présent après laquelle le point doit être considéré comme expiré. Un paramètre entier est compris comme étant le temps en secondes jusqu'à l'expiration. Si la valeur null est passée explicitement, une valeur par défaut peut être utilisée. Si aucune valeur n'est définie, la valeur doit être stockée de manière permanente ou aussi longtemps que l'implémentation le permet.
     *
     * @return static
     *   L'objet appelé.
     */
    public function expiresAfter($time);

}
```

### CacheItemPoolInterface

L'objectif principal de ```Cache\CacheItemPoolInterface``` est d'accepter une clé de la bibliothèque appelante et de renvoyer l'objet ```Cache\CacheItemInterface``` associé. C'est également le principal point d'interaction avec l'ensemble de la collection de caches. Toute la configuration et l'initialisation du groupe est laissée à une bibliothèque d'implémentation.

```php
<?php

namespace Psr\Cache;

/**
 * CacheItemPoolInterface génère des objets CacheItemInterface.
 */
interface CacheItemPoolInterface
{
    /**
     * Retourne un élément de cache représentant la clé spécifiée.
     *
     * Cette méthode doit toujours renvoyer un objet CacheItemInterface, même en cas d'absence de cache. Elle ne doit pas renvoyer un objet null.
     *
     * @param string $key
     *   La clé permettant de retourner l'élément de cache correspondant.
     *
     * @throws InvalidArgumentException
     *   Si la chaîne de caractères $key n'est pas une valeur légale, une \Psr\Cache\InvalidArgumentException doit être envoyée.
     *
     * @return CacheItemInterface
     *   L'élément de cache correspondant.
     */
    public function getItem($key);

    /**
     * Renvoie un ensemble d'éléments de la mémoire cache qui peut être parcouru.
     *
     * @param string[] $keys
     *   Un tableau indexé de clés des éléments à retrouver.
     *
     * @throws InvalidArgumentException
     *   Si l'une des clés en $keys n'a pas de valeur légale, une \Psr\Cache\InvalidArgumentException doit être envoyée.
     *
     * @return array|\Traversable
     *   Une collection d'élément de cache traversable dont les clés de cache de chaque élément sont saisies. Un élément du cache sera retourné pour chaque clé, même si cette clé n'est pas trouvée. Toutefois, si aucune clé n'est spécifiée, un élément de cache vide doit être renvoyé à la place.
     */
    public function getItems(array $keys = array());

    /**
     * Confirme si le cache contient l'élément de cache spécifié.
     *
     * Note : Cette méthode peut éviter de récupérer la valeur mise en cache pour des raisons de performance.
     * Cela pourrait entraîner une situation de concurrence avec CacheItemInterface::get(). Pour éviter une telle situation, utilisez plutôt CacheItemInterface::isHit().
     *
     * @param string $key
     *   La clé qui permet de vérifier l'existence.
     *
     * @throws InvalidArgumentException
     *   Si la chaîne de caractères $key n'est pas une valeur légale, une \Psr\Cache\InvalidArgumentException doit être envoyée.
     *
     * @return bool
     *   Vrai si l'objet existe dans le cache, faux dans le cas contraire.
     */
    public function hasItem($key);

    /**
     * Supprime tous les éléments du groupe.
     *
     * @return bool
     *   C'est vrai si le groupe a été nettoyé avec succès. Faux s'il y a eu une erreur.
     */
    public function clear();

    /**
     * Retire l'élément du groupe.
     *
     * @param string $key
     *   La clé à effacer.
     *
     * @throws InvalidArgumentException
     *   Si la chaîne de caractères $key n'est pas une valeur légale, une \Psr\Cache\InvalidArgumentException doit être envoyée.
     *
     * @return bool
     *   Vrai si l'objet a été retiré avec succès. Faux s'il y a eu une erreur.
     */
    public function deleteItem($key);

    /**
     * Retire plusieurs éléments du groupe.
     *
     * @param string[] $keys
     *   Un ensemble de clés qui doivent être retirées du groupe.
     *
     * @throws InvalidArgumentException
     *   Si l'une des clés en $keys n'a pas de valeur légale, une \Psr\Cache\InvalidArgumentException doit être envoyée.
     *
     * @return bool
     *   Vrai si les objets ont été retirés avec succès. Faux s'il y a eu une erreur.
     */
    public function deleteItems(array $keys);

    /**
     * Conserve immédiatement un élément de la cache.
     *
     * @param CacheItemInterface $item
     *   L'élément de cache à sauvegarder.
     *
     * @return bool
     *   Vrai si l'objet a été conservé avec succès. Faux s'il y a eu une erreur.
     */
    public function save(CacheItemInterface $item);

    /**
     * Définit un élément de cache qui sera conservé plus tard.
     *
     * @param CacheItemInterface $item
     *   L'élément de cache à sauvegarder.
     *
     * @return bool
     *   Faux si l'élément ne peut pas être mis en file d'attente ou si un engagement a été tenté et a échoué. Vrai dans le cas contraire.
     */
    public function saveDeferred(CacheItemInterface $item);

    /**
     * Conserve tous les éléments de cache reportés.
     *
     * @return bool
     *   Vrai si tous les objets qui n'ont pas encore été conservés ont été sauvegardés avec succès ou s'il n'y en a pas eu. Faux dans le cas contraire.
     */
    public function commit();
}
```

### CacheException

Cette interface d'exception est destinée à être utilisée lorsque des erreurs critiques se produisent, mais sans s'y limiter la configuration du cache comme la connexion à un serveur de cache ou des informations d'identification non valides fournies.

Toute exception lancée par une bibliothèque d'implémentation doit implémenter cette interface.

```php
<?php

namespace Psr\Cache;

/**
 * Interface d'exception pour toutes les exceptions lancées par une bibliothèque d'implémentation.
 */
interface CacheException
{
}
```

### InvalidArgumentException

```php
<?php

namespace Psr\Cache;

/**
 * Interface d'exception pour les arguments de cache non valables.
 *
 * Chaque fois qu'un argument non valide est passé dans une méthode, il doit lancer une classe d'exception qui implémente Psr\Cache\InvalidArgumentException.
 */
interface InvalidArgumentException extends CacheException
{
}
```