Il arrive parfois d’avoir besoin de convertir un type de variable en un autre (une chaîne de caractères en nombre, par exemple). 

Ce cours traite des conversions suivantes :

- Chaînes de caractères en nombres
- Nombres en chaînes de caractères
- Dates en nombres
- Nombres en dates
- Booléens en nombres
- Nombres en booléens

## Conversion en JavaScript

Il existe, en JavaScript, deux moyens de convertir un type de variable en un autre :

- En utilisant des fonctions
- **Automatiquement**, c’est-à-dire que le langage JavaScript convertit lui-même un type en un autre. 

## Convertir une chaîne de caractères en nombres

Pour ce faire, la fonction globale ```number()``` peut-être utilisée. 

Cette fonction retourne donc une chaîne de caractères en nombre. Si la chaîne de caractères passée en paramètre est vide, alors 0 est retourné. Tout autre type de donnée retourne ```NaN```.

Exemple :

```js
Number("56.5"); // Retourne 56.5
Number(" "); // Retourne 0
Number(""); // Retourne également 0
Number("456 784"); // Retourne NaN
```

__Remarque__ : Plus de fonctions de conversion pour les nombres ont été détaillées dans le cours traitant de ce sujet. 

### L’opérateur +

Cet opérateur peut être utilisé pour convertir un type de variable en nombre.

Exemple :

```js
var x = "56";
var y = + x; // Ici, un typeOf indique que x a bien été converti en type "number"
```

## Convertir les nombres en chaîne de caractères

Tout comme il existe une fonction globale permettant de convertir une chaîne de caractère en nombre, ```String()``` est celle permettant de convertir un nombre en chaîne de caractères.

Cette fonction est utilisable avec n’importe quel autre type de variable ou expressions.

Exemple :

```js
String(56); // Retourne "56"
String(x); // Retourne le nombre contenu dans x sous-forme de string
String(10 + 10); // Retourne 20
```

La fonction ```toString``` de l’objet ```Number``` fait exactement la même chose. 

Exemple :

```js
(x).toString();
(56).toString();
(10 + 10).toString();
```

__Remarque__ : Plus de fonctions pour convertir les nombres en chaînes de caractères sont détaillées dans le cours traitant des fonctions de nombres.

## Convertir les dates en nombres

Comme pour la conversion de chaînes de caractères en nombres, la fonction globales ```Number()``` peut également être utilisée pour convertir des dates en nombres. 

Exemple :

```js
var dateToday = new Date();
Number(dateToday); // Retourne la date et l'heure sous forme de nombre
```

La méthode ```getTime()``` de l’objet ```date``` fait la même chose.

Exemple :

```js
var dateToday = new Date();
dateToday.getTime(); // Retourne la date et l'heure sous forme de nombre
```

## Convertir les dates en chaînes de caractères

La méthode globale ```String()``` permet de convertir les dates en chaînes de caractères.

Exemple :

```js
String(Date()); // Retourne la date et l'heure du jour en chaîne de caractères
```

La méthode ```toString()``` fait exactement la même chose.

```js
Date().toString() // Retourne la date et l'heure du jour sous forme de string
```

## Convertir les booléens en nombres

La méthode globale ```Number()``` peut aussi convertir les booléens en nombres.

Exemple :

```js
Number(false)     // Retourne 0
Number(true)      // Retourne 1
```

## Convertir les booléens en chaînes de caractères

La méthode globale ```String()``` permet de convertir les booléens en chaîne de caractères.

Exemple : 

```js
String(false); // Retourne "false"
String(true); // Retourne "true"
```

La fonction ```toString()``` peut faire exactement la même chose.

Exemple :

```js
(false).toString(); // Retourne "false"
(true).toString(); // Retourne "true"
```

## Conversion automatique

Lorsque le JavaScript essaye d’opérer sur le “mauvais” type de variable, il va automatiquement tenter de le convertir dans le type “correct”.

Attention, cependant, le résultat n’est pas tout le temps celui attendu. 

Exemple :

```js
5 + null // Retourne 5 parce null est converti en 0
"5" + null // Retourne "5null" car null est converti en "null"
"5" + 2 // Retourne "52", car 2 est converti en "2"
"5" - 2 // Retourne 3, car "5" est converti en 5
"5" * "2" // Retourne 10, car "5" et "2" sont convertis en 5 et 2
```