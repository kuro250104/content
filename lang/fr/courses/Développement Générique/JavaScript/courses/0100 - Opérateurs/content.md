Comme beaucoup d’autres langages de programmation, le JavaScript permet de faire des calculs et des comparaisons entre différentes valeurs. 

## Opérateurs classiques

Le langage JavaScript permet d’effectuer des opérations mathématiques de bases sur des valeurs.

Pour commencer, le signe égal est utilisé pour assigner une valeur à une variable.

Exemple :

``` js
var a = 5, b = 6; // Ici a vaut 5 et b vaut 6
```

Pour additionner des valeurs entre elles, le signe plus (+) doit être utilisé.

Exemple :

``` js
var a = 5, b = 6;
var result = a + b;

console.log(result); /* La console affiche 11, car c'est le résultat de l'addition entre les variables a et b */
```

Pour soustraire des valeurs entre elles, il faut utiliser le signe moins (-).

Exemple :

``` js
var a = 5, b = 6;
var result = b - a;

console.log(result); // Ici, la console affiche 1
```

S’il y a besoin de diviser des valeurs, le slash (/) est utilisé.

Exemple :

``` js
var a = 5, b = 6;
var result = b / a;

console.log(result); // Ici, la console affiche 1.2
```

Lorsque deux valeurs doivent être multipliées, le signe étoile (*) doit être utilisé.

Exemple :

``` js
var a = 5, b = 6;
var result = a * b;

console.log(result); // Ici, la console affiche 30
```

### Résumé des principaux opérateurs arithmétiques en JavaScript

Ci-dessous, une liste récapitulant les opérateurs arithmétiques mis à disposition par le langage JavaScript :

- ```+``` : permet d’additionner deux valeurs entre elles
- ```-``` : opérateur de soustraction
- ```*``` : permet de multiplier des valeurs entre elles
- ```/``` : permet de diviser des valeurs entre elles
- ```**``` : opérateur d’exponentiel
- ```%``` : appelé modulo, cet opérateur permet de récupérer le reste d’une division
- ```++``` : opérateur d’incrémentation
- ```--``` : opérateur de décrémentation

## Opérateurs d’assignation

Il est parfois nécessaire d’assigner une nouvelle valeur à une variable, pour ce faire, il est possible d’utiliser différents opérateurs d’assignation.

### Assigner une valeur

Pour assigner une valeur à une variable, le signe égal (=) est utilisé. 

Exemple :

``` js
var a = 10; // Ici, la variable a vaut 10
```

### Ajouter une valeur

Il est également possible d’ajouter une valeur à une autre en utilisant le signe plus égal (+=).

Exemple :

``` js
var a = 10, b = 5;
var result = a - b; // Ici, result vaut 5

result += 5; // Ici, result vaut 10, car 5 est ajouté au résultat déjà contenu dans la variable
```

### Soustraire une valeur

Pour soustraire un nombre à une valeur stockée dans une variable, le signe moins égal (-=) est utilisé.

Exemple :

``` js
var a = 10, b = 5;
var result = a - b; // Ici, result vaut 5

result -= 5; // Ici, result vaut 0, car 5 est soustrait au résultat déjà contenu dans la variable result
```

### Multiplier une valeur

Pour multiplier un chiffre par une valeur déjà contenue dans une variable, le signe étoile égale (*=) est utilisé.

Exemple :

``` js
var a = 10, b = 5;
var result = a - b; // Ici, result vaut 5

result *= 5; // Ici, result vaut 25, car 5 est multiplié par le résultat déjà contenu dans la variable result
```

### Diviser une valeur

Le langage JavaScript permet également de diviser une valeur déjà contenue dans une variable par un chiffre. Pour ce faire, il faut utiliser le signe slash égal (/=).

Exemple :

``` js
var a = 10, b = 5;
var result = a - b; // Ici, result vaut 5

result *= 5; // Ici, result vaut 1, car le résultat déjà contenu dans la variable result est divisé par 5
```

### Récupérer le reste d’une division

De manière générale, pour récupérer le reste d’une division en JavaScript, il faut utiliser le signe modulo (%).

Pour récupérer le reste d’une division effectuée avec une valeur déjà contenue dans une variable, il faut utiliser le signe modulo égal (%=).

Exemple :

``` js
var a = 10, b = 5;
var result = a - b; // Ici, result vaut 5

result %= 7; // Ici, result vaut le reste de la division de 5 par 7, c’est à dire 5
```

### Exponentielle

Pour créer une exponentielle à partir d’un résultat déjà contenu dans une variable, il faut utiliser le signe **=.

Exemple :

``` js
var a = 5, b = 6;
var result = b / a;

result **= 6; // Ici, result vaut 2.9859839999999993 
```

## Opérateurs de chaînes de caractères

Pour ajouter une chaîne de caractère à une autre - dans un tel cas, le terme “concaténation” est utilisé -, deux opérateurs sont utilisables.

### Opérateur +

Pour former une phrase avec des chaînes de caractères stockées dans des variables différentes, il est possible d’utiliser l’opérateur +.

Exemple :

``` js
var text1 = "Hello", text2 = "World !";
var text3 = text1 + " " + text2; // Ici, la variable text3 vaut "Hello World !"
```

### Opérateur +=

Comme pour les opérateurs arithmétiques, pour gagner du temps et économiser du code, une chaîne de caractères peut-être ajoutée à une autre en utilisant l’opérateur +=.

Exemple :

``` js
var text = "Hello";
text += " World !"; /* La variable text contient désormais la chaîne de caractères "Hello World !" */
```

### Ajouter des nombres à des chaînes de caractères

Quand l’opérateur + est utilisé avec des nombres, la variable contient la somme de l’addition. Cependant, lorsque cet opérateur est utilisé avec des nombres et des chaînes de caractères, le résultat retourné est une chaîne de caractères. 

Exemple :

``` js
var a = "Me", b = 5;
var c = a + b; // Ici, la variable c contient la chaîne de caractères "Me5"
```

## Opérateurs de comparaison

La liste ci-dessous récapitule les opérateurs de comparaison mis à disposition par JavaScript. Ces opérateurs sont détaillés dans le cours dédié aux opérateurs de comparaison en JavaScript.

- ```==``` : est égal à
- ```===``` : est strictement égal à
- ```!=``` : n’est pas égal à OU est différent de 
- ```!==``` : n'est strictement pas égal à OU est strictement différent de
- ```>``` : est supérieur à
- ```<``` : est inférieur à
- ```>=``` : est supérieur ou égal à
- ```<=``` : est inférieur ou égal à
- ```?``` : opérateur ternaire

## Opérateurs logiques

Les opérateurs logiques sont détaillés dans le cours dédié aux opérateurs de comparaison en JavaScript. La liste ci-dessous résume malgré tout les opérateurs logiques utilisables :

- ```&&``` : et
- ```||``` : ou
- ```!``` : n’est pas