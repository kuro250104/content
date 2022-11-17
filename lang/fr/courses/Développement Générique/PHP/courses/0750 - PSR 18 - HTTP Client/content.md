## Objectif du PSR 18

Le but de ce PSR est de permettre aux développeurs de créer des bibliothèques découplées des implémentations clientes HTTP. Cela rendra les bibliothèques plus réutilisables, car cela réduira le nombre de dépendances et la probabilité de conflits de versions.

Un deuxième objectif est que les clients HTTP puissent être remplacés selon le principe de substitution de Liskov. Cela signifie que tous les clients doivent se comporter de la même manière lors de l'envoi d'une demande.

## Définitions

- ```Client``` - Un client est une bibliothèque qui implémente cette spécification dans le but d'envoyer des messages de demande HTTP compatibles PSR-7 et de renvoyer un message de réponse HTTP compatible PSR-7 à une bibliothèque appelante.
- ```Calling Library``` - Une bibliothèque d'appels est tout code qui utilise un client. Il n'implémente pas les interfaces de cette spécification mais consomme un objet qui les implémente (un Client).

## Client

Un Client est un objet implémentant ```ClientInterface```.

Un client peut:

- Envoyer une requête HTTP modifiée à partir de celle qui a été fournie. Par exemple, il pourrait compresser un corps de message sortant.
- Modifier une réponse HTTP reçue avant de la renvoyer à la bibliothèque appelante. Par exemple, il peut décompresser le corps d'un message entrant.

Si un client choisit de modifier soit la demande HTTP, soit la réponse HTTP, il doit s'assurer que l'objet reste cohérent en interne. Par exemple, si un client choisit de décompresser le corps du message, il doit également supprimer l'en- “Content-Encoding”tête et ajuster l'en- “Content-Length”tête. Notez qu'en conséquence, puisque les objets PSR-7 sont immuables , la bibliothèque appelant ne doit pas supposer que l'objet transmis “ClientInterface::sendRequest()” sera le même objet PHP qui est réellement envoyé. Par exemple, l'objet Request qui est renvoyé par une exception peut être un objet différent de celui passé à “sendRequest()”, donc la comparaison par référence (===) n'est pas possible.Un client doit rassembler une réponse HTTP 1xx à plusieurs étapes elle-même afin que ce qui est renvoyé à la bibliothèque appelante soit une réponse HTTP valide de code d'état 200 ou supérieur.

## Error handling

Un client ne doit pas traiter une demande HTTP ou une réponse HTTP bien formée comme une condition d'erreur. Par exemple, les codes d'état de réponse dans la plage 400 et 500 ne doivent pas provoquer d'exception et doivent être renvoyés à la bibliothèque appelant normalement. Un client doit lancer une instance de ```Psr\Http\Client\ClientExceptionInterface``` si et seulement s'il est incapable d'envoyer la demande HTTP du tout ou si la réponse HTTP n'a pas pu être analysée dans un objet de réponse PSR-7. Si une demande ne peut pas être envoyée parce que le message de demande n'est pas une demande HTTP bien formée ou qu'il manque une information critique (telle qu'un hôte ou une méthode), le client doit lancer une instance de ```Psr\Http\Client\RequestExceptionInterface```. Si la demande ne peut pas être envoyée en raison d'une défaillance du réseau de quelque nature que ce soit, y compris un délai d'attente, le client doit lancer une instance de ```Psr\Http\Client\NetworkExceptionInterface```. Les clients peuvent lancer des exceptions plus spécifiques que celles définies ici (a ```TimeOutException``` ou ```HostNotFoundException``` par exemple), à ​​condition qu'ils implémentent l'interface appropriée définie ci-dessus.

## Les interfaces

“ClientInterface” :

```php
namespace Psr\Http\Client;

use Psr\Http\Message\RequestInterface;
use Psr\Http\Message\ResponseInterface;

interface ClientInterface
{
    /**
     * @param RequestInterface $request
     * @return ResponseInterface
     * @throws \Psr\Http\Client\ClientExceptionInterface
     */
    public function sendRequest(RequestInterface $request): ResponseInterface;
}
```

“ClientExceptionInterface” :

```php
namespace Psr\Http\Client;

interface ClientExceptionInterface extends \Throwable
{
}
```

“RequestExceptionInterface” :

```php
namespace Psr\Http\Client;

use Psr\Http\Message\RequestInterface;

interface RequestExceptionInterface extends ClientExceptionInterface
{
    /**
     * @return RequestInterface
     */
    public function getRequest(): RequestInterface;
}
```

“NetworkExceptionInterface” :

```php
namespace Psr\Http\Client;

use Psr\Http\Message\RequestInterface;

interface NetworkExceptionInterface extends ClientExceptionInterface
{
    /**
     * @return RequestInterface
     */
    public function getRequest(): RequestInterface;
}
```