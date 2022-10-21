Le langage JavaScript, comme pour d’autres fonctionnalités, met à disposition des fonctions utilisables avec les tableaux, afin de pouvoir facilement manipuler les données qui s’y trouvent.

## Convertir un tableau en chaîne de caractères

### La fonction toString()

La fonction ```toString()``` permet de convertir les données d’un tableau en chaîne de caractères. Chaque entrée est séparée par une virgule.

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands.toString();
```

Cet exemple retourne le résultat suivant :

```js
"Renault,Peugeot,Citroen,Volvo"
```

__Remarque__ : En JavaScript, la fonction ```toString()``` est automatiquement implémentée pour les tableaux. En effet, même si elle n’est pas utilisée, le JavaScript retourne, malgré tout, un ensemble de valeurs séparées par des virgules.

### La fonction join()

La fonction ```join()``` permet, elle aussi, de réunir les entrées d’un tableau dans une chaîne de caractères. La différence avec ```toString()``` est qu’en plus, ```join()``` permet également de préciser le séparateur. 

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroën",
    "Volvo" 
];
carBrands.join(' - ');
```

Cet exemple retourne le résultat suivant :

```js
"Renault - Peugeot - Citroen - Volvo"
```

__Remarque__ : Si aucun séparateur n’est précisé lorsque la fonction ```join()``` est utilisée, alors la virgule est utilisée comme séparateur par défaut.

## Supprimer et ajouter des entrées

En JavaScript, il est très facile de supprimer ou d’ajouter des valeurs à un tableau, car, là encore, il existe deux fonctions natives à JavaScript.

### Supprimer une entrée

La fonction ```pop()``` permet de supprimer la dernière entrée dans un array, et retourne la valeur qui a été supprimée.

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands.pop();
```

Ici, la fonction ```pop()``` retourne : “Volvo”.

### Ajouter une entrée

La fonction ```push()```, quant à elle, permet d’ajouter une nouvelle entrée à la fin du tableau. Cette fonction retourne la taille de l’élément ajouté.

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands.push('Nissan');
```

Dans cet exemple, ```push()``` retourne **4**, la taille de l’élément ajouté.

## “Déplacer” des éléments

En JavaScript, “déplacer” un élément consiste à supprimer une entrée dans un tableau. Cependant, cette fois, plutôt que de supprimer le dernier élément de l’array, c’est le premier qui est supprimé.

### Supprimer la première entrée d’un tableau

Pour supprimer la première entrée du tableau, la fonction ```shift()``` est utilisée. Cette fonction retourne l’élément qui a été supprimé.

__Remarque__ : En plus de supprimer la première entrée d’un tableau, cette fonction fait également “remonter” les autres éléments. En d’autres termes, une entrée qui a l’index 2, se voit attribuer l’index 1 après l’utilisation de ```shift()```.

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands.shift();
```

Dans cet exemple, la fonction ```shift()``` retourne “**Renault**”, car c’est l’élément supprimé. De plus, les autres éléments sont “remontés”. Par exemple, l’entrée “**Peugeot**” avait, auparavant, l’index 1 ; désormais, il se voit attribuer l’index 0.

## Ajouter une entrée au début du tableau

Pour ajouter une entrée au début du tableau, il faut utiliser la méthode ```unshift()```. Cette fonction retourne la taille de l’élément ajouté.

De plus, une fois la nouvelle entrée ajoutée, les autres éléments contenus dans le tableau sont descendus. Leur numéro d’index prend alors **+1**.

Exemple :

```js
var carBrands = [
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands.unshift("Renault");
```

Dans cet exemple, ```unshift()``` retourne la valeur 4, car c’est la taille de l’élément ajouté. De plus, les autres entrées sont descendues. Par exemple, l’index de “**Peugeot**” était, auparavant **0**, il vaut désormais **1**.

## Changer les éléments

Les numéros d’index sont utilisés pour accéder à un élément d’un array.

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands[0];
```

Dans cet exemple, le résultat retourné est “**Renault**”, car c’est l’élément placé à l’index **0**.

Un bon moyen d’ajouter un élément à la fin d’un array est d’utiliser la fonction ```length()```.

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands[carBrands.length] = "Nissan";
```

Dans cet exemple, l’entrée est ajoutée à la fin du tableau, car le dernier index est sélectionné grâce à ```carBrands[carBrands.length]```.

## Effacer des éléments

Étant donné que les arrays, en JavaScript, sont des objets, des éléments peuvent être supprimés grâce à l’opérateur **delete**.

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
delete carBrands[3];
```

Dans cet exemple, La dernière entrée du tableau - ici “**Volvo**”, est supprimée du tableau.

__Remarque__ : Lorsqu’une entrée est supprimée d’un array en utilisant **delete**, la place de cet élément dans le tableau n’est pas supprimée pour autant. Utiliser **delete** peut laisser des “trous” indéfinis dans le tableau, c’est pourquoi il est plutôt recommandé d’utiliser ```shift()``` ou ```pop()```.

## La fonction splice()

Cette fonction peut être utilisée à la fois pour ajouter de nouvelles entrées dans un tableau, ou pour en supprimer. 

### Ajouter une entrée dans un tableau

Lorsqu’un élément doit être ajouté à tableau, la fonction ```splice()``` prend, dans cet ordre, les paramètres suivants :

- La position à laquelle le nouvel élément doit être ajouté dans le tableau
- Le nombre d’éléments à supprimer
- La ou les nouvelles entrées à ajouter dans le tableau

Cette fonction retourne un array avec les éléments supprimés.

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands.splice(1, 0, "Nissan", "Toyota");
```

Dans l’exemple ci-dessus, “**Nissan**” est ajouté dans l’array à l’index 1, et “**Toyota**” à l’index 2. Aucun élément n’est supprimé.

### Supprimer un élément

En définissant correctement les paramètres dans la fonction ```splice()```, il est possible de supprimer des éléments sans laisser des trous dans le tableau. 

Pour ce faire, voici comment définir les paramètres :

- La position - l’index - de ou des éléments à supprimer
- Le nombre d’éléments à supprimer
- Le troisième paramètre n’est pas précisé, car aucune valeur n’est ajoutée

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands.splice(3, 1);
```

Dans cet exemple, l’entrée “**Volvo**” est supprimée, car c’est celle qui se trouve à l’index 3.

## Fusionner - concaténer - des tableaux

La fonction ```concat()``` permet de fusionner plusieurs array en en créant un nouveau.

Exemple :

```js
var eleves = [
	"Joe",
	"Johanna",
	"Kevin"
];

var notes = [12, 15, 20];

var bulletin = eleves.concat(notes);
```

Dans cet exemple, les deux tableaux ```eleves``` et ```notes``` sont fusionnés dans le nouveau tableau ```bulletin```.

__Remarque__ : La fonction ```concat()``` ne modifie aucun tableau, mais en crée toujours un nouveau.

### Ajouter un élément dans le tableau grâce à concat()

Cette fonction permet également d’ajouter un élément à la fin d’un tableau.

Exemple :

```js
bulletin.concat("Benoit", 13);
```

## Découper un tableau

La fonction ```slice()``` permet de découper un tableau. Cette fonction crée un nouveau tableau sans ne rien modifier dans le tableau actuel. 

Cette fonction prend en paramètre l’index de l’élément à partir duquel découper le tableau.

Exemple :

```js
var carBrands = [
    "Renault",
    "Peugeot",
    "Citroen",
    "Volvo" 
];
carBrands.slice(0);
```

Cet exemple retourne le tableau suivant : ```["Peugeot”, “Citroen”, “Volvo”]```, car la fonction ```slice()``` a découpé le tableau à partir de la première entrée.