Les cadres Web fournissent des ressources telles que des pages HTML, des scripts, des images, etc. à différents endroits.

La fonction suivante est utilisée pour définir des itinéraires dans une application Express.

## app.method(path, handler)

Cette MÉTHODE peut être appliquée à n'importe lequel des verbes HTTP - get, set, put, delete. Il existe également une autre méthode, qui s'exécute indépendamment du type de demande.

Le chemin est la route sur laquelle la requête sera exécutée.

Le gestionnaire est une fonction de rappel qui s'exécute lorsqu'un type de demande correspondant est trouvé sur la route concernée. Par exemple,

```js
var express = require('express');
var app = express();

app.get('/hello', function(req, res){
    res.send("Hello World!");
});

app.listen(3000);
```

Si nous exécutons notre application et nous rendons à localhost:3000/hello, le serveur reçoit une demande d'accès à la route "/hello", notre application Express exécute la fonction de rappel attachée à cette route et envoie "Hello World !

On peut aussi avoir plusieurs méthodes différentes sur une même route. Par exemple,

```js
var express = require('express');
var app = express();

app.get('/hello', function(req, res){
    res.send("Hello World!");
});

app.post('/hello', function(req, res){
    res.send("You just called the post method at '/hello'!\n");
});

app.listen(3000);
```

Pour tester cette requête, ouvrez votre terminal et utilisez cURL pour exécuter la requête suivante : -.

```bash
curl -X POST "http://localhost:3000/hello"
```

Une méthode spéciale, all, est fournie par Express pour traiter tous les types de méthodes http sur une route particulière en utilisant la même fonction. Pour utiliser cette méthode, essayez ce qui suit.

```js
app.all('/test', function(req, res){
    res.send("HTTP method doesn't have any effect on this route!");
});
```

Cette méthode est généralement utilisée pour définir les intergiciels, dont nous parlerons dans le chapitre sur les intergiciels.

## Routers

Définir des routes comme ci-dessus est très fastidieux à maintenir. Pour séparer les routes de notre fichier index.js principal, nous allons utiliser Express.Router. Créez un nouveau fichier appelé things.js et tapez ce qui suit dans ce fichier.

```js
var express = require('express');
var router = express.Router();

router.get('/', function(req, res){
    res.send('GET route on things.');
});
router.post('/', function(req, res){
    res.send('POST route on things.');
});

//export this router to use in our index.js
module.exports = router;
```

Maintenant pour utiliser ce routeur dans notre index.js, tapez ce qui suit avant l'appel de la fonction app.listen.

```js
var express = require('Express');
var app = express();

var things = require('./things.js');

//both index.js and things.js should be in same directory
app.use('/things', things);

app.listen(3000);
```

L'appel à la fonction app.use sur la route '/things' attache le routeur things à cette route. Maintenant, toutes les demandes que notre application reçoit sur '/things', seront traitées par notre routeur things.js. La route '/' dans things.js est en fait un sous-route de '/things'.

Les routeurs sont très utiles pour séparer les préoccupations et garder ensemble les parties pertinentes de notre code. Ils aident à construire un code facile à maintenir. Vous devez définir vos routes relatives à une entité dans un seul fichier et l'inclure en utilisant la méthode ci-dessus dans votre fichier index.js.