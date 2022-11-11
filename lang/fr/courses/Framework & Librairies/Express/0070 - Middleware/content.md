Les fonctions middleware sont des fonctions qui ont accès à l'objet de requête (req), à l'objet de réponse (res) et à la fonction middleware suivante dans le cycle requête-réponse de l'application. Ces fonctions sont utilisées pour modifier les objets req et res pour des tâches telles que l'analyse du corps des requêtes, l'ajout d'en-têtes de réponse, etc.

Voici un exemple simple d'une fonction d'intergiciel en action.

```js
var express = require('express');
var app = express();

//Simple request time logger
app.use(function(req, res, next){
    console.log("A new request received at " + Date.now());

    //This function call is very important. It tells that more processing is
    //required for the current request and is in the next middleware
    function route handler.
    next();
});

app.listen(3000);
```

Le middleware ci-dessus est appelé pour chaque requête sur le serveur. Ainsi, après chaque requête, nous obtiendrons le message suivant dans la console -

```bash
A new request received at 1467267512545
```

Pour le restreindre à une route spécifique (et à toutes ses sous-routes), fournissez cette route comme premier argument de ```app.use()```. Par exemple,

```js
var express = require('express');
var app = express();

//Middleware function to log request protocol
app.use('/things', function(req, res, next){
    console.log("A request for things received at " + Date.now());
    next();
});

// Route handler that sends the response
app.get('/things', function(req, res){
    res.send('Things');
});

app.listen(3000);
```

Maintenant, chaque fois que vous demandez un sous-routage de '/things', alors seulement il enregistrera l'heure.

## Order of Middleware Calls

L'une des choses les plus importantes concernant les intergiciels dans Express est l'ordre dans lequel ils sont écrits/inclus dans votre fichier ; l'ordre dans lequel ils sont exécutés, étant donné que la correspondance des routes doit également être prise en compte.

Par exemple, dans l'extrait de code suivant, la première fonction s'exécute en premier, puis le gestionnaire de route et enfin la fonction de fin. Cet exemple résume la manière d'utiliser un intergiciel avant et après le gestionnaire de route, ainsi que la manière dont un gestionnaire de route peut être utilisé comme un intergiciel.

```js
var express = require('express');
var app = express();

//First middleware before response is sent
app.use(function(req, res, next){
    console.log("Start");
    next();
});

//Route handler
app.get('/', function(req, res, next){
    res.send("Middle");
    next();
});

app.use('/', function(req, res){
    console.log('End');
});

app.listen(3000);
```

Lorsque nous visitons '/' après avoir exécuté ce code, nous recevons la réponse comme Middle et sur notre console -

```bash
Start
End
```

Maintenant que nous avons vu comment créer notre propre intergiciel, examinons quelques-uns des intergiciels les plus couramment utilisés par la communauté.

## Middleware tiers

Une liste de middleware tiers pour Express est disponible ici. Voici quelques-uns des intergiciels les plus couramment utilisés ; nous apprendrons également à les utiliser et à les monter.

### body-parser

Il est utilisé pour analyser le corps des requêtes auxquelles sont attachées des charges utiles. Pour monter body parser, nous devons l'installer en utilisant npm install --save body-parser et pour le monter, inclure les lignes suivantes dans votre index.js -

```js
var bodyParser = require('body-parser');

//To parse URL encoded data
app.use(bodyParser.urlencoded({ extended: false }))

//To parse json data
app.use(bodyParser.json())
```

Pour voir toutes les options disponibles pour body-parser, visitez sa page github.

### cookie-parser

Il analyse l'en-tête de cookie et remplit req.cookies avec un objet dont la clé est le nom des cookies. Pour monter le cookie parser, nous devons l'installer en utilisant ```npm install --save cookie-parser``` et pour le monter, inclure les lignes suivantes dans votre index.js -

```js
var cookieParser = require('cookie-parser');
app.use(cookieParser())
```

### express-session

Elle crée un intergiciel de session avec les options données. Nous discuterons de son utilisation dans la section Sessions.
Nous avons beaucoup d'autres intergiciels tiers dans ExpressJS. Cependant, nous n'avons abordé ici que quelques uns des plus importants.