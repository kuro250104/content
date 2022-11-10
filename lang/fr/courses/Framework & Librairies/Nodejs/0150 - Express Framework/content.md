## Aperçu Express

Express est un cadre d'application web Node.js minimal et flexible qui fournit un ensemble robuste de fonctionnalités pour développer des applications web et mobiles. Il facilite le développement rapide d'applications Web basées sur Node. Voici quelques-unes des principales caractéristiques du cadre Express :

- Permet de configurer des intergiciels pour répondre aux requêtes HTTP.
- Définit une table de routage qui est utilisée pour effectuer différentes actions basées sur la méthode HTTP et l'URL.
- Permet de rendre dynamiquement des pages HTML en fonction des arguments passés aux modèles.

## Installation de Express

Tout d'abord, installez globalement le framework Express à l'aide de NPM afin de pouvoir l'utiliser pour créer une application web à l'aide du terminal node.

```bash
$ npm install express --save
```

La commande ci-dessus enregistre l'installation localement dans le répertoire node_modules et crée un répertoire express à l'intérieur de node_modules. Vous devez installer les modules importants suivants en même temps que Express :

- **body-parser** - Il s'agit d'un middleware node.js pour traiter les données de formulaire codées JSON, Raw, Text et URL.
- **cookie-parser** - Analyse l'en-tête de cookie et remplit req.cookies avec un objet dont la clé est le nom du cookie.
- **multer** - Il s'agit d'un intergiciel node.js permettant de traiter les données de formulaire multipart/form-data.

```bash
$ npm install body-parser --save
$ npm install cookie-parser --save
$ npm install multer --save
```

## Exemple de Hello World

Voici une application Express très basique qui démarre un serveur et écoute la connexion sur le port 8081. Cette application répond avec Hello World! pour les requêtes vers la page d'accueil. Pour tout autre chemin, elle répondra par un 404 Not Found.

```js
var express = require('express');
var app = express();

app.get('/', function (req, res) {
    res.send('Hello World');
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port
    
    console.log("Example app listening at http://%s:%s", host, port)
})
```

Enregistrez le code ci-dessus dans un fichier nommé server.js et exécutez-le avec la commande suivante.

```bash
$ node server.js
```

Vous verrez la sortie suivante :

```bash
Example app listening at http://0.0.0.0:8081
```

Ouvrez ```http://127.0.0.1:8081/``` dans n'importe quel navigateur pour voir le résultat.

## Demande et réponse

L'application Express utilise une fonction de rappel dont les paramètres sont des objets de demande et de réponse.

```js
app.get('/', function (req, res) {
    // --
})
```

- **Request Object** - L'objet request représente la requête HTTP et possède des propriétés pour la chaîne de requête, les paramètres, le corps, les en-têtes HTTP, etc.
- **Objet Response** - L'objet response représente la réponse HTTP qu'une application Express envoie lorsqu'elle reçoit une requête HTTP.

Vous pouvez imprimer les objets req et res qui fournissent de nombreuses informations relatives à la demande et à la réponse HTTP, notamment les cookies, les sessions, l'URL, etc.

## Routage de base

Nous avons vu une application de base qui sert une requête HTTP pour la page d'accueil. Le routage consiste à déterminer comment une application répond à une demande du client vers un point de terminaison particulier, qui est une URI (ou un chemin) et une méthode de demande HTTP spécifique (GET, POST, etc.).

Nous allons étendre notre programme Hello World pour traiter d'autres types de requêtes HTTP.

```js
var express = require('express');
var app = express();

// This responds with "Hello World" on the homepage
app.get('/', function (req, res) {
    console.log("Got a GET request for the homepage");
    res.send('Hello GET');
})

// This responds a POST request for the homepage
app.post('/', function (req, res) {
    console.log("Got a POST request for the homepage");
    res.send('Hello POST');
})

// This responds a DELETE request for the /del_user page.
app.delete('/del_user', function (req, res) {
    console.log("Got a DELETE request for /del_user");
    res.send('Hello DELETE');
})

// This responds a GET request for the /list_user page.
app.get('/list_user', function (req, res) {
    console.log("Got a GET request for /list_user");
    res.send('Page Listing');
})

// This responds a GET request for abcd, abxcd, ab123cd, and so on
app.get('/ab*cd', function(req, res) {   
    console.log("Got a GET request for /ab*cd");
    res.send('Page Pattern Match');
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port
    
    console.log("Example app listening at http://%s:%s", host, port)
})
```

Enregistrez le code ci-dessus dans un fichier nommé server.js et exécutez-le avec la commande suivante.

```bash
$ node server.js
```

Vous verrez la sortie suivante :

```bash
Example app listening at http://0.0.0.0:8081
```

Vous pouvez maintenant essayer différentes requêtes sur ```http://127.0.0.1:8081``` pour voir le résultat généré par server.js. Voici quelques URL que vous pouvez tester : 
- ```http://127.0.0.1:8081/list_user```
- ```http://127.0.0.1:8081/abcd```
- ```http://127.0.0.1:8081/abcdefg```

## Servir des fichiers statiques

Express fournit un middleware intégré express.static pour servir les fichiers statiques, tels que les images, CSS, JavaScript, etc.

Il vous suffit de passer le nom du répertoire dans lequel vous conservez vos ressources statiques au middleware express.static pour commencer à servir les fichiers directement. Par exemple, si vous conservez vos images, vos fichiers CSS et JavaScript dans un répertoire nommé public, vous pouvez procéder comme suit :

```js
app.use(express.static('public'));
```

Nous garderons quelques images dans le sous-répertoire public/images comme suit :

```bash
node_modules
server.js
public/
public/images
public/images/logo.png
```

Modifions l'application "Hello Word" pour ajouter la fonctionnalité de gestion des fichiers statiques.

```js
var express = require('express');
var app = express();

app.use(express.static('public'));

app.get('/', function (req, res) {
    res.send('Hello World');
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port

    console.log("Example app listening at http://%s:%s", host, port)
})
```

Enregistrez le code ci-dessus dans un fichier nommé server.js et exécutez-le avec la commande suivante.

```bash
$ node server.js
```

Ouvrez maintenant ```http://127.0.0.1:8081/images/logo.png``` dans n'importe quel navigateur et observez le résultat.

## Méthode GET

Voici un exemple simple qui transmet deux valeurs en utilisant la méthode HTML FORM GET. Nous allons utiliser le routeur process_get dans server.js pour gérer cette entrée.

```html
<html>
    <body>
        
        <form action = "http://127.0.0.1:8081/process_get" method = "GET">
            First Name: <input type = "text" name = "first_name">  <br>
            Last Name: <input type = "text" name = "last_name">
            <input type = "submit" value = "Submit">
        </form>
        
    </body>
</html>
```

Enregistrons le code ci-dessus dans index.htm et modifions server.js pour gérer les requêtes de la page d'accueil ainsi que les entrées envoyées par le formulaire HTML.

```js
var express = require('express');
var app = express();

app.use(express.static('public'));
app.get('/index.htm', function (req, res) {
    res.sendFile( __dirname + "/" + "index.htm" );
})

app.get('/process_get', function (req, res) {
    // Prepare output in JSON format
    response = {
        first_name:req.query.first_name,
        last_name:req.query.last_name
    };
    console.log(response);
    res.end(JSON.stringify(response));
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port
    
    console.log("Example app listening at http://%s:%s", host, port)
})
```

En accédant au document HTML à l'aide de ```http://127.0.0.1:8081/index.htm```, Vous devriez voir apparaître le formulaire correspondant au code HTML présenté ci-dessus.

Maintenant, vous pouvez entrer le prénom et le nom de famille, puis cliquer sur le bouton "Envoyer" pour voir le résultat :

```bash
{"first_name":"John","last_name":"Paul"}
```

## Méthode POST

Voici un exemple simple qui transmet deux valeurs en utilisant la méthode HTML FORM POST. Nous allons utiliser le routeur process_get dans server.js pour gérer cette entrée.

```html
<html>
    <body>
        <form action = "http://127.0.0.1:8081/process_post" method = "POST">
            First Name: <input type = "text" name = "first_name"> <br>
            Last Name: <input type = "text" name = "last_name">
            <input type = "submit" value = "Submit">
        </form>
    </body>
</html>
```

Enregistrons le code ci-dessus dans index.htm et modifions server.js pour gérer les requêtes de la page d'accueil ainsi que les entrées envoyées par le formulaire HTML.

```js
var express = require('express');
var app = express();
var bodyParser = require('body-parser');

// Create application/x-www-form-urlencoded parser
var urlencodedParser = bodyParser.urlencoded({ extended: false })

app.use(express.static('public'));
app.get('/index.htm', function (req, res) {
    res.sendFile( __dirname + "/" + "index.htm" );
})

app.post('/process_post', urlencodedParser, function (req, res) {
    // Prepare output in JSON format
    response = {
        first_name:req.body.first_name,
        last_name:req.body.last_name
    };
    console.log(response);
    res.end(JSON.stringify(response));
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port
    console.log("Example app listening at http://%s:%s", host, port)
})
```

En accédant au document HTML à l'aide de http://127.0.0.1:8081/index.htm, le formulaire correspondant au formulaire HTML ci-dessus devrait apparaître.

Maintenant, vous pouvez entrer le prénom et le nom, puis cliquer sur le bouton "Envoyer" pour voir le résultat suivant :

```bash
{"first_name":"John","last_name":"Paul"}
```

## Téléchargement de fichiers

Le code HTML suivant crée un formulaire de téléchargement de fichiers. L'attribut method de ce formulaire est réglé sur POST et l'attribut enctype est réglé sur multipart/form-data.

```html
<html>
    <head>
        <title>File Uploading Form</title>
    </head>

    <body>
        <h3>File Upload:</h3>
        Select a file to upload: <br />
        
        <form action = "http://127.0.0.1:8081/file_upload" method = "POST" 
            enctype = "multipart/form-data">
            <input type="file" name="file" size="50" />
            <br />
            <input type = "submit" value = "Upload File" />
        </form>
        
    </body>
</html>
```

Enregistrons le code ci-dessus dans index.htm et modifions server.js pour gérer les requêtes de la page d'accueil ainsi que le téléchargement de fichiers.

```js
var express = require('express');
var app = express();
var fs = require("fs");

var bodyParser = require('body-parser');
var multer  = require('multer');

app.use(express.static('public'));
app.use(bodyParser.urlencoded({ extended: false }));
app.use(multer({ dest: '/tmp/'}));

app.get('/index.htm', function (req, res) {
    res.sendFile( __dirname + "/" + "index.htm" );
})

app.post('/file_upload', function (req, res) {
    console.log(req.files.file.name);
    console.log(req.files.file.path);
    console.log(req.files.file.type);
    var file = __dirname + "/" + req.files.file.name;
    
    fs.readFile( req.files.file.path, function (err, data) {
        fs.writeFile(file, data, function (err) {
            if( err ) {
                console.log( err );
                } else {
                response = {
                    message:'File uploaded successfully',
                    filename:req.files.file.name
                };
                }
            
            console.log( response );
            res.end( JSON.stringify( response ) );
        });
    });
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port
    
    console.log("Example app listening at http://%s:%s", host, port)
})
```

En accédant au document HTML à l'aide de http://127.0.0.1:8081/index.htm, le formulaire correspondant au formulaire HTML ci-dessus devrait apparaître.

## Gestion des cookies

Vous pouvez envoyer des cookies à un serveur Node.js qui peut les gérer en utilisant l'option middleware suivante. Voici un exemple simple pour imprimer tous les cookies envoyés par le client.

```js
var express      = require('express')
var cookieParser = require('cookie-parser')

var app = express()
app.use(cookieParser())

app.get('/', function(req, res) {
    console.log("Cookies: ", req.cookies)
})
app.listen(8081)
```

__Remarque__ : Pour en savoir plus sur Express, vous pouvez vous réferrer au cours plus complet présent dans la catégorie Express !