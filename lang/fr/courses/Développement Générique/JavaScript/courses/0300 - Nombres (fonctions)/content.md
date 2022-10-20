JavaScript met à disposition des fonctions natives afin de permettre aux développeurs de travailler les nombres.

## Convertir un nombre en chaîne de caractères

La fonction ```toString()``` permet de convertir un nombre en chaîne de caractères.

Exemple :

```js
var x = 123; // Ici, x contient le NOMBRE 123
x.toString(); // Ici, désormais, x n'est plus un nombre, mais une chaîne de caractères
```

## Exponentielle

La méthode ```toExponential()``` permet d’arrondir un nombre avec une notation exponentielle, c’est-à-dire avec un exposant.

Cette fonction prend en paramètre le nombre de chiffres après la virgule où le nombre doit être arrondi.

__Remarque__ : Si aucun paramètre n’est passé, la fonction n’arrondit pas le nombre.

Exemple :

```js
var x = 2.4567;
x.toExponential(2);
```

Cet exemple retourne le résultat suivant : ```2.46e+0```. En fait, comme demandé en paramètre, la fonction ```toExponential()``` arrondi le nombre x à deux chiffres après la virgule et indique la “puissance” mathématiques des nombres - ici : ```e+0```.

## Retourner un décimal en chaîne de caractères

Le JavaScript permet également de retourner un nombre en tant que chaîne de caractères, avec un nombre spécifique de chiffres après la virgule. Pour ce faire, il faut utiliser la fonction ```toFixed()```. Cette fonction reçoit en paramètre le nombre de chiffres à retourner après la virgule. 

Exemple :

```js
var x = 2.4567;
x.toFixed(2);
```

L’exemple ci-dessus retourne le résultat suivant : 2.46.

## Longueur spécifique

Pour retourner un nombre avec une longueur spécifique, la fonction ```toPrecision()``` est utilisée. Elle reçoit en valeur la taille du nombre à retourner. 

Exemple :

```js
var x = 2.4567;
x.toPrecision(1); // Ici, x vaut 2
x.toPrecision(2); // Ici, x vaut 2.5
```

## Retourner la valeur primitive d’un objet

La fonction ```valueOf()``` permet de retourner la valeur primitive d’un objet. 

En JavaScript, un nombre peut être primitif ou un objet. La fonction ```valueOf()``` est utilisée de manière interne en JavaScript afin de convertir un objet en valeur primitive. Il n’y a donc aucune raison d’utiliser cette fonction au sein d’un script. 

Exemple : 

```js
(5 + 5).valueOf(); // Ici, la valeur 60 est retournée
```

## Convertir des variables en nombre

Il existe 3 fonctions JavaScript permettant de convertir une variable en nombre. 

### La fonction Number()

Cette fonction est utilisée pour convertir une variable en nombre. 

Exemple :

```js
Number("5"); // Retourne 5
Number("Bonjour"); // Retourne NaN
```

La deuxième ligne de code retourne ```NaN``` car “Bonjour” est bien une chaîne de caractères et non pas un nombre.

### La fonction parseInt()

Cette fonction permet de parser une chaîne de caractères et retourne un nombre entier. Les espaces sont autorisés et seul le premier nombre est retourné. 

Exemple :

```js
parseInt("10 20 30 40");
```

Dans cet exemple, seul le premier nombre est retourné, donc 10.

### La fonction parseFloat()

La fonction ```parseFloat()``` permet de parser une chaîne de caractères et retourne un nombre entier. Les espaces sont autorisés et seul le premier nombre est retourné. 

Si un nombre flottant - c’est-à-dire à virgule - est déclaré, grâce à ```parseFloat()```, ce nombre sera retourné tel quel ; tandis que si un nombre à virgule est utilisé avec ```parseInt()```, seul le nombre avant la virgule est retourné. 

Exemple :

```js
parseFloat("10.45"); // Ici, 10.45 est retourné
```

## Les propriétés de nombres en JavaScript

Le langage JavaScript met à disposition un certain nombre de propriétés permettant de travailler sur les nombres. 

### Les propriétés MIN_VALUE et MAX_VALUE

Ces deux propriétés permettent de retourner le plus grand nombre disponible en JavaScript, pour ```MAX_VALUE```, et le plus petit nombre disponible pour ```MIN_VALUE```.

Exemple :

```js
var x = Number.MIN_VALUE; // Retourne le plus petit nombre disponible en Javascript
var y = Number.MAX_VALUE; // Retourne le plus grand nombre disponible en Javascript
```

### POSITIVE_INFINITY et NEGATIVE_INFINITY

```POSITIVE_INFINITY``` représente l’infini positif, tandis que ```NEGATIVE_INFINITY``` représente l’infini négatif. 

Exemple :

```js
var x = 1 / 0; // Ici, POSITIVE_INFINITY est retourné
var y = -1 / 0; // Ici, NEGATIVE_INFINITY est retourné
```

## Les propriétés et les variables

Les propriétés de nombre appartiennent à l’objet ```Number``` en JavaScript. Ces propriétés peuvent seulement être utilisées avec ```Number.MAX_VALUE```. Cela signifie également qu’elles ne peuvent pas être utilisées de cette manière : ```variable.MAX_VALUE```, car **variable** n’est pas un objet ```Number```.
