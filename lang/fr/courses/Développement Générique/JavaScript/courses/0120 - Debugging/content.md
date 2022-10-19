Tout programme doit être débuggé lorsque celui-ci retourne une erreur. En JavaScript, il existe plusieurs méthodes pour débugger un code.

## Débugger

Un programme peut contenir des erreurs de logique ou de syntaxe. La plupart de ces difficultés sont difficiles à trouver - surtout lorsqu’un programme est composé de plusieurs centaines de lignes de code. 

Souvent, lorsqu’un programme contient une erreur, il ne se passera rien. En fait, soit le programme ne se lancera pas, soit il ne retournera tout simplement rien. Parfois des messages d’erreurs sont retournés, mais pas tout le temps.

Chercher et résoudre les erreurs dans un code est appelé “debugger” un code. 

## Les débogueurs JavaScript

Une débuggueur est un outil utilisé pour débugger un code - donc pour chercher et résoudre les erreurs dans un programme. 

Ces outils sont utilisés pour faciliter la tâche aux développeurs. 

Tous les navigateurs internet modernes possèdent un débuggueur de code JavaScript. Ces derniers peuvent être désactivés de manière à ce que les erreurs ne soient pas affichées aux utilisateurs.

Il est également possible, grâce à ces outils, d’installer des “points d’arrêt”, ou break point en anglais. Ces points d’arrêt permettent d’arrêter l’exécution du code à un endroit précis, afin de tester le contenu d’une variable, par exemple.

## Débbuger un code

Pour débugger un code, il existe plusieurs méthodes.

### La méthode console.log()

```console.log()``` est souvent utilisé pour débbuger un code, notamment en affichant le contenu d’une variable. Cette fonction affiche le contenu de la variable dans la console du navigateur. 

Exemple :

``` js
let userAge = 12;
console.log(userAge);
```

Cet exemple affiche 12 - le contenu de la variable ```userAge``` - dans la console du navigateur.

### Mettre des breaks points

Dans la fenêtre de débuggage du navigateur, il y a la possibilité de mettre des breaks points dans du code JavaScript. 

En fait, à chaque break point, JavaScript arrête l’exécution du programme et permet au développeur d’examiner le contenu d’une variable. 

Une fois l’examen de la variable effectué, il est possible de reprendre l’exécution du code.

### Le mot-clé debugger

Ce mot-clé stop l’exécution du code JavaScript là où il est placé et appelle, si elles sont disponibles, les fonctions de débuggage. Ce mot-clé a, en fait, les mêmes fonctions qu’un break point dans un code. Si aucun débuggueur n’est disponible, cette déclaration n’a aucun effet et l’exécution du code s’effectue correctement. 

Exemple :

``` js
let x = 15 * 5;
debugger;
document.getElementById("demo").innerHTML = x;
```

Dans cet exemple, si un débuggueur est disponible, JavaScript arrête l’exécution du programme à l’endroit où debugger est déclaré. La troisième ligne n’est donc pas exécutée. 