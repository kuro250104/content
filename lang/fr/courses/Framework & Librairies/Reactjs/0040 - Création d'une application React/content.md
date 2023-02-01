## Introduction

Comme nous l'avons appris précédemment, la bibliothèque React peut être utilisée dans les applications simples et complexes. Une application simple inclut normalement la bibliothèque React dans sa section script. Dans une application complexe, les développeurs doivent diviser le code en plusieurs fichiers et organiser le code dans une structure standard. Ici, la chaîne d'outils React fournit une structure prédéfinie pour amorcer l'application. En outre, les développeurs sont libres d'utiliser leur propre structure de projet pour organiser le code.

Voyons comment créer une application React simple ou complexe.

- Application simple utilisant le CDN ;
- Application complexe utilisant React Create App cli ; 
- Application complexe utilisant une méthode personnalisée.

## Utilisation du bundler Rollup

Rollup est l'un des bundlers JavaScript petits et rapides. Dans ce chapitre, nous allons apprendre à utiliser le bundler Rollup.

Ouvrez un terminal et allez dans votre espace de travail.

```bash
cd /go/to/your/workspace
```

Ensuite, créez un dossier, expense-manager-rollup et déplacez-le dans le dossier nouvellement créé. Ouvrez également le dossier dans votre éditeur ou IDE préféré.

```bash
mkdir expense-manager-rollup 
cd expense-manager-rollup
```

Ensuite, il faut créer et initialiser le projet.

```bash
npm init -y
```

Ensuite, installez les bibliothèques React (react et react-dom).

```bash
npm install react@^17.0.0 react-dom@^17.0.0 --save
```

Ensuite, installez babel et ses bibliothèques prédéfinies comme dépendance de développement.

```bash
npm install @babel/preset-env @babel/preset-react 
@babel/core @babel/plugin-proposal-class-properties -D
```

Ensuite, installez rollup et ses bibliothèques de plugins comme dépendance de développement.

```bash
npm i -D rollup postcss@8.1 @rollup/plugin-babel 
@rollup/plugin-commonjs @rollup/plugin-node-resolve 
@rollup/plugin-replace rollup-plugin-livereload 
rollup-plugin-postcss rollup-plugin-serve postcss@8.1 
postcss-modules@4 rollup-plugin-postcss
```

Ensuite, installez corejs et le runtime regenerator pour la programmation asynchrone.

```bash
npm i regenerator-runtime core-js
```

Ensuite, créez un fichier de configuration babel, .babelrc sous le dossier racine pour configurer le compilateur babel.

```json
{
    "presets": [
        [
            "@babel/preset-env",
            {
                "useBuiltIns": "usage",
                "corejs": 3,
                "targets": "> 0.25%, not dead"
            }
        ],
        "@babel/preset-react"
    ],
    "plugins": [
        "@babel/plugin-proposal-class-properties"
    ]
}
```

Ensuite, créez un fichier rollup.config.js dans le dossier racine pour configurer le regroupeur de rollup.

```js
import babel from '@rollup/plugin-babel';
import resolve from '@rollup/plugin-node-resolve';
import commonjs from '@rollup/plugin-commonjs';
import replace from '@rollup/plugin-replace';
import serve from 'rollup-plugin-serve';
import livereload from 'rollup-plugin-livereload';
import postcss from 'rollup-plugin-postcss'

export default {
    input: 'src/index.js',
    output: {
        file: 'public/index.js',
        format: 'iife',
    },
    plugins: [
        commonjs({
            include: [
                'node_modules/**',
            ],
            exclude: [
                'node_modules/process-es6/**',
            ],
        }),
        resolve(),
        babel({
            exclude: 'node_modules/**'
        }),
        replace({
            'process.env.NODE_ENV': JSON.stringify('production'),
        }),
        postcss({
            autoModules: true
        }),
        livereload('public'),
        serve({
            contentBase: 'public',
            port: 3000,
            open: true,
        }), // index.html should be in root of project
    ]
}
```

Ensuite, mettez à jour le package.json et incluez notre point d'entrée (public/index.js et public/styles.css) et la commande pour construire et exécuter l'application.

```bash
...
"main": "public/index.js",
"style": "public/styles.css",
"files": [
    "public"
],
"scripts": {
    "start": "rollup -c -w",
    "build": "rollup"
},
...
```

Ensuite, créez un dossier src dans le répertoire racine de l'application, qui contiendra tout le code source de l'application.

Ensuite, créez un dossier, components sous src pour inclure nos composants React. L'idée est de créer deux fichiers, ```<component>.js``` pour écrire la logique du composant et ```<component.css>``` pour inclure les styles spécifiques au composant.

La structure finale de la demande sera la suivante :

```bash
|-- package-lock.json
|-- package.json
|-- rollup.config.js
|-- .babelrc
`-- public
    |-- index.html
`-- src
    |-- index.js
    `-- components
    |  |-- mycom.js
    |  |-- mycom.css
```

Créons un nouveau composant, HelloWorld, pour confirmer que notre installation fonctionne bien. Créez un fichier, HelloWorld.js dans le dossier components et écrivez un composant simple pour émettre un message Hello World.

```js
import React from "react";

class HelloWorld extends React.Component {
    render() {
        return (
            <div>
                <h1>Hello World!</h1>
            </div>
        );
    }
}
export default HelloWorld;
```

Ensuite, créez notre fichier principal, index.js sous le dossier src et appelez notre composant nouvellement créé.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import HelloWorld from './components/HelloWorld';

ReactDOM.render(
    <React.StrictMode>
        <HelloWorld />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, créez un dossier public dans le répertoire racine.

Ensuite, créez un fichier html, index.html (sous le dossier public*), qui sera notre point d'entrée dans l'application.

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Expense Manager :: Rollup version</title>
    </head>
    <body>
        <div id="root"></div>
        <script type="text/JavaScript" src="./index.js"></script>
    </body>
</html>
```

Ensuite, construisez et exécutez l'application.

```bash
npm start
```

La commande npm build exécutera le rollup et regroupera notre application dans un seul fichier, le fichier dist/index.js, et commencera à servir l'application. La commande dev recompilera le code chaque fois que le code source sera modifié et rechargera également les changements dans le navigateur.

```bash
> expense-manager-rollup@1.0.0 build /path/to/your/workspace/expense-manager-rollup 
> rollup -c 
rollup v2.36.1 
bundles src/index.js → dist\index.js... 
LiveReload enabled 
http://localhost:10001 -> /path/to/your/workspace/expense-manager-rollup/dist 
created dist\index.js in 4.7s 

waiting for changes...
```

## Utilisation du bundler Parcel

Parcel est un bundler rapide avec zéro configuration. Il n'attend que le point d'entrée de l'application et il résoudra lui-même les dépendances et regroupera l'application. Nous allons apprendre à utiliser le bundler Parcel dans ce chapitre.

Tout d'abord, installez le collecteur de colis.

```bash
npm install -g parcel-bundler
```

Ouvrez un terminal et allez dans votre espace de travail.

```bash
cd /go/to/your/workspace
```

Ensuite, créez un dossier, expense-manager-parcel et déplacez-le dans le dossier nouvellement créé. Ouvrez également le dossier dans votre éditeur ou IDE préféré.

```bash
mkdir expense-manager-parcel 
cd expense-manager-parcel
```

Ensuite, il faut créer et initialiser le projet.

```bash
npm init -y
```

Ensuite, installez les bibliothèques React (react et react-dom).

```bash
npm install react@^17.0.0 react-dom@^17.0.0 --save
```

Ensuite, installez babel et ses bibliothèques prédéfinies comme dépendance de développement.

```bash
npm install @babel/preset-env @babel/preset-react @babel/core @babel/plugin-proposal-class-properties -D
```

Ensuite, créez un fichier de configuration babel, .babelrc sous le dossier racine pour configurer le compilateur babel.

```json
{
    "presets": [
        "@babel/preset-env",
        "@babel/preset-react"
    ],
    "plugins": [
        "@babel/plugin-proposal-class-properties"
    ]
}
```

Ensuite, mettez à jour le package.json et incluez notre point d'entrée (src/index.js) et les commandes pour construire et exécuter l'application.

```bash
... 
"main": "src/index.js", 
"scripts": {
    "start": "parcel public/index.html",
    "build": "parcel build public/index.html --out-dir dist" 
},
...
```

Ensuite, créez un dossier src dans le répertoire racine de l'application, qui contiendra tout le code source de l'application.

Ensuite, créez un dossier, components sous src pour inclure nos composants React. L'idée est de créer deux fichiers, ```<component>.js``` pour écrire la logique du composant et ```<component.css>``` pour inclure les styles spécifiques au composant.

La structure finale de la demande sera la suivante :

```bash
|-- package-lock.json
|-- package.json
|-- .babelrc
`-- public
    |-- index.html
`-- src
    |-- index.js
    `-- components
    |  |-- mycom.js
    |  |-- mycom.css
```

Créons un nouveau composant, HelloWorld, pour confirmer que notre installation fonctionne bien. Créez un fichier, HelloWorld.js dans le dossier components et écrivez un composant simple pour émettre un message Hello World.

```js
import React from "react";

class HelloWorld extends React.Component {
    render() {
        return (
            <div>
                <h1>Hello World!</h1>
            </div>
        );
    }
}
export default HelloWorld;
```

Ensuite, créez notre fichier principal, index.js sous le dossier src et appelez notre composant nouvellement créé.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import HelloWorld from './components/HelloWorld';

ReactDOM.render(
    <React.StrictMode>
        <HelloWorld />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, créez un dossier public dans le répertoire racine.

Ensuite, créez un fichier html, index.html (dans le dossier public), qui sera notre point d'entrée dans l'application.

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Expense Manager :: Parcel version</title>
    </head>
    <body>
        <div id="root"></div>
        <script type="text/JavaScript" src="../src/index.js"></script>
    </body>
</html>
```

Ensuite, construisez et exécutez l'application.

```bash
npm start
```

La commande npm build exécutera la commande parcel. Elle regroupera et servira l'application à la volée. Il recompile chaque fois que le code source est modifié et recharge également les changements dans le navigateur.

```bash
> expense-manager-parcel@1.0.0 dev /go/to/your/workspace/expense-manager-parcel 
> parcel index.html Server running at http://localhost:1234 
√ Built in 10.41s.
```

Pour créer le bundle de production de l'application afin de la déployer sur le serveur de production, utilisez la commande build. Elle générera un fichier index.js avec tous les codes sources regroupés dans le dossier dist.

```bash
npm run build
> expense-manager-parcel@1.0.0 build /go/to/your/workspace/expense-manager-parcel
> parcel build index.html --out-dir dist

√  Built in 6.42s.

dist\src.80621d09.js.map    270.23 KB     79ms
dist\src.80621d09.js        131.49 KB    4.67s
dist\index.html                 221 B    1.63s
```
