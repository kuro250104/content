JavaScript permet de parcourir les données contenues dans un tableau, afin de, par la suite, pouvoir effectuer différentes opérations avec ces données.

## La fonction forEach()

Pour parcourir un tableau, la fonction ```forEach()``` peut-être utilisée. ```forEach()``` appelle une fonction dite de “rappel” - communément appelée fonction *callback* - sur chaque élément contenu dans le tableau.

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];
let txt = "";
numbers.forEach(maFonction);

function maFonction(value, index, array) {
    txt += value + "<br>";
}
```

Dans cet exemple, la fonction callback ```maFonction``` est passée en paramètre de la fonction ```forEach()```. ```maFonction``` est appelée pour chaque valeur du tableau.

## La fonction map()

Cette fonction crée un nouveau tableau en utilisant une fonction sur chaque élément du tableau. Cependant, ```map()``` n’exécute pas la fonction pour les éléments du tableau sans valeur. De plus, ```map()``` ne change pas le tableau original.

Exemple :

```js
const numbers1 = [45, 4, 9, 16, 25];
const numbers2 = numbers1.map(myFunction);

function myFunction(value, index, array) {
    return value * 2;
}
```

Ici, un deuxième tableau est créé. Ce tableau est initialisé avec un appel à la fonction ```map()``` sur le premier tableau : ```numbers1.map()```.

Ensuite, le nom de la fonction de rappel est passé en paramètre de ```map()```, afin que cette fonction de rappel soit parcourue pour chaque valeur du tableau. 

Enfin, la fonction de rappel ```myFunction``` est créée. Son but est de multiplier chaque valeur du tableau par deux puis de retourner le résultat.

## La fonction filter()

Cette fonction crée un nouvel array contenant les valeurs du premier tableau ayant passé un test. 

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];
const over18 = numbers.filter(myFunction);

function myFunction(value, index, array) {
    return value > 18;
}
```

Dans cet exemple, les valeurs stockées dans le nouvel array créé par la fonction ```filter()``` sont celles strictement supérieures à 18 (ici, **25** et **45**).

## La fonction reduce()

Cette méthode traite chaque entrée numérique d’un tableau de la gauche vers la droite afin de réduire le “total” à une seule valeur.

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];
numbers.reduce(myFunction);

function myFunction(total, value) {
    return total + value;
}
```

Dans cet exemple, la fonction ```reduce()``` fait appel à une fonction callback, dont le but est d’additionner chaque valeur entre elles et de retourner le résultat. Le résultat obtenu est donc 99.

__Remarque__ : La fonction ```reduce()``` peut prendre une valeur initiale qui est ajoutée au total calculé. 

Exemple :

```js
numbers.reduce(myFunction, 100);
```

Ici, le résultat retourné est 199, car 100 - qui est la valeur initiale - est ajouté au total calculé.

## La fonction every()

Cette fonction permet de sélectionner les entrées qui remplissent une certaine condition.

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];

var over18 = numbers.every(myFunction);

function myFunction(value) {
	return value > 18;
}
```

Cet exemple retourne les valeurs 25, 45, car ce sont les seules entrées à être supérieures à 18.

## La fonction some()

Cette fonction permet de faire la même chose que la fonction évoquée au point précédent.

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];

var over18 = numbers.some(myFunction);

function myFunction(value) {
	return value > 18;
}
```

Dans cet exemple, les valeurs retournées sont également 25 et 45.

## La fonction indexof()

Cette fonction prend en paramètres une entrée du tableau et retourne l’index de position dudit élément.

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];

numbers.indexOf(45);
```

Cet exemple retourne 0, qui est l’index de position de l’élément **45** dans le tableau ```numbers```.

Cette fonction prend obligatoirement un paramètre - l’élément dont il faut obtenir la position -, mais peut également recevoir un second paramètre : la position à partir de laquelle il faut commencer la “recherche”. Il est toutefois important de noter qu’une valeur négative passée en second paramètre commencera la recherche à la position spécifiée, en partant de la fin du tableau. 

__Remarques__ :

- Si aucun élément ne correspond à celui recherché, la fonction retourne **-1**.
- Si l’élément recherché est répété plusieurs fois dans le tableau, seule l’index de position de la première occurrence est retournée.

## La fonction lastIndexOf()

Cette fonction est la même que la précédente, à la seule différence ```lastIndexOf()``` retourne la position de la dernière occurrence. 

Les paramètres reçus sont les mêmes que la fonction détaillée au point précédent.

Exemple :

```js
const numbers = [45, 4, 9, 16, 25, 45];
numbers.lastIndexOf(45);
```

Cet exemple retourne la valeur 5, qui est l’index de position correct de la dernière occurrence de 45.

## La fonction includes()

Cette fonction permet de tester si un élément est présent dans un tableau ou non. La fonction ```includes()``` retourne **true** si l’élément est présent dans le tableau, et **false** s’il ne l’est pas. 

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];
numbers.includes(9); // Ici la includes() retourne true car l'élément 9 est bien présent dans le tableau
numbers.includes(100); // Ici, false est retourné, car 100 n'existe pas dans le tableau.
```

## La fonction find()

Cette fonction permet de retourner le **premier** élément qui réussit un test.

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];
let firstNumber = numbers.find(myFunction);
function myFunction(value, index, array) {
	return value > 18;
}
```

Cet exemple retourne le premier élément du tableau qui est supérieur à 18, c’est-à-dire 45.

## La fonction findIndex()

Cette fonction permet de retourner l’index de position de la première valeur qui passe un test.

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];
let firstNumber = numbers.find(myFunction);
function myFunction(value, index, array) {
	return value > 18;
}
```