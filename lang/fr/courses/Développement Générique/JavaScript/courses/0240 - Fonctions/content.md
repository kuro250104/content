Un bon code est un code découpé en fonctions, chacune exécutant **une** tâche particulière.

## Syntaxe

Pour créer une fonction en JavaScript, il faut utiliser le mot clé ```function```, suivi du nom de la fonction, suivi de parenthèses - permettant d’indiquer si la fonction reçoit ou non des paramètres -, elles-mêmes suivies d’une paire d'accolades contenant le code à exécuter. 

Le nom d’une fonction peut contenir des lettres, des chiffres, des underscores (**_**) et un signe dollar (**$**).

Exemple :

```js
function name (paremètre1, paramètre2) {
    // Code à exécuter
}
```

__Remarque__ :

- Dans une fonction, les paramètres sont appelés **arguments** et contiennent les valeurs que la fonction doit utiliser.
- Dans une fonction, les **arguments** agissent comme des **variables locales**

## Appeler une fonction

Il existe 3 méthodes pour appeler une fonction :

- Lorsqu’un évènement se produit (par exemple, lorsque l’utilisateur clique sur un bouton)
- Lorsqu’elle est appelée directement depuis le code JavaScript
- Automatiquement (la fonction s’appelle elle-même)

## Return

Lorsque la fonction doit retourner un résultat, le mot-clé ```return``` est utilisé. Lorsque JavaScript atteint un ```return```, il stoppe l’exécution de la fonction et retourne le résultat à la variable qui a appelé la fonction.

Exemple : 

```js
result = multiply(4,5);

function multiply(number1, number2) {
	return number1*number2; // Ici, la fonction renvoie 20 à la variable result
}
```

## Pourquoi utiliser les fonctions ?

Il existe de nombreux avantages à utiliser les fonctions, parmi lesquels, le fait d’écrire une seule fonction et pouvoir l’appeler plusieurs fois dans le code, le fait de découper le code en plusieurs tâches uniques, rendant la lecture du code plus agréable et permettant d’optimiser ce dernier. 

## Les parenthèses lors de l’appel de la fonction

Il existe une particularité à connaître lors de l’appel à une fonction et qui peut causer des résultats inattendus lors de l’exécution du code, si cette particularité n’est pas connue : l’utilisation des parenthèses. 

Lorsqu’un appel à une fonction est effectué et que les parenthèses sont **utilisées**, cela réfère au **résultat** de la fonction appelée ; tandis que lorsqu’elles ne sont **pas utilisées**, cela réfère à l’objet de la fonction.

Exemple :

```js
function toCelsius(fahrenheit) {
    return (5/9) * (fahrenheit-32);
}
document.getElementById("demo").innerHTML = toCelsius(77);
```

Dans cet exemple, des parenthèses sont utilisées lors de l’appel de la fonction ```toCelsius```. Cela réfère donc au **résultat** de la fonction.

Exemple :

```js
function toCelsius(fahrenheit) {
    return (5/9) * (fahrenheit-32);
}
document.getElementById("demo").innerHTML = toCelsius;
```

Dans cet exemple, les parenthèses ne sont pas utilisées lors de l’appel à la fonction. Cela réfère donc à l’**objet** de la fonction.

## Utilisation des fonctions comme des valeurs de variables

Les fonctions peuvent être utilisées de la même manière que les variables, dans tout type de formules, d’assignation et de calculs.

Exemple :

```js
var x = toCelsius(77);
var text = "La température est de " + x + " degrés Celsius";
```

Dans cet exemple, la valeur du calcul fait par la fonction ```toCelsius``` est stockée dans une variable ```x```. C’est cette variable qui est appelée dans le texte à afficher. 

Exemple :

```js
var text = "La température est de " + toCelsius(77) + " degrés Celsius";
```

Dans cet exemple, le résultat de la conversion des Fahrenheit en Celsius est directement affiché avec l’appel à la fonction ```toCelsius```.

## Variables locales

Les variables créées au sein d’une fonction sont des variables dites **locales**. Cela signifie qu’elles ne sont reconnues qu’au sein de ladite fonction. En d’autres termes, ces variables sont créées lorsque la fonction commence et sont effacées lorsque la fonction est terminée. 

L’avantage au fait que les variables déclarées au sein d’une fonction soient locales est que le même nom peut être donné à des variables créées dans des fonctions différentes.

Exemple :

```js
// Le code situé avant la fonction ne peut pas utiliser la variable "car"

function myFunction() {
  var car = "Volvo";
  // Ce code peut utiliser la variable "car"
}

// Ce code ne peut pas utiliser la variable "car"
```
