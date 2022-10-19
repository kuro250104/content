La mise en cache est un moyen courant d'améliorer les performances de tout projet, faisant des bibliothèques de mise en cache l'une des fonctionnalités les plus courantes de nombreux frameworks et bibliothèques. L'interopérabilité à ce niveau signifie que les bibliothèques peuvent supprimer leurs propres implémentations de mise en cache et s'appuyer facilement sur celle qui leur est fournie par le framework ou sur une autre bibliothèque de cache dédiée.

PSR-6 résout déjà ce problème, mais de manière assez formelle et verbeuse pour ce dont les cas d'utilisation les plus simples ont besoin. Cette approche plus simple vise à construire une interface rationalisée standardisée pour les cas courants. Il est indépendant du PSR-6, mais a été conçu pour rendre la compatibilité avec le PSR-6 aussi simple que possible.

## Définitions

Les définitions de la bibliothèque d'appel, de la bibliothèque d'implémentation, de la durée de vie, de l'expiration et de la clé sont copiées de PSR-6 car les mêmes hypothèses sont vraies.

- ```Calling Library``` - La bibliothèque ou le code qui a réellement besoin des services de cache. Cette bibliothèque utilisera des services de mise en cache qui implémentent les interfaces de cette norme, mais n'aura autrement aucune connaissance de la mise en œuvre de ces services de mise en cache.

- ```Implementing Library``` - Cette bibliothèque est responsable de la mise en œuvre de cette norme afin de fournir des services de mise en cache à toute bibliothèque appelant. La bibliothèque d'implémentation doit fournir une classe implémentant l'interface ```Psr\SimpleCache\CacheInterface```. La mise en œuvre des bibliothèques doit prendre en charge au minimum la fonctionnalité TTL comme décrite ci-dessous avec une granularité à la seconde entière.
- ```TTL``` - La durée de vie (TTL) d'un élément est le temps qui s'écoule entre le moment où cet élément est stocké et celui où il est considéré comme périmé. Le TTL est normalement défini par un entier représentant le temps en secondes ou un objet DateInterval.
- ```Expiration``` - L'heure réelle à laquelle un élément est configuré pour devenir périmé. Ceci est calculé en ajoutant le TTL au moment où un objet est stocké.
Un élément avec un TTL de 300 secondes stocké à 1:30:00 aura une expiration de 1:35:00.
Les bibliothèques de mise en œuvre peuvent expirer un élément avant son heure d'expiration demandée, mais doivent traiter un élément comme expiré une fois que son heure d'expiration est atteinte. Si une bibliothèque appelant demande qu'un élément soit sauvegardé, mais ne spécifie pas de délai d'expiration, ou spécifie un délai d'expiration nul ou un TTL, une bibliothèque de mise en œuvre peut utiliser une durée par défaut configurée. Si aucune durée par défaut n'a été définie, la bibliothèque de mise en œuvre doit interpréter cela comme une demande de mise en cache de l'élément pour toujours, ou aussi longtemps que la mise en œuvre sous-jacente le prend en charge.
Si un TTL négatif ou nul est fourni, l'élément doit être supprimé du cache s'il existe, car il a déjà expiré.
- ```Key``` - Une chaîne d'au moins un caractère qui identifie de manière unique un élément mis en cache. Les bibliothèques de mise en œuvre doivent prendre en charge les clés composées des caractères “A-Z, a-z, 0-9, _”, et dans n'importe quel ordre de codage UTF-8 et d'une longueur allant jusqu'à 64 caractères. Les bibliothèques de mise en œuvre peuvent prendre en charge des caractères et des codages supplémentaires ou des longueurs plus longues, mais doivent prendre en charge au moins ce minimum. Les bibliothèques sont responsables de leur propre échappement des chaînes de clé, le cas échéant, mais doivent être capables de retourner la chaîne de clé originale non modifiée. Les caractères suivants sont réservés pour de futures extensions et ne doivent pas être pris en charge par l'implémentation des bibliothèques : ```{}()/\@:```
- ```Cache``` - Un objet qui implémente l'“Psr\SimpleCache\CacheInterface” interface.
- ```Cache Misses``` - Un cache miss renverra null et donc détecter si un stocké “null” n'est pas possible. C'est le principal écart par rapport aux hypothèses de PSR-6.

## Cache

Les mises en œuvre peuvent fournir un mécanisme permettant à un utilisateur de spécifier un TTL par défaut s'il n'en est pas spécifié pour un élément de cache spécifique. Si aucune valeur par défaut spécifiée par l'utilisateur n'est fournie, les mises en œuvre doivent par défaut la valeur légale maximale autorisée par la mise en œuvre sous-jacente. Si la mise en œuvre sous-jacente ne prend pas en charge le TTL, le TTL spécifié par l'utilisateur doit être ignoré en silence.

## Les données

Les bibliothèques d'implémentation doivent prendre en charge tous les types de données PHP sérialisables, notamment :

- ```Strings``` - Chaînes de caractères de taille arbitraire dans n'importe quel encodage compatible PHP.
- ```Integers``` - Tous les entiers de toute taille pris en charge par PHP, jusqu'à 64 bits signés.
- ```Floats``` - Toutes les valeurs à virgule flottante signées.
- ```Booleans``` - Vrai et Faux.
- ```Null``` - La valeur nulle (bien qu'elle ne soit pas distinguable d'un échec de cache lors de sa lecture).
- ```Arrays``` - Tableaux indexés, associatifs et multidimensionnels de profondeur arbitraire.
- ```Objects``` - Tout objet qui prend en charge la sérialisation et la désérialisation sans perte tel que ```$o == unserialize(serialize($o))```. Les objets peuvent exploiter l'interface sérialisable de PHP, ```__sleep()``` ou ```__wakeup()``` des méthodes magiques, ou des fonctionnalités de langage similaires, le cas échéant.

Toutes les données transmises à la bibliothèque de mise en œuvre doivent être retournées exactement telles qu'elles ont été transmises. Cela inclut le type de variable. C'est-à-dire que c'est une erreur de renvoyer (string) 5 si (int) 5 était la valeur enregistrée. L'implémentation des bibliothèques peut utiliser les fonctions serialize()/unserialize() de PHP en interne, mais n'est pas obligé de le faire. La compatibilité avec eux est simplement utilisée comme référence pour les valeurs d'objet acceptables.

S'il n'est pas possible de retourner la valeur sauvegardée exacte pour quelque raison que ce soit, les bibliothèques de mise en œuvre doivent répondre avec un cache manquant plutôt que des données corrompues.

## CacheInterface

L'interface de cache définit les opérations les plus élémentaires sur une collection d'entrées de cache, ce qui implique la lecture, l'écriture et la suppression d'éléments de cache individuels. De plus, il dispose de méthodes pour traiter plusieurs ensembles d'entrées de cache telles que l'écriture, la lecture ou la suppression de plusieurs entrées de cache à la fois. Ceci est utile lorsque vous avez beaucoup de lectures/écritures de cache à effectuer et vous permet d'effectuer vos opérations en un seul appel au serveur de cache en réduisant considérablement les temps de latence. Une instance de “CacheInterface” correspond à une seule collection d'éléments de cache avec un seul espace de nom de clé et équivaut à un "Pool" dans PSR-6. Différentes instances de “CacheInterface” peuvent être soutenues par le même magasin de données, mais doivent être logiquement indépendantes.

``` php
<?php

namespace Psr\SimpleCache;

interface CacheInterface
{
    /**
     * @param string $key    
     * @param mixed  $default
     * @return mixed
     * @throws \Psr\SimpleCache\InvalidArgumentException
     */
    public function get($key, $default = null);

    /**
     * @param string $key   
     * @param mixed                 
     * @param null|int|\DateInterval $ttl  
     * @return bool
     * @throws \Psr\SimpleCache\InvalidArgumentException
     */
    public function set($key, $value, $ttl = null);

    /**
     * @param string $key
     * @return bool
     * @throws \Psr\SimpleCache\InvalidArgumentException
     */
    public function delete($key);

    /**
     * @return bool
     */
    public function clear();

    /**
     * @param iterable $keys   
     * @param mixed 
     * @return iterable
     * @throws \Psr\SimpleCache\InvalidArgumentException
     */
    public function getMultiple($keys, $default = null);

    /**
     * @param iterable              
     * @param null|int|\DateInterval $ttl  
     * @return bool
     * @throws \Psr\SimpleCache\InvalidArgumentException
     */
    public function setMultiple($values, $ttl = null);

    /**
     * @param iterable $keys
     * @return bool
     * @throws \Psr\SimpleCache\InvalidArgumentException
     */
    public function deleteMultiple($keys);

    /**
     * @param string $key
     * @return bool
     * @throws \Psr\SimpleCache\InvalidArgumentException
     */
    public function has($key);
}
```

## CacheException

``` php
<?php

namespace Psr\SimpleCache;

interface CacheException
{
}
```

## InvalidArgumentException

``` php
<?php

namespace Psr\SimpleCache;

interface InvalidArgumentException extends CacheException
{}
```