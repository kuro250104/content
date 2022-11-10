## Qu'est-ce que le rappel ?

Le callback est l'équivalent asynchrone d'une fonction. Une fonction de rappel est appelée à la fin d'une tâche donnée. Node fait un usage intensif des callbacks. Toutes les API de Node sont écrites de telle manière qu'elles supportent les callbacks.

Par exemple, une fonction de lecture d'un fichier peut commencer à lire le fichier et renvoyer immédiatement le contrôle à l'environnement d'exécution afin que l'instruction suivante puisse être exécutée. Une fois l'E/S du fichier terminée, elle appellera la fonction de callback en lui passant en paramètre le contenu du fichier. Il n'y a donc pas de blocage ou d'attente pour l'E/S de fichier. Cela rend Node.js très évolutif, car il peut traiter un grand nombre de demandes sans attendre qu'une fonction renvoie des résultats.

## Exemple de code de blocage

Créez un fichier texte nommé input.txt avec le contenu suivant :

```bash
Microlead, le chemin vers le succès !!!!!
```

Créez un fichier js nommé main.js avec le code suivant :

```js
var fs = require("fs");
var data = fs.readFileSync('input.txt');

console.log(data.toString());
console.log("Program Ended");
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```js
$ node main.js
```

Vérifier la sortie.

```bash
Microlead, le chemin vers le succès !!!!!
```

## Exemple de code non bloquant

Créez un fichier texte nommé input.txt avec le contenu suivant.

```bash
Microlead, le chemin vers le succès !!!!!
```

Mettez à jour main.js pour avoir le code suivant :

```js
var fs = require("fs");

fs.readFile('input.txt', function (err, data) {
    if (err) return console.error(err);
    console.log(data.toString());
});

console.log("Program Ended");
```

Maintenant, exécutez le fichier main.js pour voir le résultat :

```bash
$ node main.js
```

Vérifier la sortie.

```bash
Program Ended
Microlead, le chemin vers le succès !!!!!
```

Ces deux exemples expliquent le concept des appels bloquants et non bloquants.

- Le premier exemple montre que le programme se bloque jusqu'à ce qu'il lise le fichier et ensuite seulement il procède à la fin du programme.
- Le second exemple montre que le programme n'attend pas la lecture du fichier et procède à l'impression de "Program Ended" et, au même moment, le programme sans blocage continue à lire le fichier.

Ainsi, un programme bloquant s'exécute de manière très séquentielle. Du point de vue de la programmation, il est plus facile de mettre en œuvre la logique, mais les programmes non bloquants ne s'exécutent pas en séquence. Dans le cas où un programme a besoin d'utiliser des données à traiter, celles-ci doivent être conservées dans le même bloc pour que l'exécution soit séquentielle.