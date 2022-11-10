## Que sont les Streams ?

Les streams sont des objets qui vous permettent de lire des données depuis une source ou d'écrire des données vers une destination de manière continue. Dans Node.js, il y a quatre types de streams : 

- **Readable** - Stream qui est utilisé pour les opérations de lecture.
- **Writable** - Stream qui est utilisé pour les opérations d'écriture.
- **Duplex** - Stream qui peut être utilisé pour les opérations de lecture et d'écriture.
- **Transformer** - Un type de flux duplex où la sortie est calculée sur la base de l'entrée.

Chaque type de streams est une instance d'**EventEmitter** et lance plusieurs événements à des moments différents. Par exemple, les événements les plus couramment utilisés sont les suivants :

- **data** - Cet événement est déclenché lorsque des données sont disponibles pour la lecture.
- **end** - Cet événement est déclenché lorsqu'il n'y a plus de données à lire.
- **error** - Cet événement est déclenché en cas d'erreur de réception ou d'écriture de données.
- **finish** - Cet événement est déclenché lorsque toutes les données ont été transférées vers le système sous-jacent.

Ce cours fournit une compréhension de base des opérations couramment utilisées sur les streams.

## Lecture d'un Stream

Créez un fichier texte nommé input.txt ayant le contenu suivant :

```bash
Microlead, le chemin vers le succès !!!!!
```

Créez un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");
var data = '';

// Create a readable stream
var readerStream = fs.createReadStream('input.txt');

// Set the encoding to be utf8. 
readerStream.setEncoding('UTF8');

// Handle stream events --> data, end, and error
readerStream.on('data', function(chunk) {
    data += chunk;
});

readerStream.on('end',function() {
    console.log(data);
});

readerStream.on('error', function(err) {
    console.log(err.stack);
});

console.log("Program Ended");
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```js
$ node main.js
```

Vérifier la sortie.

```bash
Program Ended
Microlead, le chemin vers le succès !!!!!
```

## Écrire dans un Stream

Créez un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");
var data = 'Microlead, le chemin vers le succès !!!!!';

// Create a writable stream
var writerStream = fs.createWriteStream('output.txt');

// Write the data to stream with encoding to be utf8
writerStream.write(data,'UTF8');

// Mark the end of file
writerStream.end();

// Handle stream events --> finish, and error
writerStream.on('finish', function() {
    console.log("Write completed.");
});

writerStream.on('error', function(err) {
    console.log(err.stack);
});

console.log("Program Ended");
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```js
$ node main.js
```

Vérifier la sortie.

```bash
Program Ended
Write completed.
```

Ouvrez maintenant le fichier output.txt créé dans votre répertoire actuel ; il devrait contenir les éléments suivants :

```bash
Microlead, le chemin vers le succès !!!!!
```

## Piping de Streams

Le piping est un mécanisme par lequel nous fournissons la sortie d'un stream comme entrée à un autre stream. Il est normalement utilisé pour obtenir des données d'un stream et pour transmettre la sortie de ce stream à un autre stream. Il n'y a pas de limite aux opérations de piping. Nous allons maintenant montrer un exemple de piping pour lire un fichier et l'écrire dans un autre fichier.

Créez un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");

// Create a readable stream
var readerStream = fs.createReadStream('input.txt');

// Create a writable stream
var writerStream = fs.createWriteStream('output.txt');

// Pipe the read and write operations
// read input.txt and write data to output.txt
readerStream.pipe(writerStream);

console.log("Program Ended");
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Program Ended
```

Ouvrez le fichier output.txt créé dans votre répertoire courant ; il devrait contenir les éléments suivants :

```bash
Microlead, le chemin vers le succès !!!!!
```

## Chaîner les Streams

Le chaînage est un mécanisme permettant de connecter la sortie d'un stream à un autre stream et de créer une chaîne d'opérations de streams multiples. Il est normalement utilisé avec les opérations de piping. Nous allons maintenant utiliser le piping et le chaînage pour compresser un fichier, puis le décompresser.

Créez un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");
var zlib = require('zlib');

// Compress the file input.txt to input.txt.gz
fs.createReadStream('input.txt')
   .pipe(zlib.createGzip())
   .pipe(fs.createWriteStream('input.txt.gz'));
  
console.log("File Compressed.");
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
File Compressed.
```

Vous constaterez que input.txt a été compressé et qu'il a créé un fichier input.txt.gz dans le répertoire courant. Maintenant essayons de décompresser le même fichier en utilisant le code suivant :

```js
var fs = require("fs");
var zlib = require('zlib');

// Decompress the file input.txt.gz to input.txt
fs.createReadStream('input.txt.gz')
    .pipe(zlib.createGunzip())
    .pipe(fs.createWriteStream('input.txt'));

console.log("File Decompressed.");
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
File Decompressed.
```