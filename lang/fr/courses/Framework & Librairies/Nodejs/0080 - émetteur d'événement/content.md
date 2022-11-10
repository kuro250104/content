De nombreux objets d'un nœud émettent des événements, par exemple, un net.Server émet un événement chaque fois qu'un pair se connecte à lui, un fs.readStream émet un événement lorsque le fichier est ouvert. Tous les objets qui émettent des événements sont des instances de events.EventEmitter.

## Classe EventEmitter

Comme nous l'avons vu dans la section précédente, la classe EventEmitter se trouve dans le module events. Elle est accessible via le code suivant :

```js
// Import events module
var events = require('events');

// Create an eventEmitter object
var eventEmitter = new events.EventEmitter();
```

Lorsqu'une instance d'EventEmitter est confrontée à une erreur, elle émet un événement "error". Lorsqu'un nouvel auditeur est ajouté, l'événement "newListener" est déclenché et lorsqu'un auditeur est supprimé, l'événement "removeListener" est déclenché.

EventEmitter fournit plusieurs propriétés comme **on** et **emit**. La propriété on est utilisée pour lier une fonction à l'événement et emit est utilisée pour déclencher un événement.

## Méthodes

- ```addListener(event, listener)``` : Ajoute un écouteur à la fin du tableau des écouteurs pour l'événement spécifié. Aucune vérification n'est faite pour savoir si le listener a déjà été ajouté. Des appels multiples passant la même combinaison d'événement et d'écouteur auront pour résultat que l'écouteur sera ajouté plusieurs fois. Renvoie l'émetteur, de sorte que les appels peuvent être enchaînés.
- ```on(event, listener)``` : Ajoute un écouteur à la fin du tableau des écouteurs pour l'événement spécifié. Aucune vérification n'est faite pour savoir si le listener a déjà été ajouté. Des appels multiples passant la même combinaison d'événement et de listener auront pour résultat que le listener sera ajouté plusieurs fois. Retourne l'émetteur, de sorte que les appels peuvent être enchaînés.
- ```once(event, listener)``` : Ajoute un écouteur unique à l'événement. Cet écouteur n'est invoqué que la prochaine fois que l'événement est déclenché, après quoi il est supprimé. Retourne l'émetteur, donc les appels peuvent être enchaînés.
- ```removeListener(event, listener)``` : Supprime un écouteur du tableau des écouteurs pour l'événement spécifié. Attention - Cela modifie les indices du tableau de listers derrière le listener. removeListener supprimera, au maximum, une instance d'un listener du tableau de listers. Si un seul écouteur a été ajouté plusieurs fois au tableau d'écouteurs pour l'événement spécifié, alors removeListener doit être appelé plusieurs fois pour supprimer chaque instance. Retourne l'émetteur, de sorte que les appels peuvent être enchaînés.
- ```removeAllListeners([event])``` : Supprime tous les listeners, ou ceux de l'événement spécifié. Ce n'est pas une bonne idée de supprimer des listeners qui ont été ajoutés ailleurs dans le code, en particulier lorsque c'est sur un émetteur que vous n'avez pas créé (par exemple, des sockets ou des flux de fichiers). Retourne l'émetteur, donc les appels peuvent être enchaînés.
- ```setMaxListeners(n)``` : Par défaut, EventEmitters affichera un avertissement si plus de 10 listeners sont ajoutés pour un événement particulier. C'est un défaut utile qui aide à trouver les fuites de mémoire. Il est évident que tous les Emitters ne doivent pas être limités à 10. Cette fonction permet d'augmenter ce nombre. Mettre à zéro pour un nombre illimité.
- ```listeners(event)``` : Renvoie un tableau d'écouteurs pour l'événement spécifié.
- ```emit(event, [arg1], [arg2], [...])``` : Exécute chacun des listeners dans l'ordre avec les arguments fournis. Retourne true si l'événement a des listeners, false sinon.

## Méthodes de classe

- ```listenerCount(emitter, event)``` : Retourne le nombre d'auditeurs pour un événement donné.

## Événements

### newListener

- **event** - String : le nom de l'événement
- **listener** - Function : la fonction de gestion de l'événement

Cet événement est émis chaque fois qu'un auditeur est ajouté. Lorsque cet événement est déclenché, il se peut que l'écouteur n'ait pas encore été ajouté au tableau des écouteurs de l'événement.

### removeListener

- **event** - String Le nom de l'événement
- **listener** - Function La fonction de gestion de l'événement

Cet événement est émis chaque fois que quelqu'un supprime un auditeur. Lorsque cet événement est déclenché, il se peut que l'auditeur n'ait pas encore été retiré du tableau des auditeurs de l'événement.

## Exemple

Créez un fichier js nommé main.js avec le code Node.js suivant :

```js
var events = require('events');
var eventEmitter = new events.EventEmitter();

// listener #1
var listner1 = function listner1() {
    console.log('listner1 executed.');
}

// listener #2
var listner2 = function listner2() {
    console.log('listner2 executed.');
}

// Bind the connection event with the listner1 function
eventEmitter.addListener('connection', listner1);

// Bind the connection event with the listner2 function
eventEmitter.on('connection', listner2);

var eventListeners = require('events').EventEmitter.listenerCount
    (eventEmitter,'connection');
console.log(eventListeners + " Listner(s) listening to connection event");

// Fire the connection event 
eventEmitter.emit('connection');

// Remove the binding of listner1 function
eventEmitter.removeListener('connection', listner1);
console.log("Listner1 will not listen now.");

// Fire the connection event 
eventEmitter.emit('connection');

eventListeners = require('events').EventEmitter.listenerCount(eventEmitter,'connection');
console.log(eventListeners + " Listner(s) listening to connection event");

console.log("Program Ended.");
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```js
$ node main.js
```

Vérifier la sortie.

```bash
2 Listner(s) listening to connection event
listner1 executed.
listner2 executed.
Listner1 will not listen now.
listner2 executed.
1 Listner(s) listening to connection event
Program Ended.
```