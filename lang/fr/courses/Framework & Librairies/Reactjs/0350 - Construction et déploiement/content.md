## Introduction

Dans ce chapitre, nous allons apprendre comment construire et déployer une application React en production.

## Building

Une fois le développement d'une application React terminé, l'application doit être regroupée et déployée sur un serveur de production. Apprenons les commandes disponibles pour construire et déployer l'application dans ce chapitre.

Une seule commande suffit pour créer une version de production de l'application.

```bash
npm run build
> expense-manager@0.1.0 build path\to\expense-manager
> react-scripts build

Creating an optimized production build...
Compiled with warnings.

File sizes after gzip:

   41.69 KB   build\static\js\2.a164da11.chunk.js
    2.24 KB   build\static\js\main.de70a883.chunk.js
    1.4  KB   build\static\js\3.d8a9fc85.chunk.js
    1.17 KB   build\static\js\runtime-main.560bee6e.js
  493     B   build\static\css\main.e75e7bbe.chunk.css

The project was built assuming it is hosted at /.
You can control this with the homepage field in your package.json.

The build folder is ready to be deployed.
You may serve it with a static server:

   npm install -g serve
   serve -s build

Find out more about deployment here:

   https://cra.link/deployment
```

Une fois l'application construite, l'application est disponible dans le dossier build/static.

Par défaut, l'option de profilage est désactivée et peut être activée par l'option de ligne de commande -profile. L'option -profile permet d'inclure des informations de profilage dans le code. Les informations de profilage peuvent être utilisées avec React DevTools pour analyser l'application.

```bash
npm run build -- --profile
```

## Déploiement

Une fois l'application construite, elle peut être déployée sur n'importe quel serveur web. Nous allons apprendre comment déployer une application React dans ce chapitre.

### Déploiement local

Le déploiement local peut être fait en utilisant le paquet serve. Installons tout d'abord le paquet serve en utilisant la commande suivante.

```bash
npm install -g server
```

Pour démarrer l'application à l'aide de serve, utilisez la commande suivante -

```bash
cd /go/to/app/root/folder 
serve -s build
```

Par défaut, l'application est servie par le port 5000. L'application peut être consultée à l'adresse http://localhost:5000.

### Déploiement de la production

Le déploiement en production peut être facilement effectué en copiant les fichiers du dossier build/static dans le répertoire racine de l'application de production. Il fonctionnera sur tous les serveurs web, y compris Apache, IIS, Nginx, etc.

### Chemin relatif

Par défaut, le build de production est créé en supposant que l'application sera hébergée dans le dossier racine d'une application web. Si l'application doit être hébergée dans un sous-dossier, utilisez la configuration ci-dessous dans le package.json et construisez ensuite l'application.

```bash
{ ... "homepage": "http://domainname.com/path/to/subfolder", ... }
```