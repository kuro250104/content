## Introduction

Dans ce chapitre, nous allons apprendre les commandes de base disponibles dans l'application en ligne de commande Create React App.

## Créer une nouvelle application

Create React App propose plusieurs façons de créer une application React.

Utilisation du script npx.

```bash
npx create-react-app <react-app-name>
npx create-react-app hello-react-app
```

Utilisation du gestionnaire de paquets npm.

```bash
npm init react-app <react-app-name>
npm init react-app hello-react-app
```

Utilisation du gestionnaire de paquets yarn.

```bash
yarn init react-app <react-app-name>
yarn init react-app hello-react-app
```

## Sélection d'un modèle

Create React App crée une application React en utilisant le modèle par défaut. Le modèle fait référence au code initial avec certaines fonctionnalités intégrées. Il y a des centaines de modèles avec de nombreuses fonctionnalités avancées qui sont disponibles dans le serveur de paquets npm. Create React App permet aux utilisateurs de sélectionner le modèle par le biais du commutateur de ligne de commande -template.

```bash
create-react-app my-app --template typescript
```

La commande ci-dessus va créer une application react en utilisant le paquet cra-template-typescript du serveur npm.

## Installation d'une dépendance

Le paquet de dépendances React peut être installé en utilisant la commande normale npm ou yarn package car React utilise la structure de projet recommandée par npm et yarn.

Utilisation du gestionnaire de paquets npm.

```bash
npm install --save react-router-dom
```

Utilisation du gestionnaire de paquets yarn.

```bash
yarn add react-router-dom
```

## Running the application

L'application React peut être lancée à l'aide de la commande npm ou yarn, selon le gestionnaire de paquets utilisé dans le projet.

Utilisation du gestionnaire de paquets npm.

```bash
npm start
```

Utilisation du gestionnaire de paquets yarn.

```bash
yarn start
```

Pour exécuter l'application en mode sécurisé (HTTPS), définissez une variable d'environnement, HTTPS, et attribuez-lui la valeur true avant de démarrer l'application. Par exemple, dans l'invite de commande de Windows (cmd.exe), la commande ci-dessous définit HTTPS et lance l'application en mode HTTPS.

```bash
set HTTPS=true && npm start
```