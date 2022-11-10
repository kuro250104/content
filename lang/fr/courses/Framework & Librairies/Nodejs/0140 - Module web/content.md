## Qu'est-ce qu'un serveur Web ?

Un serveur Web est une application logicielle qui traite les demandes HTTP envoyées par le client HTTP, comme les navigateurs Web, et renvoie des pages Web en réponse aux clients. Les serveurs Web fournissent généralement des documents html accompagnés d'images, de feuilles de style et de scripts.

La plupart des serveurs Web prennent en charge les scripts côté serveur, en utilisant des langages de script ou en redirigeant la tâche vers un serveur d'application qui récupère les données d'une base de données et exécute une logique complexe, puis envoie un résultat au client HTTP par le biais du serveur Web.

Le serveur web Apache est l'un des serveurs web les plus couramment utilisés. Il s'agit d'un projet open source.

## Architecture des applications Web

Une application Web est généralement divisée en quatre couches :

- **Client** - Cette couche est constituée de navigateurs Web, de navigateurs mobiles ou d'applications qui peuvent faire des demandes HTTP au serveur Web.
- **Serveur** - Cette couche contient le serveur Web qui peut intercepter les demandes faites par les clients et leur transmettre la réponse.
- **Business** - Cette couche contient le serveur d'application qui est utilisé par le serveur Web pour effectuer le traitement requis. Cette couche interagit avec la couche de données via la base de données ou certains programmes externes.
- **Données** - Cette couche contient les bases de données ou toute autre source de données.

## Création d'un serveur Web à l'aide de Node

Node.js fournit un module http qui peut être utilisé pour créer un client HTTP d'un serveur. Voici la structure minimale d'un serveur HTTP qui écoute sur le port 8081.

![Structure minimale d'un serveur http](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Nodejs/0140%20-%20Module%20web/images/image1.jpg)

Créez un fichier js nommé server.js. :

```js
var http = require('http');
var fs = require('fs');
var url = require('url');

// Create a server
http.createServer( function (request, response) {  
    // Parse the request containing file name
    var pathname = url.parse(request.url).pathname;

    // Print the name of the file for which request is made.
    console.log("Request for " + pathname + " received.");

    // Read the requested file content from file system
    fs.readFile(pathname.substr(1), function (err, data) {
        if (err) {
            console.log(err);

            // HTTP Status: 404 : NOT FOUND
            // Content Type: text/plain
            response.writeHead(404, {'Content-Type': 'text/html'});
        } else {	
            //Page found	  
            // HTTP Status: 200 : OK
            // Content Type: text/plain
            response.writeHead(200, {'Content-Type': 'text/html'});	

            // Write the content of the file to response body
            response.write(data.toString());		
        }

        // Send the response body 
        response.end();
    });   
}).listen(8081);

// Console will print the message
console.log('Server running at http://127.0.0.1:8081/');
```

Ensuite, créons le fichier html suivant nommé index.htm dans le même répertoire que celui où vous avez créé server.js :

```html
<html>
    <head>
        <title>Sample Page</title>
    </head>
    
    <body>
        Hello World!
    </body>
</html>
```

Maintenant, exécutons le server.js pour voir le résultat :

```bash
$ node server.js
```

Vérifier la sortie.

```bash
Server running at http://127.0.0.1:8081/
```

## Faire une demande au serveur Node.js

Ouvrez http://127.0.0.1:8081/index.htm dans n'importe quel navigateur pour voir le résultat.

Vérifiez la sortie au niveau du serveur.

```bash
Server running at http://127.0.0.1:8081/
Request for /index.htm received.
```

## Création d'un client Web à l'aide de Node

Un client web peut être créé en utilisant le module http. Vérifions l'exemple suivant.

Créez un fichier js nommé client.js. :

```js
var http = require('http');

// Options to be used by request 
var options = {
    host: 'localhost',
    port: '8081',
    path: '/index.htm'  
};

// Callback function is used to deal with response
var callback = function(response) {
    // Continuously update stream with data
    var body = '';
    response.on('data', function(data) {
        body += data;
    });
    
    response.on('end', function() {
        // Data received completely.
        console.log(body);
    });
}
// Make a request to the server
var req = http.request(options, callback);
req.end();
```

Maintenant, exécutez le client.js à partir d'un terminal de commande différent de celui de server.js pour voir le résultat :

```bash
$ node client.js
```

Vérifier la sortie.

```html
<html>
    <head>
        <title>Sample Page</title>
    </head>
    
    <body>
        Hello World!
    </body>
</html>
```

Vérifiez la sortie au niveau du serveur.

```bash
Server running at http://127.0.0.1:8081/
Request for /index.htm received.
```