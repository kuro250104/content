Le JavaScript peut s’exécuter à intervalle régulier. Il s’agit alors d’utiliser l’événement ```timing```.

## Les événements de timing

En fait, c’est l’objet ```Windows``` qui permet l’exécution de code à intervalle régulier. Ces intervalles de temps sont appelés événements de timing.

Voici les deux fonctions utilisables pour gérer les événements de timing :

- ```setTimeOut(fonction, millisecondes)``` : Cette fonction exécute une fonction après un certain nombre de millisecondes écoulées.
- ```setInterval(fonction, millisecondes)``` : Cette fonction permet d’exécuter une fonction après un certain nombre de millisecondes écoulées et répète continuellement la fonction.

__Remarque__ : Ces deux méthodes appartiennent à l’objet DOM ```window```.

## La méthode setTimeOut()

### Syntaxe

Voici la syntaxe pour utiliser cette méthode :

```js
window.setTimeOut(fonction, millisecondes);
```

Le premier paramètre reçu est la fonction à exécuter. Ce peut être une fonction externe ou une fonction anonyme (ou fléchée). Le second paramètre est le temps, en millisecondes, qui doit s’écouler avant que la fonction ne s'exécute à nouveau. 

__Remarque__ : Ici encore, le préfixe ```Windows``` n’est pas obligatoire.

Exemple :

```js
<button onclick="setTimeout(myFunction, 3000)">Try it</button>

<script>
function myFunction() {
    alert('Hello');
}
</script>
```

### Arrêter l’exécution

Pour arrêter l’exécution de ```setTimeOut()```, la méthode ```clearTimeOut()``` est utilisée. Cette méthode, en fait, arrête l’exécution de la fonction appelée dans ```setTimeOut()```.

#### Syntaxe

```js
clearTimeOut(variable);
```

Cette méthode prend en paramètre la variable retournée par ```setTimeOut()```.

Si la fonction n’a pas encore été exécutée, il est tout de même possible d’utiliser la méthode d’arrêt, mais celle-ci ne prend aucun paramètre : ```clearTimeOut()```.

Exemple :

```js
<button onclick="myVar = setTimeout(myFunction, 3000)">Try it</button>

<button onclick="clearTimeout(myVar)">Stop it</button>
```

## La méthode setInterval()

Cette méthode répète la fonction invoquée dans un intervalle de temps donné. 

### Syntaxe

```js
setInterval(fonction, milliseconds);
```

Cette méthode prend en premier paramètre la fonction à exécuter. Le second paramètre indique la longueur de l’intervalle de temps à laisser avant d’exécuter à nouveau la fonction.

Exemple :

```js
setInterval(myTimer, 1000);

function myTimer() {
    const d = new Date();
    document.getElementById("demo").innerHTML = d.toLocaleTimeString();
}
```

Cet exemple exécute une fonction appelée ```myTimer()``` toutes les secondes, comme une montre.

### Arrêter l’exécution

Comme pour la méthode précédente, il existe également une méthode pour arrêter l’exécution de la fonction appelée par ```setInterval()```. Il s’agit de la méthode ```clearInterval()```.

#### Syntaxe

La syntaxe de ```clearInterval()``` est la suivante :

```js
clearInterval(variable)
```

Ici encore, ```clearInterval()``` utilise la variable retournée par ```setInterval()```.

Exemple :

```js
<p id="demo"></p>

<button onclick="clearInterval(myVar)">Stop time</button>

<script>
let myVar = setInterval(myTimer, 1000);
function myTimer() {
  const d = new Date();
  document.getElementById("demo").innerHTML = d.toLocaleTimeString();
}
</script>
```

Cet exemple est le même que celui écrit pour la méthode ```setTimeOut()```. La seule différence est qu’ici, un bouton “stop timer” a été ajouté. 
