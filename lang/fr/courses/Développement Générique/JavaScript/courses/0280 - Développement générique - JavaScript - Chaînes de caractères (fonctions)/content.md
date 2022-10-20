Les chaînes de caractères primitives telles que “Hello World” ne peuvent pas avoir de propriétés ou de méthodes, car ce ne sont pas des objets.

Cependant, le langage JavaScript permet d’utiliser des méthodes et des propriétés avec des valeurs primitives, car celles-ci sont traitées comme des objets au moment de l’exécution du script.

Le JavaScript met à disposition des fonctions particulières permettant de travailler sur les chaînes de caractères.

## Trouver une chaîne dans une chaîne

### Fonction indexOf()

La fonction ```indexOf()``` retourne la position de la **première** occurrence d’un mot spécifique au sein d’une chaîne de caractère. 

Exemple :

```js
var x = "Ceci est une chaine de caractères";
console.log(x.indexOf("chaine"));
```

__Remarque__ : Le langage JavaScript, comme beaucoup d’autres langages informatiques, commence à compter à partir de **zéro**, non pas à partir de un. 

### Fonction lastIndexOf()

Cette fonction retourne la position de la **dernière** occurrence d’un mot spécifique au sein d’une chaîne de caractères.

Exemple : 

```js
var x = "Ceci est une chaine de caractères dans laquelle nous allons trouver une chaine spécifique";
console.log(x.indexOf("chaine"));
```

__Remarque__ : Ces deux fonctions retournent **-1** si l’occurrence n’a pas été trouvée.

### Préciser la position de départ

Les fonctions ```indexOf()``` et ```lastIndexOf()``` acceptent un second paramètre : la position de départ de la recherche. 

__Remarque__ : La fonction ```lastIndexOf()``` recherche une occurrence en partant de la fin de la string et en allant vers le début.

Exemple :

```js
var x = "Ceci est une chaine de caractères";
console.log(x.indexOf("chaine", 10));
```

Dans cet exemple, la recherche du mot *chaine* au sein de la chaine de caractères **x** démarre à partir du 10ème caractère.

## Rechercher une chaîne dans une chaîne

La méthode ```search()``` cherche une valeur spécifique au sein de la chaîne de caractère, et retourne la position de la correspondance entre les deux. 

Exemple :

```js
var x = "Ceci est une chaine de caractères";
console.log(x.search("chaine"));
```

__Remarque__ : Les deux fonctions ```indexOf()``` et ```search()``` ne sont pas pareilles. Voici les principales différences entre ces deux fonctions :

- La fonction ```search()``` ne peut pas recevoir un deuxième paramètre permettant de préciser la position de départ de la recherche. 
- La fonction ```indexOf()``` ne permet de rechercher des expressions régulières

## Extraire des chaînes de caractères

### La fonction slice()

La fonction ```slice()``` permet d’extraire une partie d’une chaîne de caractères et de retourner le morceau extrait dans une nouvelle *string*.

Cette fonction prend deux paramètres :

- La position à laquelle commencer l’extraction
- La position à laquelle terminer l’extraction. 

__Rappel__ : Le langage JavaScript compte à partir de 0 et non de 1.

Exemple :

```js
var y = "Ceci est une chaîne de caractères";
console.log(y.slice(13, 19));
```

Dans cet exemple, le mot “chaîne” est extrait de la *string* ```y```, car il se trouve entre le 13ème et le 19ème caractère.

#### Paramètres négatifs

Si des valeurs négatives sont passées en paramètres de la fonction ```slice()```, alors le comptage des caractères commence depuis la fin de la chaîne. 

Exemple :

```js
var y = "Ceci est une chaîne de caractères";
console.log(y.slice(-21, -15));
```

Dans cet exemple, le mot “chaîne” est retourné par la console, car il se trouve entre le 15ème et le 21ème caractère en partant de la fin de la chaîne (sachant que le comptage s’effectue à partir de 0).

#### Paramètre unique

Si un seul paramètre est passé à ```slice()```, alors l’extraction s’effectue à partir du Nème caractère spécifié et jusqu’à la fin de la chaîne de caractères. 

Exemple :

```js
var y = "Ceci est une chaîne de caractères";
console.log(y.slice(13));
```

Dans l’exemple ci-dessus, la chaîne suivante est extraite et retournée par la console : “chaîne des caractères”, car l’extraction commence au 13ème caractère et se poursuit jusqu’à la fin de la chaîne, puisqu’un seul paramètre est passé à ```slice()```.

### La fonction substring()

Cette fonction est similaire à ```slice()``` à ceci près qu’elle n’accepte les valeurs négatives.

Exemple : 

```js
var y = "Ceci est une chaîne de caractères";
console.log(y.substring(13,19));
```

Dans cet exemple, le mot “chaîne” est extrait de la *string*.

### La fonction substr()

Cette fonction est également similaire à ```slice()```. La seule différence est que le second paramètre reçu donne la taille du morceau à extraire.

Exemple :

```js
var y = "Ceci est une chaîne de caractères";
console.log(y.substr(13, 6);
```

Dans cet exemple, le mot “chaîne” est récupéré, car c’est le mot qui se trouve au 13ème caractère et qui a 6 caractères (le deuxième paramètre passé à ```substr()```).

Si le deuxième paramètre n’est pas précisé, alors ```substr()``` extrait le reste de la chaîne de caractères.

De même, si le premier paramètre passé est une valeur négative, alors la position sera comptée à partir de la fin de la chaîne de caractères.

## Remplacer le contenu d’un chaîne de caractères

La fonction ```replace()``` permet de remplacer un morceau d’une chaîne de caractères pas un autre. 

Exemple :

```js
chaine = "Ceci est une chaîne de caractères";
var y = chaine.replace("chaine de caractères", "string");
```

Dans cet exemple, "chaîne de caractères” est remplacé par “string”.

__Remarque__ : En fait, la fonction ```replace()``` ne remplace pas le contenu directement dans la chaîne sur laquelle elle est appelée, mais retourne une nouvelle *string*.

Par défaut, cette fonction remplace seulement la première occurrence et est sensible à la casse ; cela signifie que ```replace()``` considère qu’un même mot écrit en majuscule et en minuscule sont différents. 

Exemple :

```js
chaine = "Ceci est une chaîne de caractères";
var y = chaine.replace("CHAINE DE CARACTÈRES", "string");
```

Cet exemple ne fonctionne pas, car pour ```replace()```, “chaîne de caractères” est strictement différent de “CHAINE DE CARACTÈRES”.

Pour régler ce problème de sensibilité à la casse, il faut utiliser une **expression régulière** avec le drapeau ```/i```.

Exemple :

```js
chaine = "Ceci est une chaîne de caractères";
var y = chaine.replace(/CHAINE DE CARACTÈRES/i, "string");
```

Cette fois, cet exemple fonctionne, car l’expression régulière ```/CHAINE DE CARACTÈRES/i``` permet de faire en sorte que ```replace()``` ne soit pas sensible à la casse. 

__Remarque__ : Lorsqu’une expression régulière est utilisée, elle n’est pas entourée de guillemets. 

Un peu plus haut dans ce chapitre, il a été évoqué le fait que par défaut, ```replace()``` ne s’occupait que de la première occurrence. Pour “contourner” cela, une expression régulière, là encore, est utilisée, avec le drapeau ```/g```.

Exemple :

```js
chaine = "Ceci est une chaîne qui va être remplacée par une autre chaîne";
var y = chaine.replace(/chaine/g, "string");
```

Ici, toutes les occurrences du mot "chaîne" sont remplacées par le mot “string”.

## Convertir en majuscule et en minuscule

### Convertir en majuscule

Pour convertir une chaîne de caractères en majuscule, la fonction ```toUpperCase()``` est utilisée.

Exemple :

```js
var x = "Ceci est un chaîne de caractères";
var y = x.toUpperCase(); // Ici, la string est convertie en majuscule
```

### Convertir en minuscule

Pour convertir une chaîne de caractères en minuscule, il faut utiliser la fonction ```toLowerCase()```. Son utilisation est la même que la fonction ```toUpperCase()```.

Exemple :

```js
var x = "CECI EST UNE CHAÎNE DE CARACTÈRES";
var y = x.toLowerCase(); // Ici, la string est convertie en minuscule
```

## Concaténation de string

En plus de l’opérateur ```+```, le langage JavaScript met à disposition une fonction permettant de concaténer les chaînes de caractères : la fonction ```concat()```.

Exemple :

```js
var texte = "Bonjour ".concat("le monde !");
```

Ici, la chaîne de caractères **texte** ressemble désormais à cela : “Bonjour le monde !”.

__Remarque__ : Toutes les fonctions utilisées pour les chaînes de caractères ne modifient pas la string de base, mais en retournent simplement une nouvelle. En d’autre termes, les chaînes de caractères ne peuvent pas être modifiées mais simplement remplacées. 

## La fonction trim()

Cette fonction élimine tous les espaces blancs autour d’une chaîne de caractères. 

Exemple :

```js
var str = "   	Hello World!    	";
alert(str.trim());
```

Ici, lors du chargement du script, une pop-up s’affiche contenant le texte “Hello World!”. Les espaces blancs autour de la *string* ont donc bien été supprimés, grâce à ```trim()```.

## Fonctions de padding

Depuis 2017, JavaScript met à disposition deux fonctions permettant de rajouter certains caractères afin d’atteindre une longueur de chaîne de caractères définie. 

Pour ce faire, il existe deux fonctions.

### Fonction padStart()

Cette fonction permet de rajouter un caractère en **début** de chaîne, et reçoit les deux paramètres suivant :

- La longueur que la chaîne doit avoir
- La caractère à ajouter en début de chaîne

Exemple :

```js
var y = "24"
y = y.padStart(4, 0);
```

Cet exemple retourne le résultat suivant : 0024, car la fonction ```padStart()``` va rajouter les deux 0 afin de créer, comme il le lui a été demandé, un chaîne de 4 caractères. 

### La fonction padEnd()

Cette fonction est la même que celle ci-dessus, et son utilisation est identique. La seule différence est que ```padEnd()``` ajoute le caractère en fin de chaîne. 

Exemple :

```js
var y = "24"
y = y.padEnd(4, 0);
```

Ici, la chaîne de caractères retournée est 2400.

## Extraire des caractères

Tout comme il est possible d’extraire une chaîne d’une autre chaîne, JavaScript permet également d’extraire un caractère d’une chaîne de caractères. 

Pour ce faire, il existe 3 fonctions.

## La fonction charAt()

Cette fonction retourne un caractère situé à une position spécifique au sein de la chaîne de caractères.

Exemple :

```js
var y = "Bonjour le monde !";
y.charAt(3);
```

Cet exemple retourne le caractère “j”, car c’est celui situé à la troisième position au sein de la chaîne ```y```. Il ne faut pas oublier que le comptage commence à partir de 0 en JavaScript.

### La fonction charCodeAt()

La fonction ```charCodeAt()``` retourne le code “unicode” d’un caractère situé à une place spécifique au sein d’une chaîne de caractères.

Exemple :

```js
var y = "Bonjour le monde !";
y.charCodeAt(3);
```

Ici, le résultat retourné est **106**, car c’est l’unicode correspondant au caractère ‘j’.

## Accès via l’index de la propriété

Depuis 2005, JavaScript permet d’utiliser l’accès via l’index de propriété ([ ]) pour extraire un caractère situé à une position spécifiée au sein d’une chaîne de caractères.

Exemple :

```js
var y = "Bonjour le monde !";
y[3];
```

Dans l’exemple ci-dessus, le caractère retourné est ‘j’, car c’est celui qui est situé à la position 3 au sein de la *string* ```y```.

## Convertir une chaîne de caractères en array

Une chaîne de caractères peut être transformée en array grâce à la fonction ```split()```. Cette fonction reçoit en valeur le séparateur à utiliser. 

Si aucun séparateur n’est passé en paramètre à la fonction ```split()```, l’array retourné contient l’ensemble de la chaîne de caractères à l’index [0].

De plus, si les guillemets sont utilisés sans préciser de séparateur, alors tous les caractères contenus dans la chaîne seront retournés comme un seul caractère.

Exemple :

```js
var txt = "a,b,c,d,e";
txt.split("|");
```