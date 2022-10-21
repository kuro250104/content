“Hoisting” est le nom donné au comportement par défaut de JavaScript quant au fait de bouger les déclarations vers le haut.

## Les déclarations JavaScript sont “hoistées”

Le langage JavaScript permet de déclarer une variable après qu’elle a été utilisée. En d’autres termes, il est possible d’utiliser une variable avant même qu’elle n’ait été déclarée. 

Exemple :

```js
x = 5;
console.log(x);
var x;
```

Pour comprendre l’exemple ci-dessus, il est nécessaire de comprendre le principe de hoisting en JavaScript. Lors de l’exécution du script le langage va remonter la déclaration de variable - peu importe où elle est réellement située dans le code - en haut de la portée actuelle (en haut du script ou de la fonction).

## Mots-clés let et const

Les variables déclarées avec ```let``` et ```const``` sont remontées en haut du bloc, mais ne sont pas initialisées. Cela veut dire que le bloc de codes sait que la variable existe, mais celle-ci ne peut pas être utilisée tant qu’elle n’a pas été initialisée. 

Utiliser une variable ```let``` avant de l’avoir déclarée retourne, à coup sûr, une ```referrenceError```.

De même, utiliser une variable ```const``` avant de l’avoir déclarée retourne une ```syntaxError``` et le code ne s'exécutera tout simplement pas.

## Initialisation et hoisting

Il est important de comprendre que ce sont simplement les **déclarations** qui sont hoistées, et non les initialisations. 

## Déclarer les variables en haut du scope

Une des bonnes pratiques à adopter, en JavaScript, est de toujours déclarer ses variables en haut du scope. En effet, s’il est mal maîtrisé, le hoisting peut causer des bugs dans un programme.