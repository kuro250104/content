Les opérateurs de comparaison et les opérateurs logiques sont utilisés afin de tester si une égalité - ou une expression - est vraie ou fausse.

## Opérateurs de comparaison

Ci-dessous, la liste des opérateurs de comparaison utilisables en Javascript :

- ```==``` : est l’opérateur d’égalité, signifiant “**est égal à**”. Exemple : ```x == 2; // Retourne true```
- ```===``` : est l’opérateur d’égalité parfaite. Il test si une égalité est vraie en valeur et en type. En d’autres termes, cet opérateur signifie “**est strictement égal à**”. Exemple : ```x === 5; // Retourne true```
- ```!=``` : est l’opérateur d’inégalité. Il signifie “**n’est pas égal à**”. Exemple : ```2 != 3;```
- ```!==``` : est l’opérateur de **stricte inégalité**. Exemple : ```"Bonjour" !== 2;```
- ```>``` : est l’opérateur permettant de tester une supériorité. Cet opérateur signifie “**est supérieur à**”. Exemple : ```3 > 2;```
- ```<``` : est l’opérateur permettant de tester une infériorité. Il signifie “**est inférieure à**”. Exemple : ```2 < 3;```
- ```>=``` et ```<=``` : sont les opérateurs permettant de tester si quelque chose est **inférieur/supérieur ou égal à**.Exemple : ```2 <= 3;``` et ```3 >= 2;```

### Utilisation

Les opérateurs de comparaison sont principalement utilisés dans des conditions, afin de tester si une expression est vraie ou fausse, et exécuter des actions en fonction. 

Exemple :

```js
if(x == 2) {
	text = "L'égalité est vraie";
}
```

## Opérateurs logiques

Ces opérateurs sont utilisés pour déterminer une logique entre des variables ou entre des valeurs.

Voici la liste des opérateurs logiques :

- ```&&``` : signifie “**et**”. Exemple : ```x == 2 && y == 2```
- ```||``` : signifie “**ou**”. Exemple : ```x == 2 || y == 2```
- ```!``` : signifie “**n’est pas**”. Exemple : ```!(x == y) // Ici, cela signifie littéralement x N'EST PAS égal à y```

## Opérateur conditionnel

JavaScript met également à disposition un opérateur conditionnel qui assigne une valeur à une variable en fonction d’une condition. 

Ce type d’expression est appelée “ternaire”. Elle permet d’économiser des lignes de codes, mais, au premier abord, peut sembler difficile à comprendre.

L’opérateur conditionnel est le point d’interrogation (?) et voici la syntaxe d’une expression ternaire :

```js
var nomDeVariable = (condition) ? valeur1 : valeur2;
```

Exemple :

```js
var ageVote = (age > 18) ? "Vous pouvez voter" : "Vous ne pouvez pas voter";
```

Dans un premier temps, la variable ```ageVote``` est créée. Ensuite, la condition teste si la valeur de la variable ```age``` est supérieur à 18. Si tel est le cas, le résultat retourné est “**Vous pouvez voter**” ; sinon, c’est “**Vous ne pouvez pas voter**” qui s’affiche sur l’écran de l’utilisateur.
