Le JavaScript met à disposition 3 standards pour afficher les dates.

## Format de sortie des dates

Par défaut, le langage JavaScript retourne une date comme une chaine de caractères. 

## Date ISO

Le format ISO est le seul format, en JavaScript qui suit un standard d’affichage strict. 

Exemple :

```js
const d = new Date("2015-03-25");
```

### Dates ISO (Année, mois)

Les dates en ISO peuvent être écrites en ne spécifiant que l’année et le mois.

Exemple :

```js
const d = new Date("2015-03");
```

### Dates ISO (Année)

De même, le format de date ISO permet de seulement spécifier l’année - ce qui n’est pas possible avec un autre format, car si un seul chiffre est passé en paramètres du constructeur ```new Date()```, celui-ci est normalement considéré comme des millisecondes. 

Exemple :

```js
const d = new Date("2015");
```

### Dates ISO (date et heure)

Au format ISO, les dates peuvent également être accompagnées des heures, minutes et secondes. 

Pour ce faire, la date et l’heure sont séparées par la lettre majuscule **T**. L’heure UTC - dite heure universelle - est accompagnée de la lettre majuscule **Z**. 

Exemple :

```js
const d = new Date("2015-03-02T10:25:30Z");
```

__Remarque__ : Omettre le **T** ou le **Z** dans une chaîne de caractères au format date-heure donne des résultats différents en fonction des navigateurs.

## Fuseau horaire

En JavaScript, lorsque aucun fuseau horaire n’est spécifié lors de la définition ou de l’obtention d’une date, c’est celui du navigateur qui sera pris en compte. 

En d’autres termes, si une date est créée au format GMT et que l’utilisateur utilise un navigateur en France, alors la date et l’heure sont converties au fuseau horaire de Paris.

## Dates courtes en JavaScript

Le format de date raccourci, en JavaScript, doit respecter le format MM/DD/YYYY.

Exemple :

```js
const d = new Date("11/03/2020");
```

Dans cet exemple, la date définie est le 03 décembre 2020.

### Avertissements

Avec certains navigateurs internet, les mois ou les jours qui ne sont pas précédés de 0 peuvent produire une erreur.

Exemple :

```js
const d = new Date("2015-3-20");
```

Les formats de dates raccourcis YYYY/MM/DD et DD/MM/YYYY ne sont, nativement, pas définis. Ainsi, certains navigateurs tenteront de deviner le format, tandis que d’autres retourneront simplement ```NaN```.

## Dates longues en JavaScript

Les dates longues, en JavaScript, sont souvent écrites avec le format suivant : “MMM DD YYYY”.

Exemple :

```js
const d = new Date("Jan 25 2020");
```

Cependant, le format français est aussi accepté.

Exemple :

```js
const d = new Date("25 Jan 2020");
```

De plus, le mois peut-être écrit dans sa totalité ou de manière abrégée.

Exemple :

```js
const d = new Date("25 January 2020");
```

## Transformer une date en millisecondes

Il est possible de convertir une date définie sous forme d’une chaîne de caractères en millisecondes. Pour ce faire, la fonction ```Date.parse()``` doit être utilisée.

Cette fonction, en fait, retourne le nombre de millisecondes écoulées entre la date passée en paramètres en le 1er Janvier 1970.

Exemple :

```js
const milliseconds = Date.parse("25 January 2020");
```

Ici, la variable milliseconde contient la valeur suivante : ```1579906800000```.

Il est également possible d’utiliser les millisecondes pour créer un objet de type Date. 

Exemple :

```js
const milliseconds = Date.parse("25 January 2020");
const d = new Date(msec);
```