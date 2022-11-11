Pug est un moteur de templating pour Express. Les moteurs de templating sont utilisés pour éliminer l'encombrement du code de notre serveur avec du HTML, en concaténant des chaînes de caractères de manière sauvage à des modèles HTML existants. Pug est un moteur de création de modèles très puissant qui dispose d'une grande variété de fonctionnalités, notamment les filtres, les inclusions, l'héritage, l'interpolation, etc. Il y a beaucoup de choses à couvrir sur ce sujet.

Pour utiliser Pug avec Express, nous devons l'installer,

```bash
npm install --save pug
```

Maintenant que Pug est installé, définissez-le comme le moteur de templating de votre application. Vous n'avez pas besoin de l'exiger. Ajoutez le code suivant à votre fichier index.js.

```js
app.set('view engine', 'pug');
app.set('views','./views');
```

Créez maintenant un nouveau répertoire appelé views. À l'intérieur de celui-ci, créez un fichier appelé first_view.pug, et entrez-y les données suivantes.

```
doctype html
html
    head
        title = "Hello Pug"
    body
        p.greetings#people Hello World!
```

To run this page, add the following route to your app −

```js
app.get('/first_template', function(req, res){
    res.render('first_view');
});
```

Vous obtiendrez le résultat suivant : Hello World ! Pug convertit ce balisage très simple en html. Nous n'avons pas besoin de garder la trace de la fermeture de nos balises, ni d'utiliser les mots-clés class et id, mais plutôt d'utiliser '.' et '#' pour les définir. Le code ci-dessus est d'abord converti en format -

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Hello Pug</title>
    </head>
    
    <body>
        <p class = "greetings" id = "people">Hello World!</p>
    </body>
</html>
```

Pug est capable de faire bien plus que de simplifier le balisage HTML.

## Caractéristiques importantes du Pug

Voyons maintenant quelques caractéristiques importantes de Pug.

### Simple Tags

Les balises sont imbriquées en fonction de leur indentation. Comme dans l'exemple ci-dessus, ```<title>``` était indenté à l'intérieur de la balise ```<head>```, il était donc à l'intérieur de celle-ci. Mais la balise ```<body>``` était sur la même indentation, elle était donc une sœur de la balise ```<head>```.

Nous n'avons pas besoin de fermer les balises, dès que Pug rencontre la balise suivante au même niveau d'indentation ou à un niveau supérieur, il ferme la balise pour nous.

Pour mettre du texte à l'intérieur d'une balise, nous avons 3 méthodes -

- **Espace séparé**

```
h1 Welcome to Pug
```

- **Texte passepoilé**

```
div
    | To insert multiline text, 
    | You can use the pipe operator.
```

- **Bloc de texte**

```
div.
    But that gets tedious if you have a lot of text.
    You can use "." at the end of tag to denote block of text.
    To put tags inside this block, simply enter tag in a new line and 
    indent it accordingly.
```

### Commentaire

Pug utilise la même syntaxe que JavaScript(//) pour créer des commentaires. Ces commentaires sont convertis en commentaires html(<!--comment-->). Par exemple,

```
//This is a Pug comment
```

Ce commentaire est converti en ce qui suit.

```
<!--This is a Pug comment-->
```

### Attributs

Pour définir les attributs, on utilise une liste d'attributs séparés par des virgules, entre parenthèses. Les attributs class et ID ont des représentations spéciales. La ligne de code suivante permet de définir les attributs, classes et id pour une balise html donnée.

```
div.container.column.main#division(width = "100", height = "100")
```

Cette ligne de code, est convertie en ce qui suit. -

```html
<div class = "container column main" id = "division" width = "100" height = "100"></div>
```

## Passer des valeurs aux Templates

Lorsque nous rendons un modèle Pug, nous pouvons en fait lui transmettre une valeur de notre gestionnaire de route, que nous pouvons ensuite utiliser dans notre modèle. Créez un nouveau gestionnaire de route avec les éléments suivants.

```js
var express = require('express');
var app = express();

app.get('/dynamic_view', function(req, res){
    res.render('dynamic', {
        name: "Microlead", 
        url:"https://microlead.fr"
    });
});

app.listen(3000);
```

Et créez un nouveau fichier de vue dans le répertoire views, appelé dynamic.pug, avec le code suivant -

```
html
    head
        title=name
    body
        h1=name
        a(href = url) URL
```

Nous pouvons également utiliser ces variables passées dans le texte. Pour insérer les variables passées dans le texte d'une balise, nous utilisons la syntaxe ```#{variableName}```. Par exemple, dans l'exemple ci-dessus, si nous voulions mettre Salutations de Microlead, nous aurions pu faire ce qui suit.

```
html
    head
        title = name
    body
        h1 Greetings from #{name}
        a(href = url) URL
```

Cette méthode d'utilisation des valeurs est appelée **interpolation**.

### Conditionnels

Nous pouvons également utiliser des instructions conditionnelles et des constructions en boucle.

Considérez les points suivants -

Si un utilisateur est connecté, la page doit afficher "Bonjour, utilisateur" et sinon, le lien "Connexion/Inscription". Pour ce faire, nous pouvons définir un modèle simple comme -

```
html
    head
        title Simple template
    body
        if(user)
            h1 Hi, #{user.name}
        else
            a(href = "/sign_up") Sign Up
```

Lorsque nous rendons ceci en utilisant nos routes, nous pouvons passer un objet comme dans le programme suivant -

```js
res.render('/dynamic',{
    user: {name: "Ayush", age: "20"}
});
```

Vous recevrez un message - Hi, Ayush. Mais si nous ne passons pas d'objet ou si nous en passons un sans clé d'utilisateur, alors nous obtiendrons un lien d'inscription.

### Include et Composants

Pug offre un moyen très intuitif de créer des composants pour une page Web. Par exemple, si vous voyez un site d'actualités, l'en-tête avec le logo et les catégories est toujours fixe. Au lieu de le copier dans chaque vue que nous créons, nous pouvons utiliser la fonction include. L'exemple suivant montre comment utiliser cette fonction.

Créez 3 vues avec le code suivant -

HEADER.PUG

```
div.header.
    I'm the header for this website.
```

CONTENT.PUG

```
html
    head
        title Simple template
    body
        include ./header.pug
        h3 I'm the main content
        include ./footer.pug
```

FOOTER.PUG

```
div.footer.
    I'm the footer for this website.
```

Créez une route pour cela comme suit -

```js
var express = require('express');
var app = express();

app.get('/components', function(req, res){
    res.render('content');
});

app.listen(3000);
```

Allez à ```localhost:3000/components```, vous devriez voir une page HTML avec les 3 parties du template apparaître devant vous.

include peut également être utilisé pour inclure du texte en clair, css et JavaScript.

Il existe de nombreuses autres fonctionnalités de Pug. Mais elles n'entrent pas dans le cadre de ce tutoriel. Vous pouvez explorer davantage Pug à Pug.