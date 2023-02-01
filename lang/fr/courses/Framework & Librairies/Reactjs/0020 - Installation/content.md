## Introduction

Ce chapitre explique l'installation de la bibliothèque React et de ses outils connexes dans votre machine. Avant de passer à l'installation, vérifions d'abord les prérequis.

React fournit des outils CLI pour le développeur afin d'accélérer la création, le développement et le déploiement de l'application web basée sur React. Les outils React CLI dépendent de Node.js et doivent être installés sur votre système. Avec un peu de chance, vous avez installé Node.js sur votre machine. Nous pouvons le vérifier en utilisant la commande ci-dessous :

```bash
node --version
```

Vous pouvez voir la version de Nodejs que vous avez installé. Elle est affichée comme ci-dessous pour moi,

```bash
v19.1.0
```

Si Nodejs n'est pas installé, vous pouvez le télécharger et l'installer en visitant <a href="https://nodejs.org/en/download/" title="Télécharger Nodejs" target="_blank">https://nodejs.org/en/download/</a>.

## Toolchain

Pour développer des fonctionnalités légères telles que la validation de formulaire, le dialogue de modèle, etc., la bibliothèque React peut être directement incluse dans l'application web via le réseau de diffusion de contenu (CDN). C'est similaire à l'utilisation de la bibliothèque jQuery dans une application web. Pour les applications de taille moyenne à grande, il est conseillé d'écrire l'application sous forme de plusieurs fichiers, puis d'utiliser des bundlers tels que webpack, parcel, rollup, etc. pour compiler et regrouper l'application avant de déployer le code.

React toolchain aide à créer, construire, exécuter et déployer l'application React. React toolchain fournit essentiellement un modèle de projet de démarrage avec tout le code nécessaire pour amorcer l'application.

Parmi les chaînes d'outils les plus populaires pour développer des applications React figurent :

- **Create React App** − Chaîne d'outils orientée SPA.
- **Next.js** − Chaîne d'outils orientée vers le rendu côté serveur.
- **Gatsby** − Chaîne d'outils orientée contenu statique.

Les outils nécessaires pour développer une application React sont :

- Le *serve*, un serveur statique pour servir notre application pendant le développement.
- Compilateur Babel.
- Créer une application React CLI.

Dans ce cours, nous allons apprendre les bases des outils mentionnés ci-dessus et comment les installer.

## Le serveur statique de service

Le serveur *serve* est un serveur web léger. Il sert les sites statiques et les applications à page unique. Il se charge rapidement et consomme un minimum de mémoire. Il peut être utilisé pour servir une application React. Installons l'outil en utilisant le gestionnaire de paquets npm dans notre système.

```bash
npm install serve -g
```

Créons un site statique simple et servons l'application en utilisant serve app.

Ouvrez une invite de commande et allez dans votre espace de travail.

```bash
cd /go/to/your/workspace
```

Créez un nouveau dossier, static_site et changez de répertoire pour le dossier nouvellement créé.

```bash
mkdir static_site 
cd static_site
```

Ensuite, créez une page web simple dans le dossier en utilisant votre éditeur html préféré.

```html
<!DOCTYPE html> 
<html> 
    <head>
        <meta charset="UTF-8" /> 
        <title>Static website</title> 
    </head> 
    <body> 
        <div><h1>Hello!</h1></div> 
    </body> 
</html>
```

Ensuite, exécutez la commande serve.

```bash
serve .
```

Nous pouvons également servir un seul fichier, index.html, au lieu du dossier entier.

```bash
serve ./index.html
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:5000``` dans la barre d'adresse et appuyez sur entrée. L'application devrait s'ouvrir en affichant le message "Hello!".

Le serveur va servir l'application en utilisant le port par défaut, 5000. S'il n'est pas disponible, il choisira un port aléatoire et le spécifiera.

```bash
│ Serving!                                     │   
│                                              │ 
│ - Local: http://localhost:57311              │ 
│ - On Your Network: http://192.168.56.1:57311 │ 
│                                              │ 
│ This port was picked because 5000 is in use. │ 
│                                              │ 
│ Copied local address to clipboard!
```

## Compilateur Babel

Babel est un compilateur JavaScript qui compile de nombreuses variantes (es2015, es6, etc.,) de JavaScript en code JavaScript standard supporté par tous les navigateurs. React utilise JSX, une extension de JavaScript pour concevoir le code de l'interface utilisateur. Babel est utilisé pour compiler le code JSX en code JavaScript.

Pour installer Babel et son compagnon React, exécutez la commande suivante :

```bash
npm install babel-cli@6 babel-preset-react-app@3 -g
... 
... 
+ babel-cli@6.26.0 
+ babel-preset-react-app@3.1.2 
updated 2 packages in 8.685s
```

Babel nous aide à écrire notre application dans la prochaine génération de syntaxe JavaScript avancée.

## Create React App toolchain

Create React App est un outil CLI moderne pour créer une application React à page unique. Il s'agit de l'outil standard soutenu par la communauté React. Il gère également le compilateur Babel. Installons Create React App dans notre système local.

```bash
> npm install -g create-react-app
+ create-react-app@4.0.1 
added 6 packages from 4 contributors, removed 37 packages and updated 12 packages in 4.693s
```

### Updating the toolchain

La chaîne d'outils React Create App utilise le paquet react-scripts pour construire et exécuter l'application. Une fois que nous avons commencé à travailler sur l'application, nous pouvons mettre à jour le react-script à la dernière version à tout moment en utilisant le gestionnaire de paquets npm.

```bash
npm install react-scripts@latest
```

### Avantages de l'utilisation de la chaîne d'outils React

React toolchain offre de nombreuses fonctionnalités prêtes à l'emploi. Voici quelques-uns des avantages de l'utilisation de la chaîne d'outils React.

- Structure prédéfinie et standard de l'application.
- Modèle de projet prêt à l'emploi pour différents types d'applications.
- Le serveur web de développement est inclus.
- Un moyen simple d'inclure des composants React tiers.
- Configuration par défaut pour tester l'application.
