En programmation Objet, il existe des fonctions appelées *getters*, permettant d’accéder et d’obtenir certaines valeurs contenues dans un objet. 

Le langage JavaScript et l’objet ```date()``` n’échappent pas à cette règle. En effet, il existe un certain nombre de fonctions *getters*, qui permettent aux développeurs d’accéder à des valeurs contenues dans l’objet ```date()```.

## La fonction getTime()

Cette fonction retourne le nombre de **millisecondes** écoulées depuis le 1er janvier 1970.

Exemple :

```js
const d = new Date();
d.getTime();
```

Cet exemple retourne ```1579906800000```.

## La fonction getFullYear()

Cette fonction retourne l’année d’une date sous forme d’un nombre à 4 chiffres.

Exemple :

```js
const d = new Date();
d.getFullYear();
```

Cet exemple retourne 2021, qui est, effectivement, l’année en cours.

## La fonction getMonth()

Cette fonction permet de récupérer le mois dans une date. Cependant, le mois est retourné sous forme d’un nombre situé entre 0 et 11 ; 0 étant janvier et 11 étant décembre.

Exemple :

```js
const d = new Date();
d.getMonth(); // Retourne 5, donc juin, le 6ème mois de l’année
```

Cependant, pour retourner le nom du mois plutôt que son nombre, il suffit de créer un array, puis de sélectionner l’index placé à ```d.getMonth()```.

Exemple :

```js
const d = new Date();
const mois = ["Janvier", "Février", "Mars", "Avril", "Mai", "Juin", "Juillet", "Août", "Septembre", "Octobre", "Novembre", "Décembre"];
mois[d.getMonth()]; // Ici, c'est "Juin" qui est retourné, car il est placé à l'index mois[5]
```

## La fonction getDate()

Cette fonction permet de récupérer le jour du mois, sous forme d’un nombre entre 1 et 31.

Exemple :

```js
d.getDate(); // Ici, le nombre retourné est 30
```

## La fonction getDay()

Cette fonction permet de récupérer le jour de la semaine. 

__Remarque__ : Avec cette fonction, le jour de la semaine est retourné sous forme d’un nombre situé entre 0 (dimanche) et 6 (samedi).

Exemple :

```js
d.getDay(); // Ici, getDay() retourne 3 pour mercredi
```

Pour contourner ce problème et afficher le jour en toutes lettres, il est possible, comme pour les mois, de créer un array contenant le nom des jours, et de récupérer celui placé à l’index ```days.[d.getDay()]```.

Exemple :

```js
const days = ["Dimanche", "Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi"];
days[d.getDay()];
```

Cet exemple retourne “mercredi”, car c’est le jour situé à l’index ```days[d.getDay()]```, c’est-à-dire 3.

## La fonction getHours()

Cette fonction permet de récupérer l’heure d’une date, sous la forme d’un nombre situé entre 0 et 23.

Exemple :

```js
d.getHours(); // Ici, 9 est retourné.
```

## La fonction getMinutes()

Cette fonction permet de récupérer le nombre de minutes d’une date sous forme d’un nombre situé en 0 et 59.

Exemple :

```js
d.getMinutes(); // Cette ligne de code retourne 12
```

## La fonction getSeconds()

```getSeconds()``` récupère les secondes d’une date sous la forme d’un nombre situé entre 0 et 59.

Exemple :

```js
d.getSeconds(); // Ici, 25 est retourné
```

## La fonction getMilliseconds()

Cette fonction retourne le nombre de millisecondes dans une date, sous forme d’un nombre situé entre 0 et 999.

Exemple :

```js
d.getMilliseconds(); // Ici, 100 est retourné
```

## Les fonctions UTC

Les mêmes fonctions que celles détaillées dans les points précédents existent en UTC (en heure universelle). Pour ce faire, il suffit d’ajouter ```UTC``` après ```get```.

Exemple :

```js
d.getUTCHours(); // Ici, c'est l'heure universelle qui est retournée
```