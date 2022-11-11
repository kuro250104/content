Les formulaires font partie intégrante du web. Presque tous les sites web que nous visitons nous proposent des formulaires qui soumettent ou récupèrent des informations pour nous. Pour commencer à utiliser les formulaires, nous allons d'abord installer le middleware body-parser (pour analyser les données JSON et url-encodées) et multer (pour analyser les données multipart/form).
Pour installer le body-parser et le multer, allez dans votre terminal et utilisez -

```bash
npm install --save body-parser multer
```

Remplacez le contenu de votre fichier index.js par le code suivant -

```js
var express = require('express');
var bodyParser = require('body-parser');
var multer = require('multer');
var upload = multer();
var app = express();

app.get('/', function(req, res){
   res.render('form');
});

app.set('view engine', 'pug');
app.set('views', './views');

// for parsing application/json
app.use(bodyParser.json()); 

// for parsing application/xwww-
app.use(bodyParser.urlencoded({ extended: true })); 
//form-urlencoded

// for parsing multipart/form-data
app.use(upload.array()); 
app.use(express.static('public'));

app.post('/', function(req, res){
    console.log(req.body);
    res.send("recieved your request!");
});
app.listen(3000);
```

Après avoir importé le body parser et multer, nous utiliserons le b pour analyser les requêtes json et x-www-form-urlencoded header, tandis que nous utiliserons multer pour analyser les multipart/form-data.

Créons un formulaire html pour le tester. Créez une nouvelle vue appelée form.pug avec le code suivant -

```
html
    head
        title Form Tester
    body
        form(action = "/", method = "POST")
            div
                label(for = "say") Say:
                input(name = "say" value = "Hi")
            br
            div
                label(for = "to") To:
                input(name = "to" value = "Express forms")
            br
            button(type = "submit") Send my greetings
```

Exécutez votre serveur en utilisant ce qui suit.

```bash
nodemon index.js
```

Maintenant, allez sur localhost:3000/ et remplissez le formulaire comme vous le souhaitez, puis soumettez-le.

Jetez un coup d'œil à votre console ; elle vous montrera le corps de votre requête sous la forme d'un objet JavaScript.

L'objet req.body contient le corps de votre requête analysée. Pour utiliser les champs de cet objet, il suffit de les utiliser comme des objets JS normaux.

C'est la façon la plus recommandée d'envoyer une demande. Il existe de nombreux autres moyens, mais il est inutile de les aborder ici, car notre application Express traitera toutes ces demandes de la même manière. Pour en savoir plus sur les différentes manières d'envoyer une demande, consultez cette page.