Le langage JavaScript permet de manier les dates comme un objet. 

Par défaut, le langage JavaScript utilise la date et l’heure du navigateur utilisé et affiche la date comme une chaîne de caractères.

Exemple :

```js
Tue Jun 29 2021 23:07:25 GMT+0200 (heure d’été d’Europe centrale)
```

## Créer un objet date

Les objets dates sont créés avec le constructeur ```new Date()```.

Il existe 4 moyens de créer un objet date :

--- ```new Date()```
--- ```new Date(year, month, day, hours, minutes, seconds, milliseconds)```
--- ```new Date(milliseconds)```
--- ```new Date(date string)```

### new Date()

Le constructeur ```new Date()``` permet de créer un objet date qui affiche la date et l’heure **actuelle**.

Exemple :

```js
const day = new date();
```

Voici ce que retourne l’exemple ci-dessus :

```js
Tue Jun 29 2021 23:29:06 GMT+0200 (heure d’été d’Europe centrale).
```

__Remarque__ : Les dates sont statiques, c’est-à-dire qu’elles ne défilent pas à l’écran.

### new Date(day, month, year, etc…)

Passer des paramètres au constructeur ```new date()``` permet de créer un objet ```date()``` avec une date et une heure spécifiques.

__Remarque__ : En JavaScript, les mois sont comptés de 0 à 11. Ainsi, 0 représente le mois de janvier, et 11 le mois de décembre.

- **7 chiffres** permettent de spécifier, dans cet ordre : année, mois, jour, heures, minutes, secondes, millisecondes : ```const d = new Date (2021, 02, 12, 03, 24, 25, 55)```
- **6 chiffres** permettent de spécifier, dans cet ordre : année, mois, jour, heures, minutes, secondes : ```const d = new Date (2021, 02, 12, 03, 24, 25)```
- **5 chiffres** permettent de spécifier : année, mois, jour, heures, minutes : ```const d = new Date (2021, 02, 12, 03, 24)```
- **4 chiffres**  permettent de spécifier : année, mois, jour, heures : ```const d = new Date (2021, 02, 12, 03)```
- **3 chiffres** permettent de spécifier : année, mois, jour : ```const d = new Date (2021, 02, 12)```
- **2 chiffres** permettent de spécifier : année, mois : ```const d = new Date (2021, 02)```

__Remarque__ : Le mois ne doit pas être omis. Si un seul chiffre est passé en paramètre du constructeur, ce chiffre est considéré comme des millisecondes.

#### Années avec 1 ou 2 chiffres

Si une année est écrite avec 1 ou 2 chiffres, elle s'affiche malgré tout avec 4 chiffres. 

Exemple :

```js
const d = new Date(95, 03); // Ici, la date s'affiche ainsi March 1995
```

### new Date(dateString)

Cette manière de créer un objet date permet de créer une date en chaîne de caractères.

Exemple :

```js
const d = new Date("October 13, 2014 11:13:00");
```

## JavaScript stocke les dates en millisecondes

JavaScript stocke les dates comme le nombre de millisecondes écoulées depuis le 01 janvier 1970 00:00:00 UTC.

### new Date(milliseconds)

Cette manière d’implémenter permet crée un nouvel objet date de **0 fois plus les millisecondes**.

__Exemple__ :

```js
const d = new Date(0);
```

Cet exemple retourne la date du 01 janvier 1970 00:00:00.

## Fonctions utilisables avec l’objet date

Lorsqu’un objet date est créé, une série de fonctions natives à JavaScript est mise à disposition afin de pouvoir manipuler les dates.

Ces fonctions permettent de définir ou d’obtenir l’année, le mois, le jour, l’heure, les minutes, les secondes et les millisecondes.

### Afficher les dates

Comme évoqué dans l’introduction, par défaut, en JavaScript, une date est affichée sous forme de chaîne de caractères. 

#### La fonction toUTCString()

Cette fonction permet de convertir une date en chaîne de caractères UTC (format d’affichage standard).

Exemple :

```js
const d = new Date();
d.toUTCString();
```

#### toDateString()

Cette fonction convertit une date en un format un peu plus lisible :

Exemple :

```js
const d = new Date();
d.toDateString();
```

#### toISOString()

Cette méthode permet de convertir une date en une chaîne de caractères ISO - autre format d’affichage standard.

Exemple :

```js
const d = new Date();
d.toISOString();
```