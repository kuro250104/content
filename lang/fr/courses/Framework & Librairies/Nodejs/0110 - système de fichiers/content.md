Node implémente les E/S de fichiers en utilisant des enveloppes simples autour des fonctions POSIX standard. Le module File System (fs) de Node peut être importé en utilisant la syntaxe suivante :

```js
var fs = require("fs")
```

## Synchrone vs Asynchrone

Chaque méthode du module fs a des formes synchrones et asynchrones. Les méthodes asynchrones prennent le dernier paramètre comme rappel de la fonction d'achèvement et le premier paramètre de la fonction de rappel comme erreur. Il est préférable d'utiliser une méthode asynchrone plutôt qu'une méthode synchrone, car la première ne bloque jamais un programme pendant son exécution, alors que la seconde le fait.

### Exemple

Créez un fichier texte nommé input.txt avec le contenu suivant :

```bash
Microlead, le chemin vers le succès !!!!!
```

Créons un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");

// Asynchronous read
fs.readFile('input.txt', function (err, data) {
    if (err) {
        return console.error(err);
    }
    console.log("Asynchronous read: " + data.toString());
});

// Synchronous read
var data = fs.readFileSync('input.txt');
console.log("Synchronous read: " + data.toString());

console.log("Program Ended");
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Synchronous read: Microlead, le chemin vers le succès !!!!!

Program Ended
Asynchronous read: Microlead, le chemin vers le succès !!!!!
```

Les sections suivantes de ce chapitre fournissent un ensemble de bons exemples sur les principales méthodes d'E/S de fichiers.

## Ouvrir un fichier

### Syntaxe

Voici la syntaxe de la méthode d'ouverture d'un fichier en mode asynchrone :

```js
fs.open(path, flags[, mode], callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **path** - Il s'agit de la chaîne de caractères contenant le nom du fichier et le chemin d'accès.
- **flags** - Les drapeaux indiquent le comportement du fichier à ouvrir. Toutes les valeurs possibles ont été mentionnées ci-dessous.
- **mode** - Il définit le mode du fichier (permission et sticky bits), mais seulement si le fichier a été créé. La valeur par défaut est 0666, lisible et inscriptible.
- **callback** - C'est la fonction de rappel qui reçoit deux arguments (err, fd).

## Drapeaux

**Drapeau et description :**

- **r** : Ouvre le fichier pour la lecture. Une exception se produit si le fichier n'existe pas.
- **r+** : Ouvre le fichier pour la lecture et l'écriture. Une exception se produit si le fichier n'existe pas.
- **rs** : Ouvre le fichier en lecture en mode synchrone.
- **rs+** : Ouvre le fichier en lecture et en écriture, en demandant au système d'exploitation de l'ouvrir en mode synchrone. Voir les notes concernant 'rs' pour l'utiliser avec précaution.
- **w** : Ouvrir un fichier en écriture. Le fichier est créé (s'il n'existe pas) ou tronqué (s'il existe).
- **wx** : Comme 'w' mais échoue si le chemin existe.
- **w+** : Ouvre un fichier en lecture et en écriture. Le fichier est créé (s'il n'existe pas) ou tronqué (s'il existe).
- **wx+** : Comme 'w+' mais échoue si le chemin existe.
- **a** : Ouvre le fichier pour l'ajouter. Le fichier est créé s'il n'existe pas.
- **ax** : Comme 'a' mais échoue si le chemin existe.
- **a+** : Ouvre le fichier pour la lecture et l'ajout. Le fichier est créé s'il n'existe pas.
- **ax+** : Comme 'a+' mais échoue si le chemin d'accès existe.

### Exemple

Créons un fichier js nommé main.js contenant le code suivant pour ouvrir un fichier input.txt en lecture et en écriture.

```js
var fs = require("fs");

// Asynchronous - Opening File
console.log("Going to open file!");
fs.open('input.txt', 'r+', function(err, fd) {
    if (err) {
        return console.error(err);
    }
    console.log("File opened successfully!");     
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to open file!
File opened successfully!
```

## Obtenir des informations sur le fichier

### Syntaxe

Voici la syntaxe de la méthode permettant d'obtenir les informations sur un fichier :

```js
fs.stat(path, callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **path** - C'est la chaîne de caractères contenant le nom du fichier, y compris le chemin.
- **callback** - C'est la fonction callback qui reçoit deux arguments (err, stats) où stats est un objet de type fs.Stats qui est imprimé ci-dessous dans l'exemple.

En dehors des attributs importants qui sont imprimés ci-dessous dans l'exemple, il existe plusieurs méthodes utiles disponibles dans la classe ```fs.Stats``` qui peuvent être utilisées pour vérifier le type de fichier. Ces méthodes sont indiquées dans le tableau suivant.

### Méthode et description

- ```stats.isFile()``` : Renvoie un message si le type de fichier est un fichier simple.
- ```stats.isDirectory()``` : Renvoie un message si le type de fichier est un répertoire.
- ```stats.isBlockDevice()``` : Renvoie un message si le type de fichier est un périphérique de bloc.
- ```stats.isCharacterDevice()``` : Renvoie un message vrai si le type de fichier est un périphérique de type caractère.
- ```stats.isSymbolicLink()``` : Renvoie un message si le type de fichier est un lien symbolique.
- ```stats.isFIFO()``` : Renvoie un message si le type de fichier est un FIFO.
- ```stats.isSocket()``` : Renvoie un message si le fichier est de type asocket.

### Exemple

Créons un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");

console.log("Going to get file info!");
fs.stat('input.txt', function (err, stats) {
    if (err) {
        return console.error(err);
    }
    console.log(stats);
    console.log("Got file info successfully!");
    
    // Check file type
    console.log("isFile ? " + stats.isFile());
    console.log("isDirectory ? " + stats.isDirectory());    
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to get file info!
{ 
   dev: 1792,
   mode: 33188,
   nlink: 1,
   uid: 48,
   gid: 48,
   rdev: 0,
   blksize: 4096,
   ino: 4318127,
   size: 97,
   blocks: 8,
   atime: Sun Mar 22 2015 13:40:00 GMT-0500 (CDT),
   mtime: Sun Mar 22 2015 13:40:57 GMT-0500 (CDT),
   ctime: Sun Mar 22 2015 13:40:57 GMT-0500 (CDT) 
}
Got file info successfully!
isFile ? true
isDirectory ? false
```

Écriture d'un fichier

### Syntaxe

Voici la syntaxe de l'une des méthodes d'écriture dans un fichier :

```js
fs.writeFile(filename, data[, options], callback)
```

Cette méthode écrase le fichier si celui-ci existe déjà. Si vous voulez écrire dans un fichier existant, vous devez utiliser une autre méthode disponible.

### Paramètres

Voici la description des paramètres utilisés :

- **path** - Il s'agit de la chaîne contenant le nom du fichier, y compris le chemin.
- **data** - C'est la chaîne ou le tampon à écrire dans le fichier.
- **options** - Le troisième paramètre est un objet qui contient {encoding, mode, flag}. Par défaut, l'encodage est utf8, le mode est la valeur octale 0666 et le drapeau est 'w'.
- **callback** - C'est la fonction de rappel qui reçoit un seul paramètre err qui renvoie une erreur en cas d'erreur d'écriture.

### Exemple

Créons un fichier js nommé main.js ayant le code suivant :

```js
var fs = require("fs");

console.log("Going to write into existing file");
fs.writeFile('input.txt', 'Microlead', function(err) {
    if (err) {
        return console.error(err);
    }
    
    console.log("Data written successfully!");
    console.log("Let's read newly written data");
    
    fs.readFile('input.txt', function (err, data) {
        if (err) {
            return console.error(err);
        }
        console.log("Asynchronous read: " + data.toString());
    });
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to write into existing file
Data written successfully!
Let's read newly written data
Asynchronous read: Microlead
```

## Lecture d'un fichier

### Syntaxe

Voici la syntaxe de l'une des méthodes de lecture d'un fichier :

```js
fs.read(fd, buffer, offset, length, position, callback)
```

Cette méthode utilise le descripteur de fichier pour lire le fichier. Si vous voulez lire le fichier directement en utilisant le nom du fichier, vous devez utiliser une autre méthode disponible.

### Paramètres

Voici la description des paramètres utilisés :

- **fd** - C'est le descripteur de fichier renvoyé par fs.open().
- **buffer** - C'est le tampon dans lequel les données seront écrites.
- **offset** - Il s'agit du décalage dans le tampon pour commencer à écrire.
- **length** - Il s'agit d'un nombre entier spécifiant le nombre d'octets à lire.
- **position** - Il s'agit d'un nombre entier spécifiant l'endroit où commencer la lecture dans le fichier. Si position est nul, les données seront lues à partir de la position actuelle du fichier.
- **callback** - C'est la fonction de rappel qui reçoit les trois arguments, (err, bytesRead, buffer).

### Exemple

Créons un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");
var buf = new Buffer(1024);

console.log("Going to open an existing file");
fs.open('input.txt', 'r+', function(err, fd) {
    if (err) {
        return console.error(err);
    }
    console.log("File opened successfully!");
    console.log("Going to read the file");
    
    fs.read(fd, buf, 0, buf.length, 0, function(err, bytes){
        if (err){
            console.log(err);
        }
        console.log(bytes + " bytes read");
        
        // Print only read bytes to avoid junk.
        if(bytes > 0){
            console.log(buf.slice(0, bytes).toString());
        }
    });
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to open an existing file
File opened successfully!
Going to read the file
97 bytes read
Microlead, le chemin vers le succès !!!!!
```

## Fermeture d'un fichier

### Syntaxe

La syntaxe suivante permet de fermer un fichier ouvert : 

```js
fs.close(fd, callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **fd** - C'est le descripteur de fichier renvoyé par fs.open().
- **buffer** - C'est le tampon dans lequel les données seront écrites.
- **offset** - Il s'agit du décalage dans le tampon pour commencer à écrire.
- **length** - Il s'agit d'un nombre entier spécifiant le nombre d'octets à lire.
- **position** - Il s'agit d'un nombre entier spécifiant l'endroit où commencer la lecture dans le fichier. Si position est nul, les données seront lues à partir de la position actuelle du fichier.
- **callback** - C'est la fonction de rappel qui reçoit les trois arguments, (err, bytesRead, buffer).

### Exemple

Créons un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");
var buf = new Buffer(1024);

console.log("Going to open an existing file");
fs.open('input.txt', 'r+', function(err, fd) {
    if (err) {
        return console.error(err);
    }
    console.log("File opened successfully!");
    console.log("Going to read the file");
}
```

## Fermeture d'un fichier

### Syntaxe

La syntaxe suivante permet de fermer un fichier ouvert : 

```js
fs.close(fd, callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **fd** - C'est le descripteur de fichier renvoyé par fs.open().
- **callback** - C'est la fonction de rappel qui reçoit les trois arguments, (err, bytesRead, buffer).

### Exemple

Créons un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");
var buf = new Buffer(1024);

console.log("Going to open an existing file");
fs.open('input.txt', 'r+', function(err, fd) {
    if (err) {
        return console.error(err);
    }
    console.log("File opened successfully!");
    console.log("Going to read the file");
    
    fs.read(fd, buf, 0, buf.length, 0, function(err, bytes){
        if (err){
            console.log(err);
        }
        console.log(bytes + " bytes read");
        
        // Print only read bytes to avoid junk.
        if(bytes > 0){
            console.log(buf.slice(0, bytes).toString());
        }
    });
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to open an existing file
File opened successfully!
Going to read the file
Microlead, le chemin vers le succès !!!!!

File closed successfully.
```

## Tronquer un fichier

### Syntaxe

Voici la syntaxe de la méthode permettant de tronquer un fichier ouvert :

```bash
fs.ftruncate(fd, len, callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **fd** - C'est le descripteur de fichier renvoyé par fs.open().
- **len** - C'est la longueur du fichier après laquelle le fichier sera tronqué.
- **callback** - Il s'agit de la fonction de rappel. Aucun argument autre qu'une éventuelle exception n'est donné à la fonction de rappel d'achèvement.

### Exemple

Créons un fichier js nommé main.js ayant le code suivant :

```js
var fs = require("fs");
var buf = new Buffer(1024);

console.log("Going to open an existing file");
fs.open('input.txt', 'r+', function(err, fd) {
    if (err) {
        return console.error(err);
    }
    console.log("File opened successfully!");
    console.log("Going to truncate the file after 10 bytes");
    
    // Truncate the opened file.
    fs.ftruncate(fd, 10, function(err) {
        if (err) {
            console.log(err);
        } 
        console.log("File truncated successfully.");
        console.log("Going to read the same file"); 
        
        fs.read(fd, buf, 0, buf.length, 0, function(err, bytes){
            if (err) {
                console.log(err);
            }

            // Print only read bytes to avoid junk.
            if(bytes > 0) {
                console.log(buf.slice(0, bytes).toString());
            }

            // Close the opened file.
            fs.close(fd, function(err) {
                if (err) {
                console.log(err);
                } 
                console.log("File closed successfully.");
            });
        });
    });
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to open an existing file
File opened successfully!
Going to truncate the file after 10 bytes
File truncated successfully.
Going to read the same file
Microlead 
File closed successfully.
```

## Supprimer un fichier

### Syntaxe

Voici la syntaxe de la méthode d'effacement d'un fichier :

```bash
fs.unlink(path, callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **path** - Il s'agit du nom du fichier, y compris le chemin.
- **callback** - Il s'agit de la fonction de rappel. Aucun argument autre qu'une éventuelle exception n'est donné à la fonction de rappel d'achèvement.

### Exemple

Créons un fichier js nommé main.js ayant le code suivant :

```js
var fs = require("fs");

console.log("Going to delete an existing file");
fs.unlink('input.txt', function(err) {
    if (err) {
        return console.error(err);
    }
    console.log("File deleted successfully!");
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to delete an existing file
File deleted successfully!
```

## Créer un répertoire

### Syntaxe

Voici la syntaxe de la méthode de création d'un répertoire :

```bash
fs.mkdir(path[, mode], callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **path** - C'est le nom du répertoire incluant le chemin.
- **mode** - Il s'agit de la permission du répertoire à définir. La valeur par défaut est 0777.
- **callback** - Il s'agit de la fonction de rappel. Aucun argument autre qu'une exception éventuelle n'est donné au rappel d'achèvement.

### Exemple

Créons un fichier js nommé main.js ayant le code suivant :

```js
var fs = require("fs");

console.log("Going to create directory /tmp/test");
fs.mkdir('/tmp/test',function(err) {
    if (err) {
        return console.error(err);
    }
    console.log("Directory created successfully!");
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to create directory /tmp/test
Directory created successfully!
```

## Lire un répertoire

### Syntaxe

Voici la syntaxe de la méthode pour lire un répertoire :

```js
fs.readdir(path, callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **path** - C'est le nom du répertoire incluant le chemin.
- **callback** - C'est la fonction de rappel qui reçoit deux arguments (err, files) où files est un tableau des noms des fichiers dans le répertoire, à l'exclusion de '.' et '..'.

### Exemple

Créons un fichier js nommé main.js ayant le code suivant :

```js
var fs = require("fs");

console.log("Going to read directory /tmp");
fs.readdir("/tmp/",function(err, files) {
    if (err) {
        return console.error(err);
    }
    files.forEach( function (file) {
        console.log( file );
    });
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to read directory /tmp
ccmzx99o.out
ccyCSbkF.out
employee.ser
hsperfdata_apache
test
test.txt
```

## Supprimer un répertoire

### Syntaxe

Voici la syntaxe de la méthode permettant de supprimer un répertoire :

```js
fs.rmdir(path, callback)
```

### Paramètres

Voici la description des paramètres utilisés :

- **path** - C'est le nom du répertoire incluant le chemin.
- **callback** - Il s'agit de la fonction de rappel. Aucun argument autre qu'une éventuelle exception n'est donné à la fonction de rappel d'achèvement.

### Exemple

Créons un fichier js nommé main.js ayant le code suivant :

```js
var fs = require("fs");

console.log("Going to delete directory /tmp/test");
fs.rmdir("/tmp/test",function(err) {
    if (err) {
        return console.error(err);
    }
    console.log("Going to read directory /tmp");
    
    fs.readdir("/tmp/",function(err, files) {
        if (err) {
            return console.error(err);
        }
        files.forEach( function (file) {
            console.log( file );
        });
    });
});
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Going to read directory /tmp
ccmzx99o.out
ccyCSbkF.out
employee.ser
hsperfdata_apache
test.txt
```