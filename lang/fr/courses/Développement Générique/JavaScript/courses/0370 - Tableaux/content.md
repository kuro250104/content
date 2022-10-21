Les tableaux, souvent appelés par leur nom anglais *array*, sont utilisés pour stocker de multiples données au sein d’une seule variable.

## Qu’est-ce qu’un array ?

Un *array* est une variable spéciale permettant de stocker plus d’une seule valeur à la fois. 

Par exemple, s’il y a une liste d’item, cela pourrait très bien être fait en déclarant plusieurs variables :

```js
let voiture = "Volvo", voiture1 = "Peugeot", voiture2 = "Citroen";
```

Cependant, le problème majeur rencontré en faisant cela est qu’il est impossible de faire une boucle afin de choisir un modèle de voiture en particulier.

C’est pourquoi, il est plus judicieux de stocker toutes les marques de voiture ci-dessus dans un tableau.

## Créer un array

Utiliser un tableau littéral est le meilleur moyen de créer un *array* en JavaScript.

La syntaxe est la suivante :

```js
const nomDuTableau = [valeur1, valeur2, valeur 3];
```

Exemple :

```js
const voiture = ["Volvo", "Peugeot", "Citroen"];
```

Les espaces et les retours à la ligne ne sont pas importants. D’ailleurs, pour des raisons de lisibilité du code, il est courant que chaque item d’un tableau soit écrit sur une nouvelle ligne.

Exemple :

```js
const voiture = [
    "Volvo", 
    "Peugeot", 
    "Citroen"
];
```

### Créer un array puis l’initialiser

Le JavaScript permet également de créer un *array*, puis de lui fournir des données, grâce aux index.

__Remarque__ : Le compte des index en JavaScript part de 0.

Exemple :

```js
const voiture = []; // Initialisation du tableau
voiture[0] = "Volvo";
voiture[1] = "Peugeot";
voiture[2] = "Citroen";
```

Dans cet exemple, le tableau est créé à la première ligne, mais est laissé vide pour le moment. Ensuite, il est rempli avec des valeurs en utilisant le nom du tableau et l’index à laquelle la donnée doit être placée dans le tableau : ```voiture[0]```.

## Accéder aux éléments d’un tableau

Pour accéder à un élément du tableau, il faut utiliser l’**index** auquel se trouve cet élément.

Exemple :

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];
var x = voiture[0]; 
```

Dans l’exemple ci-dessus, la variable ```x``` vaut “**Volvo**”, car c’est l’index 0 du tableau qui est appelé.

## Changer un élément dans un tableau

Pour modifier un élément dans un tableau, il suffit d’utiliser l’index de position de l’élément, puis de préciser le nouvel élément.

Exemple :

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];
voiture[2] = "Renault";
```

Dans cet exemple, “Citroën” est remplacé par “Renault”.

## Accéder à la totalité du tableau

Pour faire cela, le nom du tableau doit simplement être utilisé. 

Exemple : 

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];
console.log(voiture);
```

## Les tableaux sont des objets

Les tableaux sont des types spécifiques d’objets. 

Les éléments sont accessibles de deux manières.

### Accès par l’index de position

Comme édicté un peu plus tôt dans ce cours, il est possible d’accéder à un élément du tableau en utilisant son index de position.

Exemple :

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];
var x = voiture[0]; 
```

### Accès par le nom de l’élément

Cependant, la réelle force des tableaux est qu’il est possible d’attribuer un nom à chaque élément et, par la suite, accéder à cet élément en utilisant son nom.

Exemple :

```js
const user = [
    prenom : "Joe",
    nom : "Blow",
    age : 40
] ;
console.log(user.prenom);
```

Dans cet exemple, **prenom**, **nom** et **age** sont les noms des éléments. Il est important de noter que les noms ne sont pas placés entre guillemets. Par la suite, afficher l’élément **prenom** se fait en utilisant le nom du tableau - ```user``` - suivi d’un point et du nom de l’élément : ```user.prenom```.

## Les éléments d’un tableau peuvent être des objets

En JavaScript, les variables sont des objets et les tableaux sont des objets d’un type particulier. Pour cela, différents types de variables peuvent être contenues dans un même array. En effet, un array peut contenir des objets, des fonctions et un tableau peut même contenir un autre tableau.

Exemple :

```js
var tableau = [];
tableau[0] = Date.now; // Ici, le premier élément est un objet de type Date
tableau[1] = maFonction; // Le deuxième élément du tableau est une fonction
tableau[2] = voiture; // Le troisième élément est le tableau voiture créé plus haut dans le cours
```

## Propriétés et fonctions pour les tableaux

Il existe des propriétés et fonctions natives à JavaScript qui permettent d’effectuer différentes actions dans les tableaux, telles que le calcul de la taille de celui-ci, ou encore de trier les données, etc. 

__Remarque__ : Les propriétés et méthodes utilisables avec les tableaux sont traitées dans un autre cours.

### La propriété length

Cette propriété retourne le nombre d’entrées dans un tableau.

Exemple :

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];
console.log(voiture.length);
```

Dans cet exemple, la valeur retournée par ```length``` est 3.

__Remarque__ : Cette propriété rajoute toujours + 1 par rapport à l’index le plus élevé dans le tableau. Par exemple, si un array est composé de 4 éléments, plutôt que de retourner 3 - car le comptage commence à partir de 0 -, ```length``` retournera 4.

#### Accéder au dernier élément d’un array grâce à length

S’il y a besoin de créer un tableau dit “dynamique” - c'est-à-dire dont le nombre d’entrées n’est pas définie à l’avance -, il se pose le problème suivant : comment accéder au dernier élément du tableau, si le nombre d’entrées n’est pas connu à l’avance ?

Pour résoudre ce problème, la propriété ```length``` est utilisée. 

Exemple :

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];
voiture[voiture.length - 1];
```

Ici, la valeur retournée est bien le dernier élément du tableau, à savoir “Renault”.

## Faire une boucle sur un tableau

Un tableau contient plusieurs entrées. Pour afficher chacune des valeurs contenues dans un array, il serait laborieux d’utiliser les index. C’est là que les boucles entrent en jeu. 

Il existe deux moyens de faire une boucle sur un tableau.

### La boucle for

La boucle est la plus sûre à utiliser avec les tableaux.

Exemple :

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];

let text;

text = "<ul>";

for (var i = 0; i < voiture.length; i++) {
    text += "<li>" + voiture[i] + "</li>"
}

text += "</ul>";
```

Dans cet exemple, la variable ```i``` est créé et initialisé à 0. Ensuite, tant que ```i``` est inférieur à la taille du tableau, alors ```i``` est incrémenté. Enfin, tant que ```i``` n’a pas atteint le dernier index du tableau, alors chaque entrée contenue est insérée dans la variable ```text```.

### La boucle forEach

Cette boucle est également couramment utilisée pour parcourir un tableau. 

Exemple :

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];

let text;

text = "<ul>";

voiture.forEach(maFonction);

text += "</ul>";

function maFonction(valeur) {
    text += "<li>" + valeur + "</li>";
}
```

Cet exemple fait exactement la même chose que le code précédent. La seule différence est que la boucle ```forEach``` appelle la fonction ```maFonction```, fonction qui se charge d’ajouter chaque élément du tableau au sein d’une liste dans la variable ```text```.

## Ajouter une entrée dans un tableau

Il existe des cas où le développeur a besoin d’ajouter une entrée dans un tableau. Pour ce faire, là encore, il existe deux possibilités.

### Utiliser la fonction push()

Le moyen le plus simple et le plus utilisé pour ajouter une entrée dans un tableau est d’utiliser la fonction ```push()```. Cette fonction ajoute l’élément à la fin du tableau.

Exemple :

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];

voiture.push("Renault"); // Ici, "Renault" est ajouté à la fin du tableau
```

### Utiliser la propriété length

Il est également possible d’ajouter une entrée à la fin d’un array en utilisant la propriété ```length```.

Exemple :

```js
const voiture = [
    "Volvo",
    "Peugeot",
    "Citroen"
];

voiture[voiture.length] = "Renault"; // Ici, "Renault" est ajouté à la fin du tableau
```

__Remarque__ : Ajouter une entrée à un array en utilisant ```length``` est déconseillé, car cela peut créer des “trous” non définis dans le tableau.

## Tableaux associatifs

La plupart des langages de programmations permettent d’attribuer un nom aux éléments du tableau, comme évoqué un peu plus tôt dans ce cours. 

Les tableaux avec des index nommés sont appelés “tableaux associatifs”.

Cependant, le langage JavaScript, basiquement, ne supporte pas les tableaux associatifs. Par défaut, donc, dans un tableau JavaScript, les entrées sont accessibles par leurs index numériques.

Néanmoins, si les tableaux associatifs sont utilisés en JavaScript, alors l’array est redéfini en objet, à la suite de quoi, certaines propriétés et fonctions peuvent retourner des résultats inattendus.

## La différence entre les tableaux et les objets

En JavaScript, les **tableaux** utilisent des **index numériques**, tandis que les **objets** utilisent des **index nommés**.
