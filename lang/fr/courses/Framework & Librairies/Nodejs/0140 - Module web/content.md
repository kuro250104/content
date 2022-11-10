## Qu'est-ce qu'un serveur Web ?

Un serveur Web est une application logicielle qui traite les demandes HTTP envoyées par le client HTTP, comme les navigateurs Web, et renvoie des pages Web en réponse aux clients. Les serveurs Web fournissent généralement des documents html accompagnés d'images, de feuilles de style et de scripts.

La plupart des serveurs Web prennent en charge les scripts côté serveur, en utilisant des langages de script ou en redirigeant la tâche vers un serveur d'application qui récupère les données d'une base de données et exécute une logique complexe, puis envoie un résultat au client HTTP par le biais du serveur Web.

Le serveur web Apache est l'un des serveurs web les plus couramment utilisés. Il s'agit d'un projet open source.

## Architecture des applications Web

Une application Web est généralement divisée en quatre couches :

- **Client** - Cette couche est constituée de navigateurs Web, de navigateurs mobiles ou d'applications qui peuvent faire des demandes HTTP au serveur Web.
- **Serveur** - Cette couche contient le serveur Web qui peut intercepter les demandes faites par les clients et leur transmettre la réponse.
- **Business** - Cette couche contient le serveur d'application qui est utilisé par le serveur Web pour effectuer le traitement requis. Cette couche interagit avec la couche de données via la base de données ou certains programmes externes.
- **Données** - Cette couche contient les bases de données ou toute autre source de données.

## Création d'un serveur Web à l'aide de Node

Node.js fournit un module http qui peut être utilisé pour créer un client HTTP d'un serveur. Voici la structure minimale d'un serveur HTTP qui écoute sur le port 8081.

