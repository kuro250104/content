JXcore, qui est un projet open source, introduit une fonctionnalité unique pour l'empaquetage et le cryptage des fichiers sources et autres actifs dans les paquets JX.

Considérez que vous avez un grand projet composé de nombreux fichiers. JXcore peut les empaqueter tous dans un seul fichier pour simplifier la distribution. Ce chapitre fournit un aperçu rapide de l'ensemble du processus à partir de l'installation de JXcore.

## Installation de JXcore

L'installation de JXcore est assez simple. Nous avons fourni ici des instructions étape par étape sur la façon d'installer JXcore sur votre système. Suivez les étapes indiquées ci-dessous :

### Étape 1

Téléchargez le paquet JXcore à partir de <a href="https://github.com/jxcore/jxcore" title="paquet JXcore" target="_blank">https://github.com/jxcore/jxcore</a>, selon votre système d'exploitation et l'architecture de votre machine. Nous avons téléchargé un paquet pour Cenots fonctionnant sur une machine 64 bits.

```bash
$ wget https://s3.amazonaws.com/nodejx/jx_rh64.zip
```

### Étape 2

Décompressez le fichier téléchargé jx_rh64.zip et copiez le binaire jx dans /usr/bin ou dans tout autre répertoire en fonction de la configuration de votre système.

```bash
$ unzip jx_rh64.zip
$ cp jx_rh64/jx /usr/bin
```

### Étape 3

Définissez votre variable PATH de manière appropriée pour exécuter jx à partir de n'importe quel endroit.

```bash
$ export PATH=$PATH:/usr/bin
```

### Étape 4

Vous pouvez vérifier votre installation en lançant une simple commande comme indiqué ci-dessous. Vous devriez constater qu'il fonctionne et qu'il affiche son numéro de version comme suit :

```bash
$ jx --version
v0.10.32
```

## Emballage du code

Considérons que vous avez un projet avec les répertoires suivants où vous avez conservé tous vos fichiers, y compris Node.js, le fichier principal, index.js, et tous les modules installés localement.

```bash
drwxr-xr-x  2 root root  4096 Nov 13 12:42 images
-rwxr-xr-x  1 root root 30457 Mar  6 12:19 index.htm
-rwxr-xr-x  1 root root 30452 Mar  1 12:54 index.js
drwxr-xr-x 23 root root  4096 Jan 15 03:48 node_modules
drwxr-xr-x  2 root root  4096 Mar 21 06:10 scripts
drwxr-xr-x  2 root root  4096 Feb 15 11:56 style
```

Pour empaqueter le projet ci-dessus, il vous suffit d'aller dans ce répertoire et de lancer la commande jx suivante. En supposant que le fichier index.js est le fichier d'entrée de votre projet Node.js :

```bash
$ jx package index.js index
```

Ici, vous auriez pu utiliser n'importe quel autre nom de paquet au lieu de index. Nous avons utilisé index parce que nous voulions garder le nom de notre fichier principal comme index.jx. Cependant, la commande ci-dessus empaquettera tout et créera les deux fichiers suivants :

- **index.jxp** Il s'agit d'un fichier intermédiaire qui contient tous les détails du projet nécessaires à la compilation du projet.
- **index.jx** Il s'agit du fichier binaire contenant le paquetage complet qui est prêt à être envoyé à votre client ou à votre environnement de production.

## Lancement du fichier JX

Considérons que votre projet Node.js original s'exécutait comme suit :

```bash
$ node index.js command_line_arguments
```

Après avoir compilé votre paquet en utilisant JXcore, il peut être démarré comme suit :

```bash
$ jx index.jx command_line_arguments
```

Pour en savoir plus sur JXcore, vous pouvez consulter son site officiel.