Tout comme il existe des *getters* pour les objets, permettant d’accéder aux valeurs contenues dans un objet, il existe également des setters permettant de modifier les valeurs contenues dans un objet. 

En JavaScript, les dates étant des objets, des *setters* sont mis à disposition afin de pouvoir les manipuler et les modifier.

## La fonction setFullYear()

Cette fonction permet de définir l’année sous la forme d’un nombre à 4 chiffres. 

Exemple :

```js
const d = new Date();
d.setFullyear(2021); // Ici, l'année est définie à 2021
```

Cette fonction peut également, mais de manière optionnelle, définir, dans cet ordre, le mois et le jour, en plus de l’année.

Exemple :

```js
const d = new Date();
d.setFullyear(2021, 0, 20); // Ici, le 20 janvier 2021 est défini
```

## La fonction setMonth()

Cette fonction permet de définir un mois sous forme d’un nombre situé entre 0 et 11, 0 étant janvier et 11 étant décembre.

Exemple :

```js
const d = new Date();
d.setMonth(3); // Ici, c'est le mois d'avril qui est définie
```

## La fonction setDate()

```setDate()``` permet de définir un jour du mois, sous forme d’un nombre situé entre 1 et 31.

Exemple :

```js
const d = new Date();
d.setDate(25); 
```

## La méthode setHours()

Cette fonction permet de définir une heure pour un objet date. Cette heure doit être définie sous la forme d’un nombre entre 0 et 23. 

Exemple :

```js
d.setHours(23);
```

## La fonction setMinutes()

Cette fonction permet de définir un nombre de minutes. Ce nombre est situé entre 0 et 59.

Exemple :

```js
d.setMinutes(55);
```

## La fonction setSeconds()

Comme pour les deux fonctions précédentes, cette fonction manipule également les heures, car elle permet de définir un nombre de secondes, situé entre 0 et 59.

Exemple :

```js
d.setSeconds(34);
```