Les objets globaux de Node.js sont globaux par nature et ils sont disponibles dans tous les modules. Nous n'avons pas besoin d'inclure ces objets dans notre application, nous pouvons plutôt les utiliser directement. Ces objets sont des modules, des fonctions, des chaînes de caractères et l'objet lui-même comme expliqué ci-dessous.

## __filename

Le __filename représente le nom de fichier du code en cours d'exécution. Il s'agit du chemin absolu résolu de ce fichier de code. Pour un programme principal, ce n'est pas nécessairement le même nom de fichier que celui utilisé dans la ligne de commande. La valeur à l'intérieur d'un module est le chemin d'accès à ce fichier de module.

### Exemple

Créez un fichier js nommé main.js avec le code suivant :

```js
// Let's try to print the value of __filename

console.log( __filename );
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

En fonction de l'emplacement de votre programme, il imprimera le nom du fichier principal de la manière suivante :

```bash
/web/com/1427091028_21099/main.js
```

## __dirname

Le __dirname représente le nom du répertoire dans lequel réside le script en cours d'exécution.

### Exemple

Créez un fichier js nommé main.js avec le code suivant :

```js
// Let's try to print the value of __dirname

console.log( __dirname );
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

En fonction de l'emplacement de votre programme, il imprimera le nom du répertoire actuel comme suit :

```bash
/web/com/1427091028_21099
```

## setTimeout(cb, ms)

La fonction globale ```setTimeout(cb, ms)``` est utilisée pour exécuter le callback cb après au moins ms millisecondes. Le délai réel dépend de facteurs externes tels que la granularité de la minuterie du système d'exploitation et la charge du système. Une minuterie ne peut pas durer plus de 24,8 jours.

Cette fonction renvoie une valeur opaque qui représente le timer et qui peut être utilisée pour effacer le timer.

### Exemple

Créez un fichier js nommé main.js avec le code suivant :

```js
function printHello() {
    console.log( "Hello, World!");
}

// Now call above function after 2 seconds
setTimeout(printHello, 2000);
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifiez que la sortie est imprimée après un petit délai.

```bash
Hello, World!
```

## clearTimeout(t)

La fonction globale ```clearTimeout(t)``` est utilisée pour arrêter un timer qui a été précédemment créé avec setTimeout(). Ici, t est le timer renvoyé par la fonction ```setTimeout()```.

### Exemple

Créez un fichier js nommé main.js avec le code suivant :

```js
function printHello() {
    console.log( "Hello, World!");
}

// Now call above function after 2 seconds
var t = setTimeout(printHello, 2000);

// Now clear the timer
clearTimeout(t);
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifiez la sortie où vous ne trouverez rien d'imprimé.

## setInterval(cb, ms)

La fonction globale ```setInterval(cb, ms)``` est utilisée pour exécuter le callback cb de manière répétée après au moins ms millisecondes. Le délai réel dépend de facteurs externes tels que la granularité de la minuterie du système d'exploitation et la charge du système. Une minuterie ne peut pas durer plus de 24,8 jours.

Cette fonction renvoie une valeur opaque qui représente le timer et qui peut être utilisée pour effacer le timer à l'aide de la fonction ```clearInterval(t)```.

### Exemple

Créez un fichier js nommé main.js avec le code suivant :

```js
function printHello() {
   console.log( "Hello, World!");
}

// Now call above function after 2 seconds
setInterval(printHello, 2000);
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Le programme ci-dessus exécutera ```printHello()``` toutes les 2 secondes. En raison de la limitation du système.