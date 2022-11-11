L'authentification est un processus dans lequel les informations d'identification fournies sont comparées à celles contenues dans une base de données d'informations sur les utilisateurs autorisés sur un système d'exploitation local ou dans un serveur d'authentification. Si les informations d'identification correspondent, le processus est terminé et l'utilisateur se voit accorder l'autorisation d'accès.

Pour créer un système d'authentification, nous devrons créer une page d'inscription et un magasin de mots de passe pour les utilisateurs. Le code suivant crée un compte pour nous et le stocke en mémoire. Ceci est juste pour les besoins de la démo ; il est recommandé de toujours utiliser un stockage persistant (base de données ou fichiers) pour stocker les informations de l'utilisateur.

```js
var express = require('express');
var app = express();
var bodyParser = require('body-parser');
var multer = require('multer');
var upload = multer(); 
var session = require('express-session');
var cookieParser = require('cookie-parser');

app.set('view engine', 'pug');
app.set('views','./views');

app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true })); 
app.use(upload.array());
app.use(cookieParser());
app.use(session({secret: "Your secret key"}));

var Users = [];

app.get('/signup', function(req, res){
    res.render('signup');
});

app.post('/signup', function(req, res){
    if(!req.body.id || !req.body.password){
        res.status("400");
        res.send("Invalid details!");
    } else {
        Users.filter(function(user){
            if(user.id === req.body.id){
                res.render('signup', {
                message: "User Already Exists! Login or choose another user id"});
            }
        });
        var newUser = {id: req.body.id, password: req.body.password};
        Users.push(newUser);
        req.session.user = newUser;
        res.redirect('/protected_page');
    }
});

app.listen(3000);
```

Maintenant pour le formulaire d'inscription, créez une nouvelle vue appelée signup.jade.

SIGNUP.JADE

```
html
    head
        title Signup
    body
        if(message)
            h4 #{message}
            form(action = "/signup" method = "POST")
            input(name = "id" type = "text" required placeholder = "User ID")
            input(name = "password" type = "password" required placeholder = "Password")
            button(type = "Submit") Sign me up!
```

Vérifiez si cette page se charge en visitant localhost:3000/signup.

Nous avons défini l'attribut obligatoire pour les deux champs, de sorte que les navigateurs compatibles HTML5 ne nous laisseront pas soumettre ce formulaire tant que nous n'aurons pas fourni l'identifiant et le mot de passe. Si quelqu'un tente de s'inscrire à l'aide d'une requête curl sans identifiant ni mot de passe, une erreur s'affichera. Créez un nouveau fichier appelé protected_page.pug dans views avec le contenu suivant -

```
html
    head
        title Protected page
    body
        div Hey #{id}, How are you doing today?
        div Want to log out?
        div Logout
```

Cette page ne doit être visible que si l'utilisateur vient de s'inscrire ou de se connecter. Définissons maintenant sa route ainsi que les routes pour se connecter et se déconnecter.

```js
var express = require('express');
var app = express();
var bodyParser = require('body-parser');
var multer = require('multer');
var upload = multer(); 
var session = require('express-session');
var cookieParser = require('cookie-parser');

app.set('view engine', 'pug');
app.set('views','./views');

app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true })); 
app.use(upload.array());
app.use(cookieParser());
app.use(session({secret: "Your secret key"}));

var Users = [];

app.get('/signup', function(req, res){
    res.render('signup');
});

app.post('/signup', function(req, res){
    if(!req.body.id || !req.body.password){
        res.status("400");
        res.send("Invalid details!");
    } else {
        Users.filter(function(user){
            if(user.id === req.body.id){
                res.render('signup', {
                message: "User Already Exists! Login or choose another user id"});
            }
        });
        var newUser = {id: req.body.id, password: req.body.password};
        Users.push(newUser);
        req.session.user = newUser;
        res.redirect('/protected_page');
    }
});
function checkSignIn(req, res){
    if(req.session.user){
        next();     //If session exists, proceed to page
    } else {
        var err = new Error("Not logged in!");
        console.log(req.session.user);
        next(err);  //Error, trying to access unauthorized page!
    }
}
app.get('/protected_page', checkSignIn, function(req, res){
    res.render('protected_page', {id: req.session.user.id})
});

app.get('/login', function(req, res){
    res.render('login');
});

app.post('/login', function(req, res){
    console.log(Users);
    if(!req.body.id || !req.body.password){
        res.render('login', {message: "Please enter both id and password"});
    } else {
        Users.filter(function(user){
            if(user.id === req.body.id && user.password === req.body.password){
                req.session.user = user;
                res.redirect('/protected_page');
            }
        });
        res.render('login', {message: "Invalid credentials!"});
    }
});

app.get('/logout', function(req, res){
    req.session.destroy(function(){
        console.log("user logged out.")
    });
    res.redirect('/login');
});

app.use('/protected_page', function(err, req, res, next){
console.log(err);
    //User should be authenticated! Redirect him to log in.
    res.redirect('/login');
});

app.listen(3000);
```

Nous avons créé une fonction middleware checkSignIn pour vérifier si l'utilisateur est connecté. La protected_page utilise cette fonction. Pour déconnecter l'utilisateur, nous détruisons la session.

Créons maintenant la page de connexion. Nommez la vue en tant que login.pug et entrez le contenu -

```
html
    head
        title Signup
    body
        if(message)
            h4 #{message}
            form(action = "/login" method = "POST")
            input(name = "id" type = "text" required placeholder = "User ID")
            input(name = "password" type = "password" required placeholder = "Password")
            button(type = "Submit") Log in
```

Notre application d'authentification simple est maintenant terminée ; testons-la maintenant. Lancez l'application en utilisant nodemon index.js, et allez sur localhost:3000/signup.

Saisissez un nom d'utilisateur et un mot de passe et cliquez sur s'inscrire. Vous serez redirigé vers la page protected_page si les détails sont valides/uniques.

Maintenant, déconnectez-vous de l'application. Cela nous redirigera vers la page de connexion.

Cette route est protégée de telle sorte que si une personne non authentifiée tente de la visiter, elle sera redirigée vers notre page de connexion. Tout ceci concernait l'authentification de base des utilisateurs. Il est toujours recommandé d'utiliser un système de session persistante et d'utiliser des hachages pour le transport des mots de passe. Il existe maintenant de bien meilleures façons d'authentifier les utilisateurs, en utilisant des jetons JSON.