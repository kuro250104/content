Une API est toujours nécessaire pour créer des applications mobiles, des applications à page unique, utiliser des appels AJAX et fournir des données aux clients. Un style architectural populaire de la façon de structurer et de nommer ces API et les points de terminaison est appelé REST (Representational Transfer State). Le protocole HTTP 1.1 a été conçu en tenant compte des principes REST. REST a été introduit par Roy Fielding en 2000 dans son article Fielding Dissertations.

Les URI et les méthodes RESTful nous fournissent presque toutes les informations dont nous avons besoin pour traiter une demande. Le tableau ci-dessous résume la manière dont les différents verbes doivent être utilisés et dont les URI doivent être nommés. Nous allons créer une API de films à la fin ; voyons maintenant comment elle sera structurée.

| **Méthode** | **URI** | **Détails** | **Fonction** |
| --- | --- | --- | --- |
| GET | /movies | Safe, cachable | Obtient la liste de tous les films et leurs détails. |
| GET | /movies/1234 | Safe, cachable | Obtient les détails de Movie id 1234 |
| POST | /movies | N/A | Crée un nouveau film avec les détails fournis. La réponse contient l'URI de cette ressource nouvellement créée. |
| PUT | /movies/1234 | Idempotent | Modifie l'id de film 1234 (en crée un s'il n'existe pas déjà). La réponse contient l'URI de cette ressource nouvellement créée. |
| DELETE | /movies/1234 | Idempotent | L'identifiant de film 1234 doit être supprimé, s'il existe. La réponse doit contenir le statut de la demande. |
| DELETE or PUT | /movies | Invalid | Devrait être invalide. DELETE et PUT devraient préciser sur quelle ressource ils travaillent. |

Créons maintenant cette API dans Express. Nous utiliserons JSON comme format de données de transport car il est facile à utiliser en JavaScript et présente d'autres avantages. Remplacez votre fichier index.js par le fichier movies.js comme dans le programme suivant.

index.js

```js
var express = require('express');
var bodyParser = require('body-parser');
var multer = require('multer');
var upload = multer();

var app = express();

app.use(cookieParser());
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));
app.use(upload.array());

//Require the Router we defined in movies.js
var movies = require('./movies.js');

//Use the Router on the sub route /movies
app.use('/movies', movies);

app.listen(3000);
```

Maintenant que nous avons mis en place notre application, concentrons-nous sur la création de l'API.

Commencez par configurer le fichier movies.js. Nous n'utilisons pas de base de données pour stocker les films, mais nous les stockons en mémoire ; ainsi, chaque fois que le serveur redémarre, les films que nous avons ajoutés disparaissent. Ceci peut facilement être imité en utilisant une base de données ou un fichier (en utilisant le module fs de node).

Une fois que vous avez importé Express, créez un routeur et exportez-le à l'aide de module.exports -.

```js
var express = require('express');
var router = express.Router();
var movies = [
    {id: 101, name: "Fight Club", year: 1999, rating: 8.1},
    {id: 102, name: "Inception", year: 2010, rating: 8.7},
    {id: 103, name: "The Dark Knight", year: 2008, rating: 9},
    {id: 104, name: "12 Angry Men", year: 1957, rating: 8.9}
];

//Routes will go here
module.exports = router;
```

## GET routes

Définissons la route GET pour obtenir tous les films -.

```js
router.get('/', function(req, res){
    res.json(movies);
});
```

Pour vérifier si tout fonctionne bien, exécutez votre application, puis ouvrez votre terminal et entrez -

```bash
curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X GET 
localhost:3000/movies
```

La réponse suivante s'affiche -

```json
[{"id":101,"name":"Fight Club","year":1999,"rating":8.1},
{"id":102,"name":"Inception","year":2010,"rating":8.7},
{"id":103,"name":"The Dark Knight","year":2008,"rating":9},
{"id":104,"name":"12 Angry Men","year":1957,"rating":8.9}]
```

Nous avons une route pour obtenir tous les films. Créons maintenant une route pour obtenir un film spécifique par son identifiant.

```js
router.get('/:id([0-9]{3,})', function(req, res){
    var currMovie = movies.filter(function(movie){
        if(movie.id == req.params.id){
            return true;
        }
    });
    if(currMovie.length == 1){
        res.json(currMovie[0])
    } else {
        res.status(404);//Set status to 404 as movie was not found
        res.json({message: "Not Found"});
    }
});
```

Cela nous permettra d'obtenir les films en fonction de l'identifiant que nous avons fourni. Pour vérifier la sortie, utilisez la commande suivante dans votre terminal -

```bash
curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X GET 
localhost:3000/movies/101
```

Vous obtiendrez la réponse suivante -

```json
{"id":101,"name":"Fight Club","year":1999,"rating":8.1}
```

Si vous visitez une route non valide, elle produira une erreur cannot GET, tandis que si vous visitez une route valide avec un id qui n'existe pas, elle produira une erreur 404.

Nous en avons terminé avec les routes GET, passons maintenant à la route POST.

## POST route

Utilisez l'itinéraire suivant pour traiter les données POSTed -

```js
router.post('/', function(req, res){
    //Check if all fields are provided and are valid:
    if(!req.body.name ||
        !req.body.year.toString().match(/^[0-9]{4}$/g) ||
        !req.body.rating.toString().match(/^[0-9]\.[0-9]$/g)){
        
        res.status(400);
        res.json({message: "Bad Request"});
    } else {
        var newId = movies[movies.length-1].id+1;
        movies.push({
            id: newId,
            name: req.body.name,
            year: req.body.year,
            rating: req.body.rating
        });
        res.json({message: "New movie created.", location: "/movies/" + newId});
    }
});
```

Cela va créer un nouveau film et le stocker dans la variable movies. Pour vérifier ce parcours, entrez le code suivant dans votre terminal -

```bash
curl -X POST --data "name = Toy%20story&year = 1995&rating = 8.5" http://localhost:3000/movies
```

La réponse suivante s'affiche -

```json
{"message":"New movie created.","location":"/movies/105"}
```

Pour vérifier si cela a été ajouté à l'objet movies, exécutez à nouveau la requête get pour /movies/105. La réponse suivante sera affichée -

```json
{"id":105,"name":"Toy story","year":"1995","rating":"8.5"}
```

Passons à la création des routes PUT et DELETE.

## PUT route

La route PUT est presque la même que la route POST. Nous allons spécifier l'identifiant de l'objet qui sera mis à jour/créé. Créez la route de la manière suivante.

```js
router.put('/:id', function(req, res){
    //Check if all fields are provided and are valid:
    if(!req.body.name ||
        !req.body.year.toString().match(/^[0-9]{4}$/g) ||
        !req.body.rating.toString().match(/^[0-9]\.[0-9]$/g) ||
        !req.params.id.toString().match(/^[0-9]{3,}$/g)){
        
        res.status(400);
        res.json({message: "Bad Request"});
    } else {
        //Gets us the index of movie with given id.
        var updateIndex = movies.map(function(movie){
            return movie.id;
        }).indexOf(parseInt(req.params.id));
        
        if(updateIndex === -1){
            //Movie not found, create new
            movies.push({
                id: req.params.id,
                name: req.body.name,
                year: req.body.year,
                rating: req.body.rating
            });
            res.json({message: "New movie created.", location: "/movies/" + req.params.id});
        } else {
            //Update existing movie
            movies[updateIndex] = {
                id: req.params.id,
                name: req.body.name,
                year: req.body.year,
                rating: req.body.rating
            };
            res.json({message: "Movie id " + req.params.id + " updated.", 
                location: "/movies/" + req.params.id});
        }
    }
});
```

Cette route exécutera la fonction spécifiée dans le tableau ci-dessus. Elle mettra à jour l'objet avec de nouveaux détails s'il existe. S'il n'existe pas, elle créera un nouvel objet. Pour vérifier la route, utilisez la commande curl suivante. Ceci mettra à jour un film existant. Pour créer un nouveau film, il suffit de changer l'id par un id non existant.

```bash
curl -X PUT --data "name = Toy%20story&year = 1995&rating = 8.5" 
http://localhost:3000/movies/101
```

Réponse

```json
{"message":"Movie id 101 updated.","location":"/movies/101"}
```

## DELETE route

Utilisez le code suivant pour créer un itinéraire de suppression. -

```js
router.delete('/:id', function(req, res){
    var removeIndex = movies.map(function(movie){
        return movie.id;
    }).indexOf(req.params.id); //Gets us the index of movie with given id.
    
    if(removeIndex === -1){
        res.json({message: "Not found"});
    } else {
        movies.splice(removeIndex, 1);
        res.send({message: "Movie id " + req.params.id + " removed."});
    }
});
```

Vérifiez la route de la même manière que nous avons vérifié les autres routes. Si la suppression est réussie (par exemple id 105), vous obtiendrez la sortie suivante -

```bash
{message: "Movie id 105 removed."}
```

Enfin, notre fichier movies.js ressemblera à ce qui suit.

```js
var express = require('express');
var router = express.Router();
var movies = [
    {id: 101, name: "Fight Club", year: 1999, rating: 8.1},
    {id: 102, name: "Inception", year: 2010, rating: 8.7},
    {id: 103, name: "The Dark Knight", year: 2008, rating: 9},
    {id: 104, name: "12 Angry Men", year: 1957, rating: 8.9}
];
router.get('/:id([0-9]{3,})', function(req, res){
    var currMovie = movies.filter(function(movie){
        if(movie.id == req.params.id){
            return true;
        }
    });
    
    if(currMovie.length == 1){
        res.json(currMovie[0])
    } else {
        res.status(404);  //Set status to 404 as movie was not found
        res.json({message: "Not Found"});
    }
});
router.post('/', function(req, res){
    //Check if all fields are provided and are valid:
    if(!req.body.name ||
        !req.body.year.toString().match(/^[0-9]{4}$/g) ||
        !req.body.rating.toString().match(/^[0-9]\.[0-9]$/g)){
        res.status(400);
        res.json({message: "Bad Request"});
    } else {
        var newId = movies[movies.length-1].id+1;
        movies.push({
            id: newId,
            name: req.body.name,
            year: req.body.year,
            rating: req.body.rating
        });
        res.json({message: "New movie created.", location: "/movies/" + newId});
    }
});

router.put('/:id', function(req, res) {
    //Check if all fields are provided and are valid:
    if(!req.body.name ||
        !req.body.year.toString().match(/^[0-9]{4}$/g) ||
        !req.body.rating.toString().match(/^[0-9]\.[0-9]$/g) ||
        !req.params.id.toString().match(/^[0-9]{3,}$/g)){
        res.status(400);
        res.json({message: "Bad Request"});
    } else {
        //Gets us the index of movie with given id.
        var updateIndex = movies.map(function(movie){
            return movie.id;
        }).indexOf(parseInt(req.params.id));
        
        if(updateIndex === -1){
            //Movie not found, create new
            movies.push({
                id: req.params.id,
                name: req.body.name,
                year: req.body.year,
                rating: req.body.rating
            });
            res.json({
                message: "New movie created.", location: "/movies/" + req.params.id});
        } else {
            //Update existing movie
            movies[updateIndex] = {
                id: req.params.id,
                name: req.body.name,
                year: req.body.year,
                rating: req.body.rating
            };
            res.json({message: "Movie id " + req.params.id + " updated.",
                location: "/movies/" + req.params.id});
        }
    }
});

router.delete('/:id', function(req, res){
    var removeIndex = movies.map(function(movie){
        return movie.id;
    }).indexOf(req.params.id); //Gets us the index of movie with given id.
    
    if(removeIndex === -1){
        res.json({message: "Not found"});
    } else {
        movies.splice(removeIndex, 1);
        res.send({message: "Movie id " + req.params.id + " removed."});
    }
});
module.exports = router;
```

Notre API REST est ainsi terminée. Vous pouvez maintenant créer des applications beaucoup plus complexes en utilisant ce style architectural simple et Express.