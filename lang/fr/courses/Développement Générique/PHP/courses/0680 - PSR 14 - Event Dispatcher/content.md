## Objectif du PSR 14

Event Dispatching est un mécanisme courant et bien testé qui permet aux développeurs d'injecter de la logique dans une application facilement et de manière cohérente.

L'objectif de ce PSR est d'établir un mécanisme commun pour l'extension et la collaboration basées sur les événements afin que les bibliothèques et les composants puissent être réutilisés plus librement entre diverses applications et frameworks.

L'objectif est de disposer d'interfaces communes pour la distribution et la gestion des événements permettant aux développeurs de créer des bibliothèques pouvant interagir avec de nombreux frameworks et autres bibliothèques de façon commune.

Quelques exemples :

- Un cadre de sécurité qui empêchera l'enregistrement/l'accès aux données lorsqu'un utilisateur n'a pas l'autorisation.
- Un système commun de mise en cache pleine page.
- Bibliothèques qui étendent d'autres bibliothèques, quel que soit le framework dans lequel elles sont toutes deux intégrées.
- Un package de journalisation pour suivre toutes les actions entreprises dans l'application

## Définitions

- ```Event``` - Un événement est un message produit par un émetteur. Il peut s'agir de n'importe quel objet PHP arbitraire.
- ```Listener``` - Un écouteur est tout appelable PHP qui s'attend à recevoir un événement. Le même événement peut être passé à zéro ou plusieurs écouteurs. Un écouteur peut mettre en file d'attente un autre comportement asynchrone s'il le souhaite.
- ```Emitter``` - Un émetteur est tout code arbitraire qui souhaite envoyer un événement. Ceci est également connu sous le nom de "code d'appel". Il n'est représenté par aucune structure de données particulière, mais fait référence au cas d'utilisation.
- ```Dispatcher``` - Un Dispatcher est un objet de service auquel un émetteur donne un objet Event. Le répartiteur est chargé de s'assurer que l'événement est transmis à tous les auditeurs pertinents, mais doit reporter la détermination des auditeurs responsables à un fournisseur d'écouteurs.
- ```Listener Provider``` - Un fournisseur d'écoute est chargé de déterminer quels auditeurs sont pertinents pour un événement donné, mais ne doit pas appeler les auditeurs lui-même. Un fournisseur d'écoute peut spécifier zéro ou plusieurs écouteurs pertinents.

## Les Events

Les événements sont des objets qui servent d'unité de communication entre un émetteur et les auditeurs appropriés.

Les objets d'événement peuvent être modifiables si le cas d'utilisation appelle des écouteurs fournissant des informations à l'émetteur. Cependant, si une telle communication bidirectionnelle n'est pas nécessaire, il est recommandé que l'événement soit défini comme immuable ; c'est-à-dire défini de telle sorte qu'il manque de méthodes de mutation.

Les implémenteurs doivent supposer que le même objet sera passé à tous les auditeurs.

Il est recommandé, mais non obligatoire, que les objets Événement prennent en charge la sérialisation et la désérialisation sans perte ; ```$event == unserialize(serialize($event))``` devrait être vrai. Les objets peuvent exploiter l'interface ```Serializable``` de PHP , ```__sleep()``` ou ```__wakeup()``` des méthodes magiques, ou des fonctionnalités de langage similaires, le cas échéant.

## Les stoppable events

Un événement stoppable est un cas particulier d'événement qui contient des moyens supplémentaires d'empêcher l'appel d'autres écouteurs. Il est indiqué par la mise en œuvre du ```StoppableEventInterface```. Un événement qui implémente ```StoppableEventInterface``` soit revenir à “true” partir du ```isPropagationStopped()``` moment où l'événement qu'il représente est terminé. C'est à l'implémentation de la classe de déterminer quand c'est. Par exemple, un événement qui demande qu'un ```RequestInterface``` objet PSR-7 soit mis en correspondance avec un ```ResponseInterface``` objet correspondant peut avoir une ```setResponse(ResponseInterface $res)``` méthode à appeler par un écouteur, ce qui provoque ```isPropagationStopped()``` le retour de “true”.

## Les listeners

Un écouteur peut être n'importe quel appel PHP. Un écouteur doit avoir un et un seul paramètre, qui est l'événement auquel il répond. Les auditeurs devraient saisir ce paramètre de manière aussi précise que cela est pertinent pour leur cas d'utilisation ; c'est-à-dire qu'un indice de type Listener peut sur une interface pour indiquer qu'elle est compatible avec tout type d'événement qui implémente cette interface, ou avec une implémentation spécifique de cette interface. Un écouteur devrait avoir un “void” retour et devrait taper un indice qui retourne explicitement. Un Dispatcher doit ignorer les valeurs de retour des Listeners. Un écouteur peut déléguer des actions à un autre code. Cela inclut un Listener étant un wrapper mince autour d'un objet qui exécute la logique métier réelle. Un auditeur peut mettre en file d'attente les informations de l'événement pour un traitement ultérieur par un processus secondaire, en utilisant cron, un serveur de file d'attente ou des techniques similaires. Il peut sérialiser l'objet Event lui-même pour le faire ; cependant, il faut veiller à ce que tous les objets Event ne soient pas sérialisables en toute sécurité. Un processus secondaire doit supposer que toute modification qu'il apporte à un objet Événement ne se propagera pas aux autres auditeurs.

## Les dispatchers

Un Dispatcher est un objet de service implémentant “EventDispatcherInterface”. Il est chargé de récupérer les écouteurs d'un fournisseur d'écouteurs pour l'événement distribué et d'appeler chaque écouteur avec cet événement.

Un répartiteur :

- doit appeler les écouteurs de manière synchrone dans l'ordre où ils sont renvoyés par un ```ListenerProvider```.
- doit retourner le même objet Event qu'il a été passé après avoir appelé les écouteurs.
- ne doit pas retourner à l'émetteur tant que tous les écouteurs n'ont pas été exécutés. Si un événement stoppable est passé, un répartiteur
- doit appeler ```isPropagationStopped()``` l'événement avant que chaque écouteur n'ait été appelé. Si cette méthode retourne, “true” elle doit retourner l'événement à l'émetteur immédiatement et ne doit pas appeler d'autres écouteurs. Cela implique que si un événement est passé au ```Dispatcher``` qui revient toujours “true” de ```isPropagationStopped()```, aucun écouteur ne sera appelé.

Un dispatcher devrait supposer que tout écouteur qui lui est renvoyé par un fournisseur d'écouteur est de type sûr. C'est-à-dire que le Dispatcher devrait supposer que l'appel ```$listener($event)``` ne produira pas de “TypeError”.

La gestion des erreurs :

Une exception ou une erreur lancée par un écouteur DOIT bloquer l'exécution de tout autre écouteur. Une exception ou une erreur lancée par un écouteur DOIT être autorisée à se propager jusqu'à l'émetteur.

Un Dispatcher PEUT attraper un objet lancé pour le consigner, permettre que des actions supplémentaires soient prises, etc., mais DOIT ensuite relancer l'objet jetable d'origine.

## Les listeners provider

Un listener provider est un objet de service chargé de déterminer quels écouteurs sont pertinents et doivent être appelés pour un événement donné. Il peut déterminer à la fois quels auditeurs sont pertinents et l'ordre dans lequel les renvoyer par le moyen qu'il choisit. Cela peut inclure :

- Permettre une certaine forme de mécanisme d'enregistrement afin que les implémenteurs puissent affecter un écouteur à un événement dans un ordre fixe.
- Dérivation d'une liste d'auditeurs applicables par réflexion basée sur le type et les interfaces implémentées de l'événement.
- Génération d'une liste compilée d'écouteurs à l'avance qui peuvent être consultés au moment de l'exécution.
- Implémenter une forme de contrôle d'accès afin que certains écouteurs ne soient appelés que si l'utilisateur actuel dispose d'une certaine autorisation.
- Extraire certaines informations d'un objet référencé par l'événement, tel qu'une entité, et appeler des méthodes de cycle de vie prédéfinies sur cet objet.
- Déléguer sa responsabilité à un ou plusieurs autres listener provider en utilisant une logique arbitraire.

Toute combinaison de ce qui précède, ou d'autres mécanismes, peut être utilisée comme vous le souhaitez. Les listener provider devraient utiliser le nom de classe d'un événement pour différencier un événement d'un autre. Ils peuvent également considérer toute autre information sur l'événement, le cas échéant. Les listener provider doivent traiter les types parents de la même manière que le propre type de l'événement lorsqu'ils déterminent l'applicabilité de l'écouteur. Dans le cas suivant :

``` php
class A {}

class B extends A {}

$b = new B();

function listener(A $event): void {};
```

Un fournisseur d'écoute ```listener()``` doit traiter comme un écouteur applicable pour ```$b```, car il est de type compatible, à moins que d'autres critères ne l'empêchent de le faire.