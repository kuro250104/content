Le protocole HTTP est apatride ; afin d'associer une demande à toute autre demande, il faut un moyen de stocker les données de l'utilisateur entre les demandes HTTP. Les cookies et les paramètres d'URL sont deux moyens appropriés pour transporter des données entre le client et le serveur. Mais ils sont tous deux lisibles et se trouvent du côté du client. Les sessions résolvent exactement ce problème. Vous attribuez au client un identifiant et il effectue toutes les demandes ultérieures en utilisant cet identifiant. Les informations associées au client sont stockées sur le serveur en lien avec cet ID.

Nous aurons besoin de la session Express, donc installez-la en utilisant le code suivant.

```bash
npm install --save express-session
```

Nous allons mettre en place le middleware de session et de cookie-parser. Dans cet exemple, nous utiliserons le magasin par défaut pour stocker les sessions, c'est-à-dire MemoryStore. Ne l'utilisez jamais dans un environnement de production. Le middleware de session gère tout pour nous, c'est-à-dire la création de la session, la définition du cookie de session et la création de l'objet de session dans l'objet req.

Chaque fois que nous effectuons une nouvelle requête du même client, les informations de session de ce dernier sont stockées avec nous (à condition que le serveur n'ait pas été redémarré). Nous pouvons ajouter d'autres propriétés à l'objet de session. Dans l'exemple suivant, nous allons créer un compteur de vues pour un client.

```js
var express = require('express');
var cookieParser = require('cookie-parser');
var session = require('express-session');

var app = express();

app.use(cookieParser());
app.use(session({secret: "Shh, its a secret!"}));

app.get('/', function(req, res){
    if(req.session.page_views){
        req.session.page_views++;
        res.send("You visited this page " + req.session.page_views + " times");
    } else {
        req.session.page_views = 1;
        res.send("Welcome to this page for the first time!");
    }
});
app.listen(3000);
```

Ce que fait le code ci-dessus, c'est que lorsqu'un utilisateur visite le site, il crée une nouvelle session pour l'utilisateur et lui attribue un cookie. La prochaine fois que l'utilisateur vient, le cookie est vérifié et la variable de session page_view est mise à jour en conséquence.

Maintenant, si vous exécutez l'application et allez à localhost:3000, la sortie suivante sera affichée: "Welcome to this page for the first time!"

Si vous revisitez la page, le compteur de pages augmente et l'autre message apparaîtra avec le nombre de fois où la page à été raffraichit.