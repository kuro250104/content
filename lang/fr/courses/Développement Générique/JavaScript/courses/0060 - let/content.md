Avant la version 6 du langage JavaScript, il n’y avait qu’un seul mot-clé utilisable pour déclarer une variable : ```var```. Depuis la sortie de cette version 6 en 2015, il est désormais possible de déclarer une variable avec ```let```. Ce mot-clé permet de créer des variables ayant leurs propres spécificités. 

## Ne peuvent pas être redéclarées

En déclarant une variable avec ```let```, il n’est pas possible de la déclarer à nouveau ensuite. Cela empêche en fait les re-déclarations pas accident. 

Exemple :

``` js
let x = 12;
let x = 24;
```

Ce programme retourne une ```syntaxError```, car ```x``` a déjà été déclaré une première fois. 

## Portée bloc

Les variables déclarées avec ```let``` - comme celles déclarées avec ```const``` - ont une portée bloc. Cela signifie que toute variable déclarée dans un bloc de code placé entre accolades n’est pas accessible hors de ce bloc. 

Exemple :

``` js
{
	let x = 0;
} 
// Ici, la variable x n'est plus accessible
```

## Mot-clé let et hoisting

Les variables déclarées avec ```let``` sont **hoistées**, mais elles ne sont pas initialisées. Cela signifie qu’une variable utilisée avant d’être déclarée retourne une ```referenceError```.

Exemple :

``` js
carName = "Saab";
let carName = "Volvo";
```