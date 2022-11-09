Voyons maintenant comment installer MongoDB sur Windows.

## Installer MongoDB sous Windows

Pour installer MongoDB sous Windows, téléchargez d'abord la dernière version de MongoDB depuis <a href="https://www.mongodb.com/download-center" title="centre de téléchargement de mongodb" target="_blank">https://www.mongodb.com/download-center</a>.

Entrez les détails requis, sélectionnez l'onglet Serveur, dans lequel vous pouvez choisir la version de MongoDB, le système d'exploitation et, le conditionnement comme :

Installez maintenant le fichier téléchargé, par défaut, il sera installé dans le dossier ```C:\Program Files\```.

MongoDB a besoin d'un dossier de données pour stocker ses fichiers. L'emplacement par défaut du répertoire de données MongoDB est ```c:\data\db```. Vous devez donc créer ce dossier à l'aide de l'Invite de commande. Exécutez la séquence de commandes suivante.

```bash
C:\>md data
C:\md data\db
```

Ensuite, vous devez spécifier l'emplacement du **dbpath** dans le répertoire créé dans ```mongod.exe```. Pour ce faire, exécutez les commandes suivantes.

Dans l'invite de commande, naviguez jusqu'au répertoire bin présent dans le dossier d'installation de MongoDB. Supposons que mon dossier d'installation soit ```C:\Program Files\MongoDB```

```bash
C:\Users\XYZ>d:cd C:\Program Files\MongoDB\Server\4.2\bin
C:\Program Files\MongoDB\Server\4.2\bin>mongod.exe --dbpath "C:\data"
```

Cela montrera le **message d'attente de connexions** sur la sortie de la console, ce qui indique que le processus mongod.exe s'exécute avec succès.
Maintenant, pour exécuter MongoDB, vous devez ouvrir une autre invite de commande et lancer la commande suivante.

```bash
C:\Program Files\MongoDB\Server\4.2\bin>mongo.exe
MongoDB shell version v4.2.1
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("4260beda-f662-4cbe-9bc7-5c1f2242663c") }
MongoDB server version: 4.2.1
>
```

Cela montrera que MongoDB est installé et exécuté avec succès. La prochaine fois que vous lancerez MongoDB, vous ne devrez émettre que des commandes.

```bash
C:\Program Files\MongoDB\Server\4.2\bin>mongod.exe --dbpath "C:\data"
C:\Program Files\MongoDB\Server\4.2\bin>mongo.exe
```

## Installer MongoDB sur Ubuntu

Exécutez la commande suivante pour importer la clé GPG publique de MongoDB -.

```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
```

Créez un fichier ```/etc/apt/sources.list.d/mongodb.list``` en utilisant la commande suivante.

```bash
echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' 
    | sudo tee /etc/apt/sources.list.d/mongodb.list
```

Maintenant, émettez la commande suivante pour mettre à jour le dépôt -

```bash
sudo apt-get update
```

Ensuite, installez MongoDB à l'aide de la commande suivante -

```bash
apt-get install mongodb-10gen = 4.2
```

Dans l'installation ci-dessus, la version 2.2.3 est la version actuelle de MongoDB. Veillez à toujours installer la dernière version. Maintenant MongoDB est installé avec succès.

## Start MongoDB

```bash
sudo service mongodb start
```

## Arrêter MongoDB

```bash
sudo service mongodb stop
```

## Redémarrer MongoDB

```bash
sudo service mongodb restart
```

To use MongoDB run the following command.

```bash
mongo
```

Cela vous connectera à l'instance MongoDB en cours d'exécution.

## Aide sur MongoDB

Pour obtenir une liste de commandes, tapez ```db.help()``` dans le client MongoDB.

## Statistiques MongoDB

Pour obtenir des statistiques sur le serveur MongoDB, tapez la commande db.stats() dans le client MongoDB. Cette commande affichera le nom de la base de données, le nombre de collections et de documents dans la base de données.