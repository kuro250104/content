En programmation, le principe d’une boucle est d’exécuter un bout de programme un certain nombre de fois, sans que le développeur ait à retaper sans cesse la même ligne de code avec juste une donnée changeante. 

## Différents types de boucle

En Javascript, il existe 5 type de boucles - également appelées avec leur nom anglais *loop* :

- La boucle ```for``` : permet de faire une boucle sur un morceau de code un certain nombre de fois. C’est la boucle détaillée dans ce chapitre.
- La boucle ```for in``` : permet de faire une boucle sur les propriétés d’un objet. 
- La boucle ```for of``` : permet de boucler sur les valeurs d’un objet itérable.
- La boucle ```while``` : boucle sur un morceau tant qu’une condition spécifique est vraie.
- La boucle ```do while``` : Même chose que pour la boucle ```while```.

Ce cours traite des trois boucles for : ```for```, ```for in``` et ```for of```.

## La boucle for

### Syntaxe

Voici la syntaxe de la boucle for :

```js
for (condition1 ; condition2 ; condition3) {
	// Code à exécuter
}
```

Avant d’entrer dans la boucle, le programme lit la condition 1. Ensuite, la condition 2 définit la condition dans laquelle le programme doit être exécuté. Enfin, la condition 3 s’applique juste avant que le programme entre dans la boucle. Ensuite, le code contenu entre accolades est exécuté. 

Exemple :

```js
for (var i = 0 ; i < 5; i++) {
	console.log("Hello World"):
}
```

Dans cet exemple, la variable ```i``` est créé et initialisé à 0.

Ensuite le programme vérifie si ```i``` est inférieur à 5. Le cas échéant, ```i``` est incrémenté de 1 à chaque fois jusqu’à ce qu’il soit égal à 5, et le texte “Hello World” s’affiche dans la console.

En revanche, dès que ```i``` vaut 5, le programme sort de la boucle, car la condition 2 n’est plus remplie.

### La condition 1

La condition 1 est utilisée pour initialiser la variable utilisée dans la boucle. Cependant, en JavaScript, cette condition est optionnelle, car il peut arriver des cas où la variable est initialisée bien avant dans le programme.

Il est possible d'initialiser plusieurs variables dans la condition 1 - La seule obligation est que chaque déclaration de variable soit séparée par une virgule.

Exemple :

```js
for (var i = 0, longueur = cars.longueur, text = "" ; i < longueur ; i++) {
	text += car[i] + "<br />";
}
```

Si les variables sont initialisées avant la boucle, il est possible d’omettre la condition 1.

Exemple : 

```js
var i = 0, longueur = cars.longueur, text = "";
for (; i < longueur ; i++)
{
	text += car[i] + "<br />"
}
```

### La condition 2

La condition est utilisée afin d’“**évaluer**” la condition de la variable initiale. 

En d’autres termes, si la condition retourne **true**, alors la boucle s’exécute à nouveau, sinon elle s’arrête.

### La condition 3

La troisième et dernière condition au sein d’une boucle for est utilisée afin de modifier la valeur de la variable initiale. Cela est faisable en incrémentant cette variable (en utilisant  ```++```), en décrémentant (avec ```--```), ou avec une incrémentation positive (```i = i + 15```).

Cette condition n’est pas obligatoire, car il est également possible de faire cette modification de la variable initiale au sein même de la boucle. 

Exemple :

```js
var i = 0, longueur = cars.longueur, text = "";
for (; i < longueur ;)
{
	text += car[i] + "<br />";
    i++
}
```

Dans cet exemple, la condition 3 n’est pas déclarée dans les paramètres de la boucle ```for```, car l’incrémentation de i se fait au sein de la boucle. 

## La boucle for in

```for in``` est utilisée afin de “boucler” les propriétés d’un objet. 

### Syntaxe

Voici la syntaxe correcte pour la boucle ```for in``` :

```js
for (clé in objet) {
	// Code
}
```

Exemple :

```js
const user = { prenom: "Joe", nom: "Blow", age: 25};

var text = "";

for (var x in user) {
	texte += user[x];
}
```

Dans cet exemple, un objet ```user``` est créé. La boucle ```for in``` va ensuite parcourir les propriétés de l’objet ```user```. ```x``` est incrémenté pour chaque propriété et la variable ```text``` se voit assigner les valeurs des propriétés de l’objet. 

### For in et les tableaux

Cette boucle peut également être utilisée pour parcourir un tableau. 

Exemple :

```js
const numbers = [45, 4, 9, 16, 25];

let txt = "";
for (let x in numbers) {
    txt += numbers[x];
}
```

__Remarque__ : Si l’ordre est important, il est recommandé de ne pas utiliser la boucle for in pour parcourir un tableau, car l’ordre des index dépend de l’implémentation et les valeurs pourraient ne pas être accessibles dans l’ordre attendu. 

Si l’ordre des valeurs compte, il est recommandé d’utiliser, à la place, la fonction ```foreach()```.

#### La boucle Array.foreach()

Cette fonction appelle la même fonction callback pour chaque élément du tableau.

Exemple :

```js
numbers.forEach(maFonction);

function maFonction(value, index, array) {
    text += value;
}
```

Dans cet exemple, la fonction ```maFonction``` est appelée pour chaque élément du tableau et ajoute chaque valeur à la variable ```text```.

## La boucle for of

```for of``` permet de boucler sur les valeurs d’un objet. Elle permet de boucler sur du contenu itérable tel que des arrays ou des chaînes de caractères. 

### Syntaxe

Voici la syntaxe pour la boucle ```for of``` :

```js
for (variable of element_itérable) {
	// Code
}
```

Pour chaque itération, la valeur de la propriété suivante est assignée à la ```variable```.

Ici, ```element_iterable``` représente un objet qui a des propriétés itérables, tel qu’un array ou une chaîne de caractères.

### For of sur un array

Ci-dessous un exemple d’utilisation de la boucle ```for of``` pour parcourir un tableau :

```js
var cars = ["Volvo", "Nissan", "Renault"];
var text = "";

for(var x of cars) {
    text += x;
}
```

À chaque parcours du tableau, la valeur suivante est attribuée à la variable ```x```. Ensuite, le programme exécute les instructions au sein de la boucle. Ici, la valeur de ```x``` est ajoutée à la variable ```text``` lors du parcours de chaque élément du tableau.
