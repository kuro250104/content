Les booléens sont utilisés dans tous les langages informatiques. Les développeurs font souvent appel à eux, car ils permettent de tester si une égalité est vraie ou fausse.

En JavaScript il existe un type de données ```Booléen```, qui peut prendre une des deux valeurs suivantes : **true** (vrai) ou **false** (faux).

## La fonction Boolean()

Cette fonction permet de tester si une expression - ou une  variable - est vraie ou fausse.

Exemple :

```js
Boolean(2 > 3); // Retourne false
```

L’écriture de cette fonction peut-être simplifiée en utilisant l’une des deux écritures suivantes :

```js
(2 > 3); // Retourne false
2 < 3; // Retourne true
```

Si l’une des deux manières d’écrire ci-dessus est utilisée, attention tout de même à ce que la lisibilité et la compréhension du code ne soient pas impactées.

## Tout ce qui a une valeur est vrai

Par défaut, en JavaScript, tout ce qui a une valeur renvoi true.

Exemple :

```js
"Bonjour";
10;
10 + 5 + 4;
```

Tous ces exemples renvoient **true**.

## Tout ce qui n’a pas de valeur est faux

À contrario, par défaut, tout ce qui n’a pas de valeur renvoie faux. 

Exemple :

```js
var d;
Boolean(d); // La fonction, ici, renvoie faux car la variable d n'a pas de valeur

var texte = "";
Boolean(text); // Ici, faux est également retourné car la chaîne de caractères est vide
```