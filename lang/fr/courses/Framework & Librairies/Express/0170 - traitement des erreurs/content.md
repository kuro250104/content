La gestion des erreurs dans Express est effectuée à l'aide d'un intergiciel. Mais cet intergiciel a des propriétés spéciales. Les intergiciels de gestion des erreurs sont définis de la même manière que les autres fonctions d'intergiciel, sauf que les fonctions de gestion des erreurs DOIVENT avoir quatre arguments au lieu de trois - err, req, res, next. Par exemple, pour envoyer une réponse à n'importe quelle erreur, nous pouvons utiliser -

```js
app.use(function(err, req, res, next) {
    console.error(err.stack);
    res.status(500).send('Something broke!');
});
```

Jusqu'à présent, nous gérions les erreurs dans les routes elles-mêmes. Le middleware de gestion des erreurs nous permet de séparer notre logique d'erreur et d'envoyer des réponses en conséquence. La méthode next() dont nous avons parlé dans le middleware nous amène au prochain middleware/gestionnaire de route.

Pour la gestion des erreurs, nous avons la fonction next(err). Un appel à cette fonction permet de sauter tous les intergiciels et de nous faire correspondre au prochain gestionnaire d'erreurs pour cette route. Comprenons cela par un exemple.

```js
var express = require('express');
var app = express();

app.get('/', function(req, res){
    //Create an error and pass it to the next function
    var err = new Error("Something went wrong");
    next(err);
});

/*
 * other route handlers and middleware here
 * ....
 */

//An error handling middleware
app.use(function(err, req, res, next) {
    res.status(500);
    res.send("Oops, something went wrong.")
});

app.listen(3000);
```

Cet intergiciel de gestion des erreurs peut être placé stratégiquement après les routes ou les conditions de contenu pour détecter les types d'erreur et répondre aux clients en conséquence. Le programme ci-dessus affichera la sortie "Oops, something went wrong.".