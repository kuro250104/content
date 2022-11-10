Le gestionnaire de paquets Node (NPM) fournit deux fonctionnalités principales :

- Dépôts en ligne pour les paquets/modules node.js qui sont consultables sur search.nodejs.org.
- Utilitaire en ligne de commande pour installer des paquets Node.js, faire la gestion des versions et des dépendances des paquets Node.js.

NPM est fourni avec les installables Node.js après la version v0.6.3. Pour vérifier la même chose, ouvrez la console et tapez la commande suivante et voyez le résultat :

```bash
$ npm --version
2.7.1
```

Si vous utilisez une ancienne version de NPM, il est assez facile de la mettre à jour avec la dernière version. Il suffit d'utiliser la commande suivante depuis l'utilisateur root :

```bash
$ sudo npm install npm -g
/usr/bin/npm -> /usr/lib/node_modules/npm/bin/npm-cli.js
npm@2.7.1 /usr/lib/node_modules/npm
```

## Installation de modules à l'aide de NPM

Il existe une syntaxe simple pour installer n'importe quel module Node.js :

```bash
$ npm install <Module Name>
```

Par exemple, la commande suivante permet d'installer un module du célèbre framework web Node.js appelé express :

```bash
$ npm install express
```

Maintenant, vous pouvez utiliser ce module dans votre fichier js comme suit :

```js
var express = require('express');
```

## Installation globale ou locale

Par défaut, NPM installe toute dépendance en mode local. Ici, le mode local fait référence à l'installation du paquet dans le répertoire **node_modules** situé dans le dossier où se trouve l'application Node. Les paquets déployés localement sont accessibles via la méthode ```require()```. Par exemple, lorsque nous avons installé le module express, il a créé le répertoire node_modules dans le répertoire actuel où il a installé le module express.

```bash
$ ls -l
total 0
drwxr-xr-x 3 root root 20 Mar 17 02:23 node_modules
```

Vous pouvez également utiliser la commande ```npm ls``` pour répertorier tous les modules installés localement.

Les paquets/dépendances installés globalement sont stockés dans le répertoire système. De telles dépendances peuvent être utilisées dans la fonction CLI (Command Line Interface) de n'importe quel node.js mais ne peuvent pas être importées en utilisant require() dans une application Node directement. Essayons maintenant d'installer le module express en utilisant l'installation globale.

```bash
$ npm install express -g
```

Cela produira un résultat similaire mais le module sera installé globalement. Ici, la première ligne indique la version du module et l'endroit où il est installé.

```bash
express@4.12.2 /usr/lib/node_modules/express
├── merge-descriptors@1.0.0
├── utils-merge@1.0.0
├── cookie-signature@1.0.6
├── methods@1.1.1
├── fresh@0.2.4
├── cookie@0.1.2
├── escape-html@1.0.1
├── range-parser@1.0.2
├── content-type@1.0.1
├── finalhandler@0.3.3
├── vary@1.0.0
├── parseurl@1.3.0
├── content-disposition@0.5.0
├── path-to-regexp@0.1.3
├── depd@1.0.0
├── qs@2.3.3
├── on-finished@2.2.0 (ee-first@1.1.0)
├── etag@1.5.1 (crc@3.2.1)
├── debug@2.1.3 (ms@0.7.0)
├── proxy-addr@1.0.7 (forwarded@0.1.0, ipaddr.js@0.1.9)
├── send@0.12.1 (destroy@1.0.3, ms@0.7.0, mime@1.3.4)
├── serve-static@1.9.2 (send@0.12.2)
├── accepts@1.2.5 (negotiator@0.5.1, mime-types@2.0.10)
└── type-is@1.6.1 (media-typer@0.3.0, mime-types@2.0.10)
```

Vous pouvez utiliser la commande suivante pour vérifier tous les modules installés globalement :

```bash
$ npm ls -g
```

## Utilisation de package.json

```package.json``` est présent dans le répertoire racine de toute application/module Node et est utilisé pour définir les propriétés d'un paquet. Ouvrons le ```package.json``` du package express présent dans ```node_modules/express/```

```json
{
    "name": "express",
        "description": "Fast, unopinionated, minimalist web framework",
        "version": "4.11.2",
        "author": {
        
            "name": "TJ Holowaychuk",
            "email": "tj@vision-media.ca"
        },
    
    "contributors": [{
        "name": "Aaron Heckmann",
        "email": "aaron.heckmann+github@gmail.com"
    }, 
    
    {
        "name": "Ciaran Jessup",
        "email": "ciaranj@gmail.com"
    },
    
    {
        "name": "Douglas Christopher Wilson",
        "email": "doug@somethingdoug.com"
    },
    
    {
        "name": "Guillermo Rauch",
        "email": "rauchg@gmail.com"
    },
    
    {
        "name": "Jonathan Ong",
        "email": "me@jongleberry.com"
    },
    
    {
        "name": "Roman Shtylman",
        "email": "shtylman+expressjs@gmail.com"
    },
    
    {
        "name": "Young Jae Sim",
        "email": "hanul@hanul.me"
    } ],
    
    "license": "MIT", "repository": {
        "type": "git",
        "url": "https://github.com/strongloop/express"
    },
    
    "homepage": "https://expressjs.com/", "keywords": [
        "express",
        "framework",
        "sinatra",
        "web",
        "rest",
        "restful",
        "router",
        "app",
        "api"
    ],
    
    "dependencies": {
        "accepts": "~1.2.3",
        "content-disposition": "0.5.0",
        "cookie-signature": "1.0.5",
        "debug": "~2.1.1",
        "depd": "~1.0.0",
        "escape-html": "1.0.1",
        "etag": "~1.5.1",
        "finalhandler": "0.3.3",
        "fresh": "0.2.4",
        "media-typer": "0.3.0",
        "methods": "~1.1.1",
        "on-finished": "~2.2.0",
        "parseurl": "~1.3.0",
        "path-to-regexp": "0.1.3",
        "proxy-addr": "~1.0.6",
        "qs": "2.3.3",
        "range-parser": "~1.0.2",
        "send": "0.11.1",
        "serve-static": "~1.8.1",
        "type-is": "~1.5.6",
        "vary": "~1.0.0",
        "cookie": "0.1.2",
        "merge-descriptors": "0.0.2",
        "utils-merge": "1.0.0"
    },
    
    "devDependencies": {
        "after": "0.8.1",
        "ejs": "2.1.4",
        "istanbul": "0.3.5",
        "marked": "0.3.3",
        "mocha": "~2.1.0",
        "should": "~4.6.2",
        "supertest": "~0.15.0",
        "hjs": "~0.0.6",
        "body-parser": "~1.11.0",
        "connect-redis": "~2.2.0",
        "cookie-parser": "~1.3.3",
        "express-session": "~1.10.2",
        "jade": "~1.9.1",
        "method-override": "~2.3.1",
        "morgan": "~1.5.1",
        "multiparty": "~4.1.1",
        "vhost": "~3.0.0"
    },
    
    "engines": {
        "node": ">= 0.10.0"
    },
    
    "files": [
        "LICENSE",
        "History.md",
        "Readme.md",
        "index.js",
        "lib/"
    ],
    
    "scripts": {
        "test": "mocha --require test/support/env 
            --reporter spec --bail --check-leaks test/ test/acceptance/",
        "test-cov": "istanbul cover node_modules/mocha/bin/_mocha 
            -- --require test/support/env --reporter dot --check-leaks test/ test/acceptance/",
        "test-tap": "mocha --require test/support/env 
            --reporter tap --check-leaks test/ test/acceptance/",
        "test-travis": "istanbul cover node_modules/mocha/bin/_mocha 
            --report lcovonly -- --require test/support/env 
            --reporter spec --check-leaks test/ test/acceptance/"
    },
    
    "gitHead": "63ab25579bda70b4927a179b580a9c580b6c7ada",
    "bugs": {
        "url": "https://github.com/strongloop/express/issues"
    },
    
    "_id": "express@4.11.2",
    "_shasum": "8df3d5a9ac848585f00a0777601823faecd3b148",
    "_from": "express@*",
    "_npmVersion": "1.4.28",
    "_npmUser": {
        "name": "dougwilson",
        "email": "doug@somethingdoug.com"
    },
    
    "maintainers": [{
        "name": "tjholowaychuk",
        "email": "tj@vision-media.ca"
    },
    
    {
        "name": "jongleberry",
        "email": "jonathanrichardong@gmail.com"
    },
    
    {
        "name": "shtylman",
        "email": "shtylman@gmail.com"
    },
    
    {
        "name": "dougwilson",
        "email": "doug@somethingdoug.com"
    },
    
    {
        "name": "aredridel",
        "email": "aredridel@nbtsc.org"
    },
    
    {
        "name": "strongloop",
        "email": "callback@strongloop.com"
    },
    
    {
        "name": "rfeng",
        "email": "enjoyjava@gmail.com"
    }],
    
    "dist": {
        "shasum": "8df3d5a9ac848585f00a0777601823faecd3b148",
        "tarball": "https://registry.npmjs.org/express/-/express-4.11.2.tgz"
    },
    
    "directories": {},
        "_resolved": "https://registry.npmjs.org/express/-/express-4.11.2.tgz",
        "readme": "ERROR: No README data found!"
}
```

## Attributs de Package.json

- **name** - nom du paquet
- **version** - version du paquet
- **description** - description du paquet
- **homepage** - page d'accueil du paquet
- **author** - auteur du paquet
- **contributeurs** - nom des contributeurs du paquet
- **dependencies** - liste des dépendances. NPM installe automatiquement toutes les dépendances mentionnées ici dans le dossier node_module du paquet.
- **repository** - type de dépôt et URL du paquet.
- **main** - point d'entrée du paquet
- **keywords** - mots-clés

## Désinstallation d'un module

Utilisez la commande suivante pour désinstaller un module Node.js.

```bash
$ npm uninstall express
```

Une fois que NPM a désinstallé le paquet, vous pouvez le vérifier en regardant le contenu du répertoire /node_modules/ ou taper la commande suivante :

```bash
$ npm ls
```

## Mise à jour d'un module

Mettez à jour le fichier package.json et modifiez la version de la dépendance à mettre à jour et exécutez la commande suivante.

```bash
$ npm update express
```

## Rechercher un module

Rechercher un nom de paquet en utilisant NPM.

```bash
$ npm search express
```

## Créer un module

La création d'un module nécessite la génération d'un package.json. Générons le package.json à l'aide de NPM, qui générera le squelette de base du package.json.

```bash
$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sane defaults.

See 'npm help json' for definitive documentation on these fields
and exactly what they do.

Use 'npm install <pkg> --save' afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
name: (webmaster)
```

Vous devrez fournir toutes les informations requises sur votre module. Vous pouvez vous aider du fichier package.json mentionné ci-dessus pour comprendre la signification des différentes informations demandées. Une fois le fichier package.json généré, utilisez la commande suivante pour vous enregistrer sur le site du dépôt NPM en utilisant une adresse e-mail valide.

```bash
$ npm adduser
Username: mcmohd
Password:
Email: (this IS public) mcmohd@gmail.com
```

Il est maintenant temps de publier votre module :

```bash
$ npm publish
```

Si tout va bien avec votre module, alors il sera publié dans le dépôt et sera accessible pour être installé en utilisant NPM comme n'importe quel autre module Node.js.