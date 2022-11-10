## Configuration de l'environnement local

Si vous êtes prêt à configurer votre environnement pour Node.js, vous avez besoin des deux logiciels suivants disponibles sur votre ordinateur, (a) un éditeur de texte et (b) les installables binaires de Node.js.

## Éditeur de texte

Il sera utilisé pour taper votre programme. Parmi les exemples de quelques éditeurs, citons le Bloc-notes de Windows, la commande Edit de l'OS, Brief, Epsilon, EMACS, et vim ou vi.

Le nom et la version de l'éditeur de texte peuvent varier selon le système d'exploitation. Par exemple, le Bloc-notes sera utilisé sur Windows, et vim ou vi peuvent être utilisés aussi bien sur Windows que sur Linux ou UNIX.

Les fichiers que vous créez avec votre éditeur sont appelés fichiers sources et contiennent le code source du programme. Les fichiers sources des programmes Node.js sont généralement nommés avec l'extension ".js".

Avant de commencer votre programmation, assurez-vous que vous disposez d'un éditeur de texte et que vous avez suffisamment d'expérience pour écrire un programme informatique, l'enregistrer dans un fichier et enfin l'exécuter.

## Le moteur d'exécution Node.js

Le code source écrit dans le fichier source est simplement du javascript. L'interpréteur Node.js sera utilisé pour interpréter et exécuter votre code javascript.

La distribution Node.js se présente sous la forme d'un binaire installable pour SunOS, Linux, Mac OS X et les systèmes d'exploitation Windows avec les architectures de processeur x86 32-bit (386) et 64-bit (amd64).

La section suivante vous guide sur la façon d'installer la distribution binaire Node.js sur différents systèmes d'exploitation.

## Télécharger l'archive Node.js

Téléchargez la dernière version du fichier d'archive installable de Node.js depuis le site officiel. Vous y trouverez également toutes les informations nécessaires à l’installation.

## Vérifier l'installation : Exécution d'un fichier

Créez un fichier js nommé main.js sur votre machine (Windows ou Linux) ayant le code suivant.

```js
/* Hello, World! program in node.js */
console.log("Hello, World!")
```

Maintenant exécutez le fichier main.js en utilisant l'interpréteur Node.js pour voir le résultat -

```bash
$ node main.js
```

Si tout se passe bien dans votre installation, le résultat devrait être le suivant :

```bash
Hello, World!
```