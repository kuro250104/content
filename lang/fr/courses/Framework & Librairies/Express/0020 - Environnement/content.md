Dans ce chapitre, nous allons apprendre comment commencer à développer et à utiliser l'Express Framework. Pour commencer, vous devez avoir installé Node et npm (node package manager). Si vous ne les avez pas encore, allez à la configuration de Node pour installer node sur votre système local. Confirmez que node et npm sont installés en exécutant les commandes suivantes dans votre terminal.

```bash
node --version
npm --version
```

Vous devriez obtenir un résultat similaire à celui qui suit.

```bash
v5.0.0
3.5.2
```

Maintenant que nous avons mis en place Node et npm, comprenons ce qu'est npm et comment l'utiliser.

## Node Package Manager(npm)

npm est le gestionnaire de paquets pour Node. Le registre npm est une collection publique de paquets de code open-source pour Node.js, les applications web frontales, les applications mobiles, les robots, les routeurs et d'innombrables autres besoins de la communauté JavaScript. npm nous permet d'accéder à tous ces paquets et de les installer localement. Vous pouvez parcourir la liste des paquets disponibles sur npm à l'adresse npmJS.

### Comment utiliser npm ?

Il existe deux façons d'installer un paquet à l'aide de npm : globalement et localement.

Globally − Cette méthode est généralement utilisée pour installer des outils de développement et des paquets basés sur l'interface CLI. Pour installer un paquet de manière globale, utilisez le code suivant.

```bash
npm install -g <package-name>
```

Locally − Cette méthode est généralement utilisée pour installer des frameworks et des bibliothèques. Un paquetage installé localement ne peut être utilisé que dans le répertoire où il est installé. Pour installer un paquetage localement, utilisez la même commande que ci-dessus sans l'option -g.

```bash
npm install <package-name>
```

Chaque fois que nous créons un projet à l'aide de npm, nous devons fournir un fichier package.json, qui contient tous les détails de notre projet. npm nous permet de configurer facilement ce fichier. Configurons notre projet de développement.

- **Étape 1** - Lancez votre terminal/cmd, créez un nouveau dossier nommé hello-world et cd (créer un répertoire) dans celui-ci.
- **Étape 2** - Maintenant pour créer le fichier package.json en utilisant npm, utilisez le code suivant.

```bash
npm init
```

Continuez à appuyer sur la touche "Entrée" et saisissez votre nom dans le champ "Nom de l'auteur".

- **Étape 3** − Maintenant que notre fichier package.json est configuré, nous allons installer Express. Pour installer Express et l'ajouter à notre fichier package.json, utilisez la commande suivante -

```bash
npm install --save express
```

Pour confirmer qu'Express a été installé correctement, exécutez le code suivant.

```bash
ls node_modules #(dir node_modules for windows)
```

__Remarque__ - L'indicateur --save peut être remplacé par l'indicateur -S. Ce drapeau garantit qu'Express est ajouté comme dépendance à notre fichier package.json. Ceci a un avantage, la prochaine fois que nous devons installer toutes les dépendances de notre projet, nous pouvons simplement exécuter la commande npm install et il trouvera les dépendances dans ce fichier et les installera pour nous.
C'est tout ce dont nous avons besoin pour commencer à développer en utilisant le framework Express. Pour faciliter notre processus de développement, nous allons installer un outil de npm, nodemon. Cet outil redémarre notre serveur dès que nous apportons une modification à l'un de nos fichiers, sinon nous devons redémarrer le serveur manuellement après chaque modification de fichier. Pour installer nodemon, utilisez la commande suivante -

```bash
npm install -g nodemon
```

Vous pouvez maintenant commencer à travailler sur Express.