Avant de créer une application "Hello, World !" à l'aide de Node.js, voyons les composants d'une application Node.js. Une application Node.js est composée des trois éléments importants suivants :

- **Importer les modules requis** - Nous utilisons la directive require pour charger les modules Node.js.
- **Créer un serveur** - Un serveur qui écoutera les requêtes du client comme le serveur HTTP Apache.
- **Lire la demande et retourner la réponse** - Le serveur créé dans une étape précédente lira la demande HTTP faite par le client qui peut être un navigateur ou une console et retournera la réponse.

## Créer une application Node.js

### Étape 1 - Importation du module requis

Nous utilisons la directive **require** pour charger le module http et stocker l'instance HTTP renvoyée dans une variable http, comme suit :

```js
var http = require("http");
```

### Étape 2 - Création du serveur

Nous utilisons l'instance http créée et appelons la méthode ```http.createServer()``` pour créer une instance de serveur, puis nous la lions au port 8081 en utilisant la méthode listen associée à l'instance de serveur. Passez-lui une fonction avec les paramètres **request** et **response**. Écrivez l'exemple d'implémentation pour qu'il retourne toujours "Hello World".

```js
http.createServer(function (request, response) {
    // Send the HTTP header 
    // HTTP Status: 200 : OK
    // Content Type: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});
    
    // Send the response body as "Hello World"
    response.end('Hello World\n');
}).listen(8081);

// Console will print the message
console.log('Server running at http://127.0.0.1:8081/');
```

Le code ci-dessus est suffisant pour créer un serveur HTTP qui écoute, c'est-à-dire qui attend une requête sur le port 8081 de la machine locale.

### Étape 3 - Test de la demande et de la réponse

Regroupons les étapes 1 et 2 dans un fichier appelé main.js et démarrons notre serveur HTTP comme indiqué ci-dessous :

```js
var http = require("http");

http.createServer(function (request, response) {
    // Send the HTTP header 
    // HTTP Status: 200 : OK
    // Content Type: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});
    
    // Send the response body as "Hello World"
    response.end('Hello World\n');
}).listen(8081);

// Console will print the message
console.log('Server running at http://127.0.0.1:8081/');
```

Maintenant, exécutez le fichier main.js pour démarrer le serveur comme suit -

```bash
$ node main.js
```

Vérifier la sortie. Le serveur a démarré.

```bash
Server running at http://127.0.0.1:8081/
```

## Faire une requête au serveur Node.js

Ouvrez l'url ```http://127.0.0.1:8081/``` dans n'importe quel navigateur et observez le navigateur afficher “Hello World”.

Félicitations, vous avez votre premier serveur HTTP opérationnel qui répond à toutes les demandes HTTP sur le port 8081.