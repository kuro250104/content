L’objet Math permet de manipuler les nombres en y effectuant des tâches mathématiques.

## Présentation de l’objet Math

Contrairement aux autres objets en JavaScript, Math n’a pas de constructeur. De plus, c’est un objet statique - qui ne change pas -, et sa particularité est que les méthodes et les propriétés de l’objet Math sont utilisables sans avoir besoin de créer un nouvel objet math.

## Les propriétés de Maths (constants)

Maths, comme tout objet qui se respecte, contient des propriétés. Celles-ci sont accessibles en utilisant la syntaxe suivante :

```js
Math.nomDeLaPropriété;
```

Une des propriétés de l’objet Math les plus utilisées est : ```Math.PI```, qui retourne le nombre PI.

Ces propriétés sont des constantes, cela signifie qu’elles ne changent jamais. 

La liste complète des propriétés de l’objet Math est disponible dans la documentation officielle.

## Les méthodes de l’objet Math

Tout comme Math contient un certain nombre de propriétés, cet objet met également à disposition un certain nombre de méthodes permettant de réaliser des opérations et tâches mathématiques sur les nombres.

Avec l’objet Math, la syntaxe pour accéder à une méthode est la suivante :

```js
Math.méthode.(nombre);
```

### Convertir un nombre en nombre entier

Il existe 4 méthodes permettant de convertir un nombre - décimal ou non - en nombre entier. 

#### La méthode round()

```Math.round(x)``` retourne le nombre entier le plus proche.

Exemple :

```js
Math.round(5.6); // Ici, la méthode retourne 6, car c'est le nombre entier le plus proche
```

#### La méthode ceil()

Cette méthode retourne le nombre entier **supérieur** le plus proche du nombre passé en paramètre. 

Exemple :

```js
Math.ceil(3.3); // Ici, le nombre 4 est retourné
```

#### La méthode floor()

```Math.floor()``` retourne le nombre entier **inférieur** le plus proche du nombre passé en paramètre. 

Exemple :

```js
Math.floor(3.9); // Retourne 3
```

#### La méthode trunc()

La méthode ```Math.trunc(x)``` - *trunc* signifiant *truncate*, tronqué en anglais - retourne la partie “entière” du nombre x passé en paramètre. 

Exemple :

```js
Math.trunc(4.9); // Ici, trunc() retourne 4, car c'est la partie entière du nombre 4.9
```

### Autres méthodes de l’objet Math

L’objet Math n’a pas que des méthodes permettant d’arrondir un nombre pour le rendre entier. Il met également à disposition d’autres méthodes permettant de réaliser des opérations un peu plus complexes.

#### La méthode Math.sign()

Cette méthode retourne le signe du nombre passé en paramètre. En d’autres termes, cette méthode indique si le nombre est positif, nul ou négatif.

```Math.sign()``` retourne 1 si le nombre passé en paramètre est positif, -1 s’il est négatif, et 0 s’il est nul.

Exemple :

```js
Math.sign(5); // Retourne 1, car 5 est positif
Math.sign(-5); // Retourne -1 car 5 est négatif
Math.sigh(0); // Retourne 0 car c'est un nombre nul
```

#### La méthode Math.pow()

Cette méthode permet de faire un calcul avec puissance. 

Exemple :

```js
Math.pow(5,2); // Retourne 25 
```

#### La méthode Math.sqrt()

Cette méthode retourne la racine carrée d’un nombre.

Exemple :

```js
Math.sqrt(25); // Retourne 5
```

#### La méthode Math.abs()

```Math.abs()``` retourne l’absolu d’un nombre, c’est-à-dire le nombre positif de ce même nombre. 

Exemple :

```js
Math.abs(-25); // Retourne 25
```

#### La méthode Math.sin()

Cette méthode retourne le sinus (un nombre situé entre -1 et 1) de l’angle, en radian, passé en paramètre.

Exemple :

```js
Math.sin(23); // Retourne 0.8462204041751706
```

#### La méthode Math.cos()

Cette fonction permet de retourner le cosinus - c’est-à-dire, comme pour le sinus, une valeur située entre -1 et 1 - de l’angle en radian passé en paramètres. 

Exemple :

```js
Math.cos(23); // Retourne -0.5328330203333975
```

#### Les méthodes Math.min et Math.max

Ces méthodes sont utilisées pour trouver le plus petit nombre (Math.min) ou le plus grand nombre (Math.max) au sein d’une liste d’arguments. 

Exemple :

```js
Math.min(25, 49, 10, 3, 50); // Retourne 3
Math.max(25, 49, 10, 3, 50); // Retourne 50
```

#### La méthode Math.random()

Cette fonction retourne un nombre choisi au hasard et situé entre 0 inclus et 1 exclu.

Exemple :

```js
Math.random(); // Retourne, ici, 0.06933473008610425
```
