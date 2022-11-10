Node.js fonctionne en mode single-thread, mais il utilise un paradigme événementiel pour gérer la concurrence. Il facilite également la création de processus enfants afin de tirer parti du traitement parallèle sur les systèmes basés sur des CPU multi-cœurs.

Les processus enfants ont toujours trois flux child.stdin, child.stdout, et child.stderr qui peuvent être partagés avec les flux stdio du processus parent.

Node fournit le module child_process qui offre les trois principales façons suivantes de créer un processus enfant.

- **exec** - la méthode ```child_process.exec()``` exécute une commande dans un shell/console et met en mémoire tampon la sortie.
- **spawn** - La méthode ```child_process.spawn()``` lance un nouveau processus avec une commande donnée.
- **fork** - La méthode ```child_process.fork()``` est un cas particulier de la méthode spawn() pour créer des processus enfants.

## La méthode exec()

La méthode child_process.exec exécute une commande dans un shell et met en mémoire tampon la sortie. Elle a la signature suivante :

```js
child_process.exec(command[, options], callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **command** (String) La commande à exécuter, avec des arguments séparés par des espaces.
- **options** (Object) peut comprendre une ou plusieurs des options suivantes :
    - **cwd** (Chaîne) Répertoire de travail actuel du processus enfant
    - **env** (Objet) Paires clé-valeur de l'environnement
    - **encoding** (Chaîne) (Par défaut : 'utf8')
    - **shell** (Chaîne) Shell pour exécuter la commande (par défaut : '/bin/sh' sous UNIX, 'cmd.exe' sous Windows, Le shell doit comprendre le commutateur -c sous UNIX ou /s /c sous Windows. Sous Windows, l'analyse de la ligne de commande doit être compatible avec cmd.exe).
    - **timeout** (Nombre) (Défaut : 0)
    - **maxBuffer** (Nombre) (Défaut : 200*1024)
    - **killSignal** (Chaîne) (Défaut : 'SIGTERM')
    - **uid** (Nombre) Définit l'identité de l'utilisateur du processus.
    - **gid** (Nombre) Définit l'identité du groupe du processus.
- **callback** La fonction reçoit trois arguments error, stdout, et stderr qui sont appelés avec la sortie lorsque le processus se termine.

La méthode ```exec()``` renvoie un tampon avec une taille maximale et attend que le processus se termine pour essayer de renvoyer toutes les données mises en tampon en une seule fois.

### Exemple

Créons deux fichiers js nommés support.js et master.js :

Fichier : support.js

```js
console.log("Child Process " + process.argv[2] + " executed." );
```

Fichier : master.js

```js
const fs = require('fs');
const child_process = require('child_process');

for(var i=0; i<3; i++) {
    var workerProcess = child_process.exec('node support.js '+i,function 
        (error, stdout, stderr) {
        
        if (error) {
            console.log(error.stack);
            console.log('Error code: '+error.code);
            console.log('Signal received: '+error.signal);
        }
        console.log('stdout: ' + stdout);
        console.log('stderr: ' + stderr);
    });

    workerProcess.on('exit', function (code) {
        console.log('Child process exited with exit code '+code);
    });
}
```

Maintenant, exécutez le master.js pour voir le résultat :

```bash
$ node master.js
```

Vérifier la sortie. Le serveur a démarré.

```bash
Child process exited with exit code 0
stdout: Child Process 1 executed.

stderr:
Child process exited with exit code 0
stdout: Child Process 0 executed.

stderr:
Child process exited with exit code 0
stdout: Child Process 2 executed.
```

## La méthode spawn()

La méthode ```child_process.spawn()``` lance un nouveau processus avec une commande donnée. Elle a la signature suivante :

```bash
child_process.spawn(command[, args][, options])
```

### Paramètres

Voici la description des paramètres utilisés :

- **command** (String) La commande à exécuter
- **args** (Tableau) Liste des arguments de type chaîne de caractères
- **options** (Object) peut comprendre une ou plusieurs des options suivantes -
    - **cwd** (Chaîne) Répertoire de travail actuel du processus enfant.
    - **env** (Object) Paires clé-valeur de l'environnement.
    - **stdio** (Array) Chaîne Configuration stdio de l'enfant.
    - **customFds** (Tableau) Déprécié Descripteurs de fichiers à utiliser par l'enfant pour stdio.
    - **detached** (Booléen) L'enfant sera un chef de groupe de processus.
    - **uid** (Nombre) Définit l'identité de l'utilisateur du processus.
    - **gid** (Nombre) Définit l'identité du groupe du processus.

La méthode ```spawn()``` renvoie des flux (stdout & stderr) et elle doit être utilisée lorsque le processus renvoie une quantité importante de données. spawn() commence à recevoir la réponse dès que le processus commence à s'exécuter.

### Exemple

Créez deux fichiers js nommés support.js et master.js :


Fichier : support.js

```js
console.log("Child Process " + process.argv[2] + " executed." );
```

Fichier : master.js

```js
const fs = require('fs');
const child_process = require('child_process');

for(var i = 0; i<3; i++) {
    var workerProcess = child_process.spawn('node', ['support.js', i]);

    workerProcess.stdout.on('data', function (data) {
        console.log('stdout: ' + data);
    });

    workerProcess.stderr.on('data', function (data) {
        console.log('stderr: ' + data);
    });

    workerProcess.on('close', function (code) {
        console.log('child process exited with code ' + code);
    });
}
```

Maintenant, exécutez le master.js pour voir le résultat :

```bash
$ node master.js
```

Vérifier la sortie. Le serveur a démarré

```bash
stdout: Child Process 0 executed.

child process exited with code 0
stdout: Child Process 1 executed.

stdout: Child Process 2 executed.

child process exited with code 0
child process exited with code 0
```

## La méthode fork()

La méthode ```child_process.fork()``` est un cas spécial de ```spawn()``` pour créer des processus Node. Elle a la signature suivante :

```js
child_process.fork(modulePath[, args][, options])
```

### Paramètres

Voici la description des paramètres utilisés :

- **modulePath** (String) Le module à exécuter dans l'enfant.
- **args** (Tableau) Liste d'arguments de type chaîne de caractères
    - **options** (Object) peut comprendre une ou plusieurs des options suivantes -
    - **cwd** (Chaîne) Répertoire de travail actuel du processus enfant.
    - **env** (Object) Paires clé-valeur de l'environnement.
    - **execPath** (Chaîne) Exécutable utilisé pour créer le processus enfant.
    - **execArgv** (Tableau) Liste des arguments de chaîne passés à l'exécutable (par défaut : process.execArgv).
    - **silent** (Booléen) Si true, stdin, stdout, et stderr de l'enfant seront transmis au parent, sinon ils seront hérités du parent, voir les options "pipe" et "inherit" pour le stdio de spawn() pour plus de détails (false par défaut).
    - **uid** (Nombre) Définit l'identité de l'utilisateur du processus.
    - **gid** (Nombre) Définit l'identité du groupe du processus.

La méthode ```fork()``` renvoie un objet avec un canal de communication intégré en plus d'avoir toutes les méthodes d'une instance ChildProcess normale.

### Exemple

Créez deux fichiers js nommés support.js et master.js :

Fichier : support.js

```js
console.log("Child Process " + process.argv[2] + " executed." );
```

Fichier : master.js

```js
const fs = require('fs');
const child_process = require('child_process');

for(var i=0; i<3; i++) {
    var worker_process = child_process.fork("support.js", [i]);	

    worker_process.on('close', function (code) {
        console.log('child process exited with code ' + code);
    });
}
```

Maintenant, exécutez le master.js pour voir le résultat :

```bash
$ node master.js
```

Vérifier la sortie. Le serveur a démarré.

```bash
Child Process 0 executed.
Child Process 1 executed.
Child Process 2 executed.
child process exited with code 0
child process exited with code 0
child process exited with code 0
```