L'échafaudage nous permet de créer facilement un squelette pour une application Web. Nous créons manuellement notre répertoire public, ajoutons des intergiciels, créons des fichiers de route distincts, etc. Un outil d'échafaudage configure toutes ces choses pour nous afin que nous puissions commencer directement à construire notre application.

Le scaffolder que nous allons utiliser s'appelle Yeoman. Il s'agit d'un outil d'échafaudage conçu pour Node.js, mais qui possède également des générateurs pour plusieurs autres frameworks (comme flask, rails, django, etc.). Pour installer Yeoman, entrez la commande suivante dans votre terminal -

```bash
npm install -g yeoman
```

Yeoman utilise des générateurs pour échafauder des applications. Pour vérifier les générateurs disponibles sur npm à utiliser avec Yeoman, vous pouvez cliquer sur ce lien. Dans ce tutoriel, nous allons utiliser le 'generator-Express-simple'. Pour installer ce générateur, entrez la commande suivante dans votre terminal -

```bash
npm install -g generator-express-simple
```

Pour utiliser ce générateur, entrez la commande suivante -

```bash
yo express-simple test-app
```

On vous posera quelques questions simples, comme les éléments que vous voulez utiliser avec votre application. Sélectionnez les réponses suivantes, ou si vous connaissez déjà ces technologies, choisissez comment vous voulez qu'elles soient.

```bash
express-simple comes with bootstrap and jquery
[?] Select the express version you want: 4.x
[?] Do you want an mvc express app: Yes
[?] Select the css preprocessor you would like to use: sass
[?] Select view engine you would like to use: jade
[?] Select the build tool you want to use for this project: gulp
[?] Select the build tool you want to use for this project: gulp
[?] Select the language you want to use for the build tool: javascript
    create public/sass/styles.scss
    create public/js/main.js
    create views/layout.jade
    create views/index.jade
    create views/404.jade
    create app.js
    create config.js
    create routes/index.js
    create package.json
    create bower.json
identical .bowerrc
identical .editorconfig
identical .gitignore
identical .jshintrc
    create gulpfile.js

I'm all done. Running bower install & npm install for you to install the
required dependencies. If this fails, try running the command yourself.
```

Il créera alors une nouvelle application pour vous, installera toutes les dépendances, ajoutera quelques pages à votre application (page d'accueil, page 404 non trouvée, etc.) et vous donnera une structure de répertoire sur laquelle travailler.

Ce générateur nous crée une structure très simple. Explorez les nombreux générateurs disponibles pour Express et choisissez celui qui vous convient le mieux. La marche à suivre pour travailler avec tous les générateurs est la même. Vous devez installer un générateur, le lancer à l'aide de Yeoman ; il vous posera quelques questions et créera ensuite un squelette pour votre application en fonction de vos réponses.