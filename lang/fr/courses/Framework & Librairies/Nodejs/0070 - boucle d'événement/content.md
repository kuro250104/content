Node.js est une application monofilaire, mais elle peut prendre en charge la concurrence via le concept d'événement et de callbacks. Toutes les API de Node.js sont asynchrones et comme elles sont monofilaires, elles utilisent des appels de fonctions asynchrones pour maintenir la concurrence. Node utilise le modèle de l'observateur. Le thread Node garde une boucle d'événement et chaque fois qu'une tâche est terminée, il déclenche l'événement correspondant qui signale à la fonction d'écoute d'événement de s'exécuter.

## Programmation pilotée par les événements

Node.js utilise fortement les événements et c'est aussi l'une des raisons pour lesquelles Node.js est assez rapide par rapport à d'autres technologies similaires. Dès que Node démarre son serveur, il initie simplement ses variables, déclare des fonctions, puis attend simplement que l'événement se produise.

Dans une application pilotée par les événements, il y a généralement une boucle principale qui écoute les événements, puis déclenche une fonction de rappel lorsqu'un de ces événements est détecté.

![Représentation d'une boucle dans une application pilotée par les événements](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Nodejs/0070%20-%20boucle%20d'%C3%A9v%C3%A9nement/images/image1.jpg)

Bien que les événements ressemblent beaucoup aux callbacks, la différence réside dans le fait que les fonctions de callback sont appelées lorsqu'une fonction asynchrone renvoie son résultat, alors que la gestion des événements fonctionne sur le modèle de l'observateur. Les fonctions qui écoutent les événements agissent comme des observateurs. Lorsqu'un événement est déclenché, sa fonction d'écoute commence à s'exécuter. Node.js dispose de plusieurs événements intégrés disponibles par le biais du module events et de la classe EventEmitter, qui sont utilisés pour lier les événements et les écouteurs d'événements comme suit :

```js
// Import events module
var events = require('events');

// Create an eventEmitter object
var eventEmitter = new events.EventEmitter();
```

Voici la syntaxe pour lier un gestionnaire d'événement à un événement :

```js
// Bind event and event  handler as follows
eventEmitter.on('eventName', eventHandler);
```

Nous pouvons lancer un événement de manière programmatique, comme suit:

```js
// Fire an event 
eventEmitter.emit('eventName');
```

## Exemple

Créez un fichier js nommé main.js avec le code suivant :

```js
// Import events module
var events = require('events');

// Create an eventEmitter object
var eventEmitter = new events.EventEmitter();

// Create an event handler as follows
var connectHandler = function connected() {
    console.log('connection succesful.');
    
    // Fire the data_received event 
    eventEmitter.emit('data_received');
}

// Bind the connection event with the handler
eventEmitter.on('connection', connectHandler);
 
// Bind the data_received event with the anonymous function
eventEmitter.on('data_received', function() {
    console.log('data received succesfully.');
});

// Fire the connection event 
eventEmitter.emit('connection');

console.log("Program Ended.");
```

Maintenant, essayons d'exécuter le programme ci-dessus et de vérifier sa sortie :

```bash
$ node main.js
```

IT devrait produire le résultat suivant :

```bash
connection successful.
data received successfully.
Program Ended.
```

## Comment fonctionnent les applications Node ?

Dans l'application Node, toute fonction asynchrone accepte un callback comme dernier paramètre et une fonction callback accepte une erreur comme premier paramètre. Reprenons l'exemple précédent. Créez un fichier texte nommé input.txt avec le contenu suivant.

```bash
Microlead, le chemin vers le succès !!!!!
```

Créez un fichier js nommé main.js ayant le code suivant :

```js
var fs = require("fs");

fs.readFile('input.txt', function (err, data) {
    if (err) {
        console.log(err.stack);
        return;
    }
    console.log(data.toString());
});
console.log("Program Ended");
```

Ici, ```fs.readFile()``` est une fonction asynchrone dont le but est de lire un fichier. Si une erreur se produit pendant l'opération de lecture, l'objet **err** contiendra l'erreur correspondante, sinon data contiendra le contenu du fichier. **readFile** transmet err et data à la fonction de rappel une fois l'opération de lecture terminée, qui imprime finalement le contenu.

```bash
Program Ended
Microlead, le chemin vers le succès !!!!!
```