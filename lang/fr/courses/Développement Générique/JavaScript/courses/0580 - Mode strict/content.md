“**use strict**” n’est pas une déclaration, mais une expression littérale qui n’existait pas dans les versions antérieures à la version 5 du langage. 

Cette directive permet d’indiquer aux navigateurs que le code doit être exécuté en mode strict, qui est un mode beaucoup plus restrictif. Cela aide néanmoins à écrire du code plus propre, car ce mode ne permet pas, par exemple, de pouvoir utiliser des variables qui n’ont pas été préalablement déclarées. C’est un mode plus restrictif, en quelque sorte. 

Cette directive ne fonctionne pas sur Internet Explorer 9 et antérieur.

__Remarque__ : “**use strict**” est une simple chaîne de caractères, donc si un navigateur ne sait pas l’interpréter, cela ne retournera pas pour autant une erreur.

## Déclarer le mode strict

Ce mode est déclaré en plaçant la directive ```use strict``` en **première ligne** d’un programme JavaScript ou d’une fonction. 

En plaçant cette directive en haut d’un code lui donnera une portée globale ; c’est donc la **totalité** du code qui est exécuté en mode strict. 

Exemple :

```js
"use strict";
x = 3.14;
```

Le code ci-dessus retourne une erreur, car la variable x n’a pas été déclarée avant d’être utilisée. 

En revanche, déclaré au sein d’une fonction, le mode strict a une portée **locale**. C’est donc **seulement** la fonction qui est exécutée en mode strict. 

Exemple :

```js
x = 3.14; 
myFunction();

function myFunction() {
    "use strict";
    y = 3.14; 
}
```

Ici, il n’y a que la fonction qui retourne une erreur. En effet, le mode strict est déclaré en son sein - il a donc une portée locale - et ne permet donc pas d’utiliser une variable sans l’avoir déclarée avant. 

## La syntaxe “use strict”

La syntaxe évoquée dans le point précédent pour déclarer le mode strict a été conçue afin de correspondre aux versions plus anciennes de JavaScript. 

Ainsi, compiler une expression telle que 4+5 ou une chaîne de caractère ne crée pas d’“effet secondaire”. Le code est simplement compilé dans une variable inexistante et meurt. 

Donc ```use strict``` importe réellement pour les nouveaux compilateurs qui “comprennent” sa signification. 

## Pourquoi utiliser le mode strict ?

Il existe plusieurs raisons pour utiliser le mode strict. La première est le fait que ce mode rend plus facile l’écriture de code JavaScript “sécurisé”.

Ce mode permet également de changer les “mauvaises syntaxes” - auparavant acceptées - en erreurs réelles. 

À titre d’exemple, en JavaScript “normal”, une variable avec une faute de frappe créait une nouvelle variable globale. En mode strict, cela va jeter une erreur, rendant impossible le fait de créer une nouvelle variable globale par accident. 

Autre exemple : en JavaScript normal, un développeur ne recevra jamais une erreur pour avoir assigné une valeur à une propriété non-éditable. Cela n’est pas le cas en mode strict. 

De manière plus générale, en mode strict, toute assignation à une variable non-éditable, à une propriété dite “getter-only”, à une propriété inexistante, à une variable inexistante ou encore à un objet inexistant jettera automatiquement une erreur.

## Ce qui n’est pas autorisé en mode strict

Voici une liste non-exhaustive de tout ce qui n’est pas autorisé en mode strict. 

### Ne pas déclarer une variable

Comme évoqué à plusieurs reprises dans ce cours, en mode strict, utiliser une variable sans l’avoir préalablement déclarée retourne une erreur.

Exemple :

```js
"use strict";
x = 3.14;
```

Cet exemple retourne une erreur, car le code est exécuté en mode strict et la variable x  est utilisée sans avoir été déclarée auparavant. 

__Remarque__ : Les objets sont également des variables.

### Ne pas déclarer un objet

Comme pour les variables, utiliser un objet sans l’avoir préalablement déclaré n’est pas permis en mode strict. 

Exemple :

```js
"use strict";
x = {p1:10, p2:20};
```

Ce code retourne une erreur, car l’objet ```x``` est utilisé sans avoir été préalablement déclaré.

### Effacer une variable ou un objet

En mode strict, effacer une variable ou un objet avec le mot-clé ```delete``` est interdit. 

Exemple :

```js
"use strict";
let x = 3.14;
delete x; 
```

### Effacer une fonction

De même, lorsque le mode strict est activé, effacer une fonction avec ```delete``` n’est pas autorisé. 

Exemple :

```js
"use strict";
function x(p1, p2) {};
delete x;
```

### Dupliquer le nom d’un paramètre

Dupliquer le nom d’un paramètre retourne une erreur lorsque le mode strict est activé. 

Exemple :

```js
"use strict";
function x(p1, p1) {};
```

Dans cet exemple, la dernière ligne retourne une erreur en mode strict, car la fonction ```x``` reçoit deux fois un paramètre avec le nom ```p1```.

### Les expressions numériques octales

Les expressions numériques octales ne sont pas autorisées en mode strict.

Exemple :

```js
"use strict";
let x = 010;
```

### L’échappement des expressions numériques octales

De même, en mode strict, échapper une expression numérique octale retourne une erreur. 

Exemple :

```js
"use strict";
let x = "\010";
```

### Les propriétés en lecture seule

En mode strict, écrire dans une propriété en lecture seule n’est pas autorisé. 

Exemple :

```js
"use strict";
const obj = {};
Object.defineProperty(obj, "x", {value:0, writable:false});

obj.x = 3.14;
```

### Écrire dans une propriété get-only

En mode strict, il est impossible de modifier directement la valeur d’une propriété accessible seulement via un *getter*. 

Exemple :

```js
"use strict";
const obj = {get x() {return 0} };

obj.x = 3.14;
```

### Propriétés ineffaçables

Effacer, grâce à ```delete```, une propriété qui ne peut pas l’être retourne une erreur.

Exemple :

```js
"use strict";
delete Object.prototype;
```

### Utiliser un mot-clé JavaScript comme nom de variable

Ci-dessous, la liste des mot-clés JavaScript qui, lorsqu’ils sont utilisés comme nom de variable retournent une erreur en mode strict :

- ```eval```
- ```arguments```

### La déclaration with

En mode strict, ```with``` n’est pas utilisable.

Exemple :

```js
"use strict";
with (Math){x = cos(2)};
```

### Eval() et la création de variable dans la portée

Pour des raisons de sécurité, la fonction ```eval()``` n’est pas autorisée à créer des variables dans la portée dans laquelle elle est appelée. 

Exemple :

```js
"use strict";
eval ("let x = 2");
alert (x); 
```

### Le mot-clé this

En mode strict, le mot-clé this n’agit pas de la même manière qu’en mode “normal”. En mode normal, ```this``` réfère à l’objet qui a appelé la fonction.

Si l’objet n’est pas spécifié, la fonction en mode strict retourne ```undefined``` tandis qu’en mode normal, les fonctions retournent l’objet global, à savoir ```window```. 

Exemple :

```js
"use strict";
function myFunction() {
    alert(this); // Retourne "undefined"
}
myFunction();
```