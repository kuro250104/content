## Qu'est-ce que l'architecture REST ?

REST est l'abréviation de REpresentational State Transfer. REST est une architecture basée sur les normes web et utilise le protocole HTTP. Elle s'articule autour d'une ressource où chaque composant est une ressource et où l'on accède à une ressource par une interface commune utilisant des méthodes standard HTTP. REST a été présenté pour la première fois par Roy Fielding en 2000.

Un serveur REST fournit simplement un accès aux ressources et le client REST accède aux ressources et les modifie en utilisant le protocole HTTP. Ici, chaque ressource est identifiée par des URI/identifiants globaux. REST utilise différentes représentations pour représenter une ressource comme le texte, JSON, XML, mais JSON est le plus populaire.

## Méthodes HTTP

Les quatre méthodes HTTP suivantes sont couramment utilisées dans l'architecture REST.

- **GET** - Cette méthode est utilisée pour fournir un accès en lecture seule à une ressource.
- **PUT** - Cette méthode est utilisée pour créer une nouvelle ressource.
- **DELETE** - Cette méthode est utilisée pour supprimer une ressource.
- **POST** - Cette méthode est utilisée pour mettre à jour une ressource existante ou créer une nouvelle ressource.

## Services Web RESTful

Un service web est un ensemble de protocoles et de normes ouverts utilisés pour échanger des données entre des applications ou des systèmes. Les applications logicielles écrites dans divers langages de programmation et fonctionnant sur diverses plates-formes peuvent utiliser les services web pour échanger des données sur des réseaux informatiques tels que l'internet, de manière similaire à la communication interprocessus sur un seul ordinateur. Cette interopérabilité (par exemple, la communication entre des applications Java et Python, ou Windows et Linux) est due à l'utilisation de normes ouvertes.

Les services web basés sur l'architecture REST sont connus sous le nom de services web RESTful. Ces services web utilisent des méthodes HTTP pour mettre en œuvre le concept de l'architecture REST. Un service web RESTful définit généralement un URI (Uniform Resource Identifier), un service qui fournit une représentation des ressources telle que JSON et un ensemble de méthodes HTTP.

## Création de RESTful pour une bibliothèque

Considérons que nous avons une base de données d'utilisateurs basée sur JSON ayant les utilisateurs suivants dans un fichier users.json :

```json
{
    "user1" : {
        "name" : "mahesh",
        "password" : "password1",
        "profession" : "teacher",
        "id": 1
    },
    
    "user2" : {
        "name" : "suresh",
        "password" : "password2",
        "profession" : "librarian",
        "id": 2
    },
    
    "user3" : {
        "name" : "ramesh",
        "password" : "password3",
        "profession" : "clerk",
        "id": 3
    }
}
```

Sur la base de ces informations, nous allons fournir les API RESTful suivantes :

| **URI** | **Méthode HTTP** | **POST body** | **Résultat** |
| --- | --- | --- | --- |
| listUsers | GET | Vide | Affiche la liste des utilisateurs |
| addUser | POST | String JSON | Ajoute les détails d’un utilisateur |
| deleteUser | DELETE | String JSON | Supprime un utilisateur existant |
| :id | GET | Vide | Affiche le détail d’un utilisateur |

Je garde la plupart de la partie de tous les exemples sous forme de codage dur en supposant que vous savez déjà comment passer des valeurs du front-end en utilisant Ajax ou des données de formulaire simples et comment les traiter en utilisant l'objet Request express.

## Liste des utilisateurs

Mettons en œuvre notre première API RESTful listUsers à l'aide du code suivant dans un fichier server.js :

```js
var express = require('express');
var app = express();
var fs = require("fs");

app.get('/listUsers', function (req, res) {
    fs.readFile( __dirname + "/" + "users.json", 'utf8', function (err, data) {
        console.log( data );
        res.end( data );
    });
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port
    console.log("Example app listening at http://%s:%s", host, port)
})
```

Essayez maintenant d'accéder à l'API définie en utilisant l'URL : http://127.0.0.1:8081/listUsers et la méthode HTTP : GET sur la machine locale en utilisant n'importe quel client REST. Cela devrait produire le résultat suivant :

Vous pouvez changer l'adresse IP donnée lorsque vous mettrez la solution dans un environnement de production.

```json
{
    "user1" : {
        "name" : "mahesh",
        "password" : "password1",
        "profession" : "teacher",
        "id": 1
    },
    
    "user2" : {
        "name" : "suresh",
        "password" : "password2",
        "profession" : "librarian",
        "id": 2
    },
    
    "user3" : {
        "name" : "ramesh",
        "password" : "password3",
        "profession" : "clerk",
        "id": 3
    }
}
```

## Ajouter un utilisateur

L'API suivante vous montrera comment ajouter un nouvel utilisateur dans la liste. Voici le détail du nouvel utilisateur :

```js
user = {
    "user4" : {
        "name" : "mohit",
        "password" : "password4",
        "profession" : "teacher",
        "id": 4
    }
}
```

Vous pouvez accepter la même entrée sous forme de JSON en utilisant l'appel Ajax, mais pour des raisons pédagogiques, nous le codons en dur ici. Voici l'API addUser pour créer un nouvel utilisateur dans la base de données :

```js
var express = require('express');
var app = express();
var fs = require("fs");

var user = {
    "user4" : {
        "name" : "mohit",
        "password" : "password4",
        "profession" : "teacher",
        "id": 4
    }
}

app.post('/addUser', function (req, res) {
    // First read existing users.
    fs.readFile( __dirname + "/" + "users.json", 'utf8', function (err, data) {
            data = JSON.parse( data );
            data["user4"] = user["user4"];
            console.log( data );
            res.end( JSON.stringify(data));
    });
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port
    console.log("Example app listening at http://%s:%s", host, port)
})
```

Essayez maintenant d'accéder à l'API définie en utilisant l'URL : http://127.0.0.1:8081/addUser et la méthode HTTP : POST sur la machine locale en utilisant n'importe quel client REST. Cela devrait produire le résultat suivant :

```json
{
    "user1":{"name":"mahesh","password":"password1","profession":"teacher","id":1},
    "user2":{"name":"suresh","password":"password2","profession":"librarian","id":2},
    "user3":{"name":"ramesh","password":"password3","profession":"clerk","id":3},
    "user4":{"name":"mohit","password":"password4","profession":"teacher","id":4}
}
```

## Afficher les détails

Maintenant nous allons implémenter une API qui sera appelée en utilisant l'ID de l'utilisateur et qui affichera les détails de l'utilisateur correspondant.

```js
var express = require('express');
var app = express();
var fs = require("fs");

app.get('/:id', function (req, res) {
    // First read existing users.
    fs.readFile( __dirname + "/" + "users.json", 'utf8', function (err, data) {
        var users = JSON.parse( data );
        var user = users["user" + req.params.id] 
        console.log( user );
        res.end( JSON.stringify(user));
    });
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port
    console.log("Example app listening at http://%s:%s", host, port)
})
```

Essayez maintenant d'accéder à l'API définie en utilisant l'URL : http://127.0.0.1:8081/2 et la méthode HTTP : GET sur la machine locale en utilisant n'importe quel client REST. Cela devrait produire le résultat suivant :

```json
{"name":"suresh","password":"password2","profession":"librarian","id":2}
```

## Supprimer l'utilisateur

Cette API est très similaire à l'API addUser, dans laquelle nous recevons des données d'entrée via req.body, puis, en fonction de l'ID de l'utilisateur, nous supprimons cet utilisateur de la base de données. Pour garder notre programme simple, nous supposons que nous allons supprimer l'utilisateur avec l'ID 2.

```js
var express = require('express');
var app = express();
var fs = require("fs");

var id = 2;

app.delete('/deleteUser', function (req, res) {
    // First read existing users.
    fs.readFile( __dirname + "/" + "users.json", 'utf8', function (err, data) {
        data = JSON.parse( data );
        delete data["user" + 2];
        
        console.log( data );
        res.end( JSON.stringify(data));
    });
})

var server = app.listen(8081, function () {
    var host = server.address().address
    var port = server.address().port
    console.log("Example app listening at http://%s:%s", host, port)
})
```

Essayez maintenant d'accéder à l'API définie en utilisant l'URL : http://127.0.0.1:8081/deleteUser et la méthode HTTP : DELETE sur la machine locale en utilisant n'importe quel client REST. Cela devrait produire le résultat suivant :

```json
{
    "user1":{"name":"mahesh","password":"password1","profession":"teacher","id":1},
    "user3":{"name":"ramesh","password":"password3","profession":"clerk","id":3}
}
```