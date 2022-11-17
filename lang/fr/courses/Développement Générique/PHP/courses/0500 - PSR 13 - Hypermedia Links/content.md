Les liens hypermédias deviennent une partie de plus en plus importante du Web, à la fois dans les contextes HTML et dans divers contextes de format API. Cependant, il n'y a pas de format hypermédia commun unique, ni de manière commune de représenter les liens entre les formats.

Cette spécification vise à fournir aux développeurs PHP une manière simple et courante de représenter un lien hypermédia indépendamment du format de sérialisation utilisé. Cela permet à son tour à un système de sérialiser une réponse avec des liens hypermédias dans un ou plusieurs formats de fil indépendamment du processus de décision de ces liens.

## Les liens de base

Un Lien Hypermédia se compose, au minimum :

- Un URI représentant la ressource cible référencée.
- Une relation définissant la relation entre la ressource cible et la source. Divers autres attributs du lien peuvent exister, selon le format utilisé. Comme les attributs supplémentaires ne sont pas bien standardisés ou universels, cette spécification ne cherche pas à les standardiser. Aux fins de la présente spécification, les définitions suivantes s'appliquent.
- Objet d'implémentation - Un objet qui implémente l'une des interfaces définies par cette spécification.
- Sérialiseur - Une bibliothèque ou un autre système qui prend un ou plusieurs objets Link et en produit une représentation sérialisée dans un format défini.

## Les attributs

Tous les liens peuvent inclure zéro ou plusieurs attributs supplémentaires au-delà de l'URI et de la relation. Il n'y a pas de registre formel des valeurs autorisées ici, et la validité des valeurs dépend du contexte et souvent d'un format de sérialisation particulier. Les valeurs couramment prises en charge incluent 'hreflang', 'title' et 'type'. Les sérialiseurs peuvent omettre des attributs sur un objet lien si cela est requis par le format de sérialisation. Cependant, les sérialiseurs devraient coder tous les attributs fournis possibles afin de permettre l'extension d'utilisateur à moins que cela ne soit empêché par la définition d'un format de sérialisation. Certains attributs (généralement “hreflang”) peuvent apparaître plusieurs fois dans leur contexte. Par conséquent, une valeur d'attribut PEUT être un tableau de valeurs plutôt qu'une simple valeur. Les sérialiseurs peuvent coder ce tableau dans le format approprié au format sérialisé (comme une liste séparée par des espaces, une liste séparée par des virgules, etc.). Si un attribut donné n'est pas autorisé à avoir plusieurs valeurs dans un contexte particulier, les sérialiseurs doivent utiliser la première valeur fournie et ignorer toutes les valeurs suivantes. Si une valeur d'attribut est boolean “true”, les sérialiseurs peuvent utiliser des formes abrégées si cela est approprié et pris en charge par un format de sérialisation. Par exemple, HTML permet aux attributs de n'avoir aucune valeur lorsque la présence de l'attribut a une signification booléenne. Cette règle s'applique si et seulement si l'attribut est boolean “true”, pas pour toute autre valeur "véridique" en PHP telle que l'entier 1. Si une valeur d'attribut est boolean “false”, les sérialiseurs devraient omettre entièrement l'attribut à moins que cela ne change la signification sémantique du résultat. Cette règle s'applique si et seulement si l'attribut est boolean “false”, pas pour toute autre valeur "false" en PHP telle que l'entier 0.

## Les relations

Les relations de lien sont définies sous forme de chaînes et sont soit un simple mot-clé dans le cas d'une relation définie publiquement, soit un URI absolu dans le cas d'une relation privée. Dans le cas où un mot clé simple est utilisé, il devrait correspondre à celui du registre IANA. Facultativement, le registre microformats.org peut être utilisé, mais cela peut ne pas être valide dans tous les contextes. Une relation qui n'est pas définie dans l'un des registres ci-dessus ou dans un registre public similaire est considérée comme « privée », c'est-à-dire spécifique à une application ou à un cas d'utilisation particulier. De telles relations doivent utiliser un URI absolu.

## Les modèles de liens

La RFC 6570 définit un format pour les modèles d'URI, autrement dit un modèle pour un URI qui doit être rempli avec les valeurs fournies par un outil client. Certains formats hypermédias prennent en charge les liens modélisés tandis que d'autres ne le font pas, et peuvent avoir une manière spéciale d'indiquer qu'un lien est un modèle. Un sérialiseur pour un format qui ne prend pas en charge les modèles d'URI doit ignorer tous les liens modélisés qu'il rencontre.

## Les fournisseurs évolutifs

Dans certains cas, un fournisseur de liens peut avoir besoin de pouvoir ajouter des liens supplémentaires. Dans d'autres, un fournisseur de liens est nécessairement en lecture seule, avec des liens dérivés au moment de l'exécution d'une autre source de données. Pour cette raison, les fournisseurs modifiables sont une interface secondaire qui peut éventuellement être implémentée.

En outre, certains objets Fournisseur de liaison, tels que les objets Réponse PSR-7, sont par conception immuables. Cela signifie que les méthodes pour y ajouter des liens sur place seraient incompatibles. Par conséquent, la “EvolvableLinkProviderInterface” méthode unique de ' nécessite qu'un nouvel objet soit renvoyé, identique à l'original, mais avec un objet Link supplémentaire inclus.

## Les objets de liaison évolutifs

Les objets de lien sont dans la plupart des cas des objets de valeur. En tant que tel, leur permettre d'évoluer de la même manière que les objets de valeur PSR-7 est une option utile. Pour cette raison, une “EvolvableLinkInterface” supplémentaire est incluse qui fournit des méthodes pour produire de nouvelles instances d'objet avec un seul changement. Le même modèle est utilisé par PSR-7 et, grâce au comportement de copie sur écriture de PHP, il est toujours efficace en termes de CPU et de mémoire.

Cependant, il n'existe pas de méthode évolutive pour les valeurs modélisées, car la valeur modélisée d'un lien est basée exclusivement sur la valeur href. Il ne doit pas  être défini indépendamment, mais dérivé du fait que la valeur href est ou non un modèle de lien RFC 6570.

## Les interfaces

“LinkInterface” :

```php
<?php

namespace Psr\Link;

interface LinkInterface
{
    /**
     * @return string
     */
    public function getHref();

    /**
     * @return bool
     */
    public function isTemplated();

    /**
     * @return string[]
     */
    public function getRels();

    /**
     * @return array
     */
    public function getAttributes();
}
```

“EvolvableLinkInterface” :

```php
<?php

namespace Psr\Link;

interface EvolvableLinkInterface extends LinkInterface
{
    /**
     * @param string $href
     * @return static
     */
    public function withHref($href);

    /**
     * @param string $rel
     * @return static
     */
    public function withRel($rel);

    /**
     * @param string $rel
     * @return static
     */
    public function withoutRel($rel);

    /**
     * @param string $attribute
     * @param string $value
     * @return static
     */
    public function withAttribute($attribute, $value);

    /**
     * @param string $attribute
     * @return static
     */
    public function withoutAttribute($attribute);
}
```

“LinkProviderInterface” :

```php
<?php

namespace Psr\Link;

interface LinkProviderInterface
{
    /**
     * @return LinkInterface[]|\Traversable
     */
    public function getLinks();

    /**
     * @return LinkInterface[]|\Traversable
     */
    public function getLinksByRel($rel);
}
```

“EvolvableLinkProviderInterface” :

```php
<?php

namespace Psr\Link;

interface EvolvableLinkProviderInterface extends LinkProviderInterface
{
    /**
     * @param LinkInterface $link
     * @return static
     */
    public function withLink(LinkInterface $link);

    /**
     * @param LinkInterface $link
     * @return static
     */
    public function withoutLink(LinkInterface $link);
}
```