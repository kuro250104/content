Nous continuons à recevoir des demandes, mais nous finissons par ne les stocker nulle part. Nous avons besoin d'une base de données pour stocker les données. Pour cela, nous allons utiliser la base de données NoSQL appelée MongoDB.

Afin d'utiliser Mongo avec Express, nous avons besoin d'une API client pour node. Il existe de multiples options pour nous, mais pour ce tutoriel, nous nous en tiendrons à Mongoose. Mongoose est utilisé pour la modélisation de documents dans Node pour MongoDB. Pour la modélisation de documents, nous créons un modèle (un peu comme une classe dans la programmation orientée document), puis nous produisons des documents en utilisant ce modèle (comme nous créons des documents d'une classe dans la POO). Tous nos traitements seront effectués sur ces "documents", puis finalement, nous écrirons ces documents dans notre base de données.

## Paramétrage de Mongoose

Maintenant que vous avez installé Mongo, installons Mongoose, de la même manière que nous avons installé les autres paquets de node.

```bash
npm install --save mongoose
```

Avant de commencer à utiliser Mongoose, nous devons créer une base de données en utilisant le shell Mongo. Pour créer une nouvelle base de données, ouvrez votre terminal et entrez "mongo". Un shell Mongo va démarrer, entrez le code suivant -
use my_db

Une nouvelle base de données sera créée pour vous. Chaque fois que vous ouvrirez le shell mongo, il utilisera par défaut la base de données "test" et vous devrez la changer pour votre base de données en utilisant la même commande que ci-dessus.

Pour utiliser Mongoose, nous allons l'exiger dans notre fichier index.js, puis nous connecter au service mongodb qui fonctionne sur mongodb://localhost.

```js
var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/my_db');
```

Maintenant que notre application est connectée à notre base de données, créons un nouveau modèle. Ce modèle agira comme une collection dans notre base de données. Pour créer un nouveau modèle, utilisez le code suivant, avant de définir une route.

```js
var personSchema = mongoose.Schema({
   name: String,
   age: Number,
   nationality: String
});
var Person = mongoose.model("Person", personSchema);
```

Le code ci-dessus définit le schéma d'une personne et est utilisé pour créer une personne en mode Mongoose.

## Sauvegarde de Documents

Maintenant, nous allons créer un nouveau formulaire html ; ce formulaire vous aidera à obtenir les détails d'une personne et à les enregistrer dans notre base de données. Pour créer le formulaire, créez un nouveau fichier de vue appelé person.pug dans le répertoire views avec le contenu suivant -

```
html
head
    title Person
    body
        form(action = "/person", method = "POST")
        div
            label(for = "name") Name: 
            input(name = "name")
        br
        div
            label(for = "age") Age: 
            input(name = "age")
        br
        div
            label(for = "nationality") Nationality: 
            input(name = "nationality")
        br
        button(type = "submit") Create new person
```

Ajoutez également une nouvelle route get dans index.js pour rendre ce document

```js
app.get('/person', function(req, res){
    res.render('person');
});
```

Allez sur ```localhost:3000/person``` pour vérifier si le formulaire affiche la sortie correcte. Notez que ce n'est que l'interface utilisateur, elle n'est pas encore fonctionnelle.

Nous allons maintenant définir un gestionnaire de route post à '/person' qui traitera cette requête

```js
app.post('/person', function(req, res){
    var personInfo = req.body; //Get the parsed information

    if(!personInfo.name || !personInfo.age || !personInfo.nationality){
        res.render('show_message', {
            message: "Sorry, you provided worng info", type: "error"});
    } else {
        var newPerson = new Person({
            name: personInfo.name,
            age: personInfo.age,
            nationality: personInfo.nationality
        });
            
        newPerson.save(function(err, Person){
            if(err)
                res.render('show_message', {message: "Database error", type: "error"});
            else
                res.render('show_message', {
                message: "New person added", type: "success", person: personInfo});
        });
    }
});
```

Dans le code ci-dessus, si nous recevons un champ vide ou si nous ne recevons aucun champ, nous enverrons une réponse d'erreur. Mais si nous recevons un document bien formé, nous créons un document newPerson à partir du modèle Person et le sauvegardons dans notre base de données à l'aide de la fonction ```newPerson.save()```. Cette fonction est définie dans Mongoose et accepte un callback comme argument. Ce callback a 2 arguments - erreur et réponse. Ces arguments vont rendre la vue show_message.

Pour afficher la réponse de cette route, nous devons également créer une vue show_message. Créez une nouvelle vue avec le code suivant -

```
html
    head
        title Person
    body
        if(type == "error")
            h3(style = "color:red") #{message}
        else
            h3 New person, 
                name: #{person.name}, 
                age: #{person.age} and 
                nationality: #{person.nationality} added!
```

Nous disposons maintenant d'une interface pour créer des personnes.

## Récupération de Documents

Mongoose fournit de nombreuses fonctions pour récupérer des documents, nous allons nous concentrer sur 3 d'entre elles. Toutes ces fonctions prennent également un callback comme dernier paramètre, et tout comme la fonction save, leurs arguments sont l'erreur et la réponse. Les trois fonctions sont les suivantes -

### Model.find(conditions, callback)

Cette fonction trouve tous les documents correspondant aux champs de l'objet conditions. Les mêmes opérateurs utilisés dans Mongo fonctionnent également dans Mongoose. Par exemple,

```js
Person.find(function(err, response){
    console.log(response);
});
```

Cela permettra de récupérer tous les documents de la collection de la personne.

```js
Person.find({name: "Ayush", age: 20}, 
    function(err, response){
        console.log(response);
    }
);
```

Cela permettra de récupérer tous les documents pour lesquels le nom du champ est "Ayush" et l'âge est 20.

Nous pouvons également fournir la projection dont nous avons besoin, c'est-à-dire les champs dont nous avons besoin. Par exemple, si nous voulons uniquement les noms des personnes dont la nationalité est "indienne", nous utilisons -

```js
Person.find({nationality: "Indian"}, "name", function(err, response){
    console.log(response);
});
```

### Model.findOne(conditions, callback)

Cette fonction récupère toujours un seul document, le plus pertinent. Elle possède exactement les mêmes arguments que ```Model.find()```.

### Model.findById(id, callback)

Cette fonction prend l'_id (défini par mongo) comme premier argument, une chaîne de projection optionnelle et un callback pour gérer la réponse. Par exemple,

```js
Person.findById("507f1f77bcf86cd799439011", function(err, response){
    console.log(response);
});
```

Créons maintenant une route pour visualiser tous les enregistrements de personnes -

```js
var express = require('express');
var app = express();

var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/my_db');

var personSchema = mongoose.Schema({
    name: String,
    age: Number,
    nationality: String
});

var Person = mongoose.model("Person", personSchema);

app.get('/people', function(req, res){
    Person.find(function(err, response){
        res.json(response);
    });
});

app.listen(3000);
```

## Modification de Documents

Mongoose fournit 3 fonctions pour mettre à jour les documents. Les fonctions sont décrites ci-dessous -

### Model.findOneAndUpdate(condition, updates, callback)

Il trouve un document basé sur la requête et le met à jour en fonction du deuxième argument. Elle prend également un callback comme dernier argument. Exécutons l'exemple suivant pour comprendre la fonction

```js
Person.findOneAndUpdate({name: "Ayush"}, {age: 40}, function(err, response) {
    console.log(response);
});
```

### Model.findByIdAndUpdate(id, updates, callback)

Cette fonction met à jour un seul document identifié par son id. Par exemple,

```js
Person.findByIdAndUpdate("507f1f77bcf86cd799439011", {name: "James"}, 
    function(err, response){
        console.log(response);
    }
);
```

Créons maintenant une route pour mettre à jour les personnes. Il s'agira d'une route PUT avec l'identifiant comme paramètre et les détails dans la charge utile.

```js
var express = require('express');
var app = express();

var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/my_db');

var personSchema = mongoose.Schema({
    name: String,
    age: Number,
    nationality: String
});

var Person = mongoose.model("Person", personSchema);

app.put('/people/:id', function(req, res){
    Person.findByIdAndUpdate(req.params.id, req.body, function(err, response){
        if(err) res.json({message: "Error in updating person with id " + req.params.id});
        res.json(response);
    });
});

app.listen(3000);
```

Pour tester cette route, entrez ce qui suit dans votre terminal (remplacez l'id par un id de vos personnes créées) -

```bash
curl -X PUT --data "name = James&age = 20&nationality = American
"http://localhost:3000/people/507f1f77bcf86cd799439011
```

Cela mettra à jour le document associé à l'identifiant fourni dans la route avec les détails ci-dessus.

## Suppression de Documents

Nous avons couvert la création, la lecture et la mise à jour, nous allons maintenant voir comment Mongoose peut être utilisé pour supprimer des documents. Nous avons ici 3 fonctions, exactement comme pour la mise à jour.

### Model.remove(condition, [callback])

Cette fonction prend un objet de condition en entrée et supprime tous les documents correspondant aux conditions. Par exemple, si nous devons supprimer toutes les personnes âgées de 20 ans, utilisez la syntaxe suivante -

```js
Person.remove({age:20});
```

### Model.findOneAndRemove(condition, [callback])

Cette fonction supprime un seul document, le plus pertinent, en fonction de l'objet des conditions. Exécutons le code suivant pour comprendre la même chose.

```js
Person.findOneAndRemove({name: "Ayush"});
```

### Model.findByIdAndRemove(id, [callback])

Cette fonction supprime un seul document identifié par son id. Par exemple,

```js
Person.findByIdAndRemove("507f1f77bcf86cd799439011");
```

Créons maintenant une route pour supprimer des personnes de notre base de données.

```js
var express = require('express');
var app = express();

var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/my_db');

var personSchema = mongoose.Schema({
    name: String,
    age: Number,
    nationality: String
});

var Person = mongoose.model("Person", personSchema);

app.delete('/people/:id', function(req, res){
    Person.findByIdAndRemove(req.params.id, function(err, response){
        if(err) res.json({message: "Error in deleting record id " + req.params.id});
        else res.json({message: "Person with id " + req.params.id + " removed."});
    });
});

app.listen(3000);
```

Pour vérifier la sortie, utilisez la commande curl suivante -

```bash
curl -X DELETE http://localhost:3000/people/507f1f77bcf86cd799439011
```

Cela supprimera la personne avec l'id donné en produisant le message suivant -

```bash
{message: "Person with id 507f1f77bcf86cd799439011 removed."}
```

Ceci résume la façon dont nous pouvons créer des applications CRUD simples en utilisant MongoDB, Mongoose et Express. Pour explorer Mongoose plus en profondeur, lisez les documents de l'API.