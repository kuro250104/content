Contrairement à Django et Rails qui ont une manière définie de faire les choses, une structure de fichiers, etc., Express ne suit pas une manière définie. Cela signifie que vous pouvez structurer l'application comme vous le souhaitez. Mais lorsque la taille de votre application augmente, il est très difficile de la maintenir si elle n'a pas une structure bien définie. Dans ce chapitre, nous allons examiner les structures de répertoire et la séparation des préoccupations généralement utilisées pour construire nos applications.

Tout d'abord, nous aborderons les meilleures pratiques pour créer des applications node et Express.

- Toujours commencer un projet node en utilisant npm init.
- Installez toujours les dépendances avec un --save ou --save-dev. Ainsi, si vous passez à une autre plateforme, il vous suffira d'exécuter npm install pour installer toutes les dépendances.
- Conservez les noms de fichiers en minuscules et les variables en camelCase. Si vous regardez n'importe quel module npm, il est nommé en minuscules et séparé par des tirets. Chaque fois que vous avez besoin de ces modules, utilisez le camelCase.
- Ne poussez pas node_modules dans vos dépôts. Au lieu de cela, npm installe tout sur les machines de développement.
- Utiliser un fichier de configuration pour stocker les variables
- Regroupez et isolez les routes dans leur propre fichier. Par exemple, prenez les opérations CRUD dans l'exemple de films que nous avons vu dans la page API REST.

## Structure du répertoire

Voyons maintenant la structure du répertoire d'Express.

### Sites web

Express ne dispose pas d'une structure définie par la communauté pour créer des applications. Voici la structure de projet la plus utilisée pour un site web.

```bash
test-project/
    node_modules/
    config/
        db.js                //Database connection and configuration
        credentials.js       //Passwords/API keys for external services used by your app
        config.js            //Other environment variables
    models/                 //For mongoose schemas
        users.js
        things.js
    routes/                 //All routes for different entities in different files 
        users.js
        things.js
    views/
        index.pug
        404.pug
            ...
    public/                 //All static content being served
        images/
        css/
        javascript/
    app.js
    routes.js               //Require all routes in this and then require this file in 
    app.js 
    package.json
```

Il existe également d'autres approches pour créer des sites Web avec Express. Vous pouvez créer un site Web en utilisant le modèle de conception MVC.

### RESTful APIs

Les API sont plus simples à concevoir ; elles n'ont pas besoin d'un répertoire public ou d'un répertoire des vues. Utilisez la structure suivante pour construire des API

```bash
test-project/
    node_modules/
    config/
        db.js                //Database connection and configuration
        credentials.js       //Passwords/API keys for external services used by your app
    models/                 //For mongoose schemas
        users.js
        things.js
    routes/                 //All routes for different entities in different files 
        users.js
        things.js
    app.js
    routes.js               //Require all routes in this and then require this file in 
    app.js 
    package.json
```

Vous pouvez également utiliser un générateur de yeoman pour obtenir une structure similaire.