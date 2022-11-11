Nous pouvons maintenant définir des routes, mais celles-ci sont statiques ou fixes. Pour utiliser les routes dynamiques, nous DEVONS fournir différents types de routes. L'utilisation de routes dynamiques nous permet de passer des paramètres et de traiter en fonction de ceux-ci.

Voici un exemple de route dynamique -

```js
var express = require('express');
var app = express();

app.get('/:id', function(req, res){
    res.send('The id you specified is ' + req.params.id);
});
app.listen(3000);
```

Pour tester cela, allez sur ```http://localhost:3000/123```. Le message "The id you specified is 123" devrait apparaître.

Vous pouvez remplacer '123' dans l'URL par n'importe quoi d'autre et le changement se reflétera dans la réponse. Un exemple plus complexe de ce qui précède est -

```js
var express = require('express');
var app = express();

app.get('/things/:name/:id', function(req, res) {
    res.send('id: ' + req.params.id + ' and name: ' + req.params.name);
});
app.listen(3000);
```

Pour tester le code ci-dessus, allez sur ```http://localhost:3000/things/Microlead/12345```. Le message "id: 123 and name:Microlead" devrait apparaître.

Vous pouvez utiliser l'objet req.params pour accéder à tous les paramètres que vous passez dans l'url. Notez que les deux éléments ci-dessus sont des chemins différents. Ils ne se chevaucheront jamais. De même, si vous voulez exécuter du code lorsque vous obtenez '/things', vous devez le définir séparément.

## Routes par Pattern

Vous pouvez également utiliser une expression rationnelle pour restreindre la correspondance des paramètres d'URL. Supposons que vous ayez besoin que l'identifiant soit un nombre long à 5 chiffres. Vous pouvez utiliser la définition de route suivante -

```js
var express = require('express');
var app = express();

app.get('/things/:id([0-9]{5})', function(req, res){
    res.send('id: ' + req.params.id);
});

app.listen(3000);
```

Notez que cela ne correspondra qu'aux demandes ayant un identifiant long de 5 chiffres. Vous pouvez utiliser des regex plus complexes pour faire correspondre/valider vos routes. Si aucune de vos routes ne correspond à la demande, vous obtiendrez un message "Cannot GET <votre-requête-route>" comme réponse. Ce message peut être remplacé par une page 404 not found en utilisant cette route simple.

```js
var express = require('express');
var app = express();

//Other routes here
app.get('*', function(req, res){
    res.send('Sorry, this is an invalid URL.');
});
app.listen(3000);
```

__Important__ - Cet élément doit être placé après toutes vos routes, car Express correspond aux routes du début à la fin du fichier index.js, y compris les routeurs externes que vous avez requis.

Par exemple, si nous appelons l'URL ```localhost:3000/thing/14554```, le message "id: 14554" sera retourné. A contrario, si nous appelons l'URL ```localhost:3000/thing/145```, le message "Sorry, this is an invalid URL." sera retourné, car "145" ne respecte par le Pattern défini dans l'URL (5 chiffres obligatoirement), et c'est donc la route ```*``` qui sera appelée.