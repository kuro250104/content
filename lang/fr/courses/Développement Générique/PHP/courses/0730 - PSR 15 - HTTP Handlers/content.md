Les gestionnaires de requêtes HTTP sont un élément fondamental de toute application Web. Le code côté serveur reçoit un message de demande, le traite et produit un message de réponse. L'intergiciel HTTP est un moyen de déplacer le traitement commun des demandes et des réponses loin de la couche d'application.

Les interfaces décrites dans ce document sont des abstractions pour les gestionnaires de demandes et les middlewares.

## Request Handlers

Un gestionnaire de requêtes est un composant individuel qui traite une requête et produit une réponse, comme défini par PSR-7.

Un gestionnaire de demande peut lever une exception si les conditions de la demande l'empêchent de produire une réponse. Le type d'exception n'est pas défini.

Les gestionnaires de requêtes utilisant cette norme doivent implémenter l'interface suivante : ```Psr\Http\Server\RequestHandlerInterface```

## Middleware

Un composant middleware est un composant individuel participant, souvent avec d'autres composants middleware, au traitement d'une demande entrante et à la création d'une réponse résultante, comme défini par PSR-7.

Un composant middleware peut créer et retourner une réponse sans déléguer à un gestionnaire de demande, si des conditions suffisantes sont remplies.

Le middleware utilisant cette norme doit implémenter l'interface suivante : ```Psr\Http\Server\MiddlewareInterface```

## Générer les réponses

Il est recommandé que tout middleware ou gestionnaire de requêtes qui génère une réponse compose soit un prototype d'un PSR-7, ```ResponseInterface``` soit une fabrique capable de générer une ```ResponseInterface``` instance afin d'éviter de dépendre d'une implémentation de message HTTP spécifique.

## Traitement des exceptions

Il est recommandé que toute application utilisant un middleware inclut un composant qui intercepte les exceptions et les convertit en réponses. Ce middleware devrait être le premier composant exécuté et envelopper tous les traitements ultérieurs pour s'assurer qu'une réponse est toujours générée.

## Les interfaces

“RequestHandlerInterface” :

```php
namespace Psr\Http\Server;

use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;

interface RequestHandlerInterface
{
    public function handle(ServerRequestInterface $request): ResponseInterface;
}
```

“MiddlewareInterface” :

```php
namespace Psr\Http\Server;

use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;

interface MiddlewareInterface
{
    public function process(ServerRequestInterface $request, RequestHandlerInterface $handler): ResponseInterface;
}
```