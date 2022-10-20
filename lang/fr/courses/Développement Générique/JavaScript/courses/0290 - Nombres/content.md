En JavaScript, contrairement à d’autres langages, il n’existe qu’un type de nombre. Ceux-ci peuvent être des nombres entiers ou des nombres décimaux. 

## Précisions sur les nombres en JavaScript

Tel que précisé dans l’introduction, JavaScript comprend un seul type de nombre. Par défaut, les nombres stockés sont des décimaux avec deux chiffres derrière la virgule. 

## Ajouter des nombres et des chaînes de caractères

__Rappel__ : L’opérateur + est à la fois utilisé pour concaténer et pour additionner. Une précision s’impose : les **chaînes de caractères** sont **concaténées**, tandis que **les nombres** sont **additionnés**.

Si deux nombres sont additionnés, le résultat retourné sera un nombre.

Exemple :

```js
var a = 5, b = 5;
console.log(a + b);
```

Dans cet exemple, la console affiche 10, car deux nombres sont additionnés ensemble.

Cependant, si un nombre est additionné avec une chaîne de caractères, ce nombre est à son tour considéré comme un *string*.

Exemple :

```js
var a = 5, b = "Bonjour";
console.log(a + b);
```

Cet exemple retourne la chaîne de caractères “**5Bonjour**”, car la variable est désormais considérée comme une chaîne de caractères, étant donné qu’elle est additionnée avec la variable b.

## Chaînes de caractères numériques

Hormis pour les additions, le JavaScript va, pour toutes les autres opérations arithmétiques, tenter de convertir une chaîne de caractères en chiffres si cela est possible.

Exemple :

```js
var a = "5", b = "5";
console.log(a / b);
```

Ici, bien que les variables **a** et **b** contiennent des chiffres considérés comme des chaînes de caractères, l’opération 5/5 fonctionne et la console retourne bien le quotient de la division : 1.

## Not a Number (NaN)

**NaN** est un mot-clé JavaScript qui indique qu’un nombre n’en est pas un. 

Exemple :

```js
var a = 5, b = "Bonjour";
console.log(a / b);
```

Dans cet exemple, la console retourne une erreur, car b est considéré comme **NaN**, c'est-à-dire que ce n’est pas un nombre.

## La fonction globale isNaN()

JavaScript met à disposition la fonction ```isNaN()``` permettant de vérifier si une variable est un nombre ou non.

Exemple :

```js
var a = "Bonjour", b = "5";
isNaN(a); // Ici la valeur retournée est true, car la variable a n'est pas un nombre
isNaN(b); // Ici la valeur retournée est false, car b contient un nombre
```

## Infini

```Infinity``` (ou ```-Infinity```) est la valeur retournée lorsqu’un nombre est calculé, mais qu’il est au-delà du plus grand nombre possible.

De plus, les divisions par 0 retournent aussi la valeur ```Infinity```.

Exemple :

## Hexadécimal

Si elles sont précédées par 0x, les constantes numériques sont interprétées par JavaScript comme des valeurs hexadécimales.

Exemple :

```js
var hexa = 0xFF // Ici, la variable hexa contient la valeur 255
```