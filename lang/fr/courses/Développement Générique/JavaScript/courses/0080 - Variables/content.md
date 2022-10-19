Comme dans tout langage de programmation, il est important de pouvoir stocker des informations en mémoire le temps de l’exécution d’un programme - informations qui seront ensuite effacées lorsque l’utilisateur aura quitté la page web. Voici le rôle des variables.

## Syntaxe

De manière générale, la syntaxe d’une variable en JavaScript est la suivante :

``` js
var nomDeLaVariable;
```

__Remarque__ : Les règles et conventions de nommage des variables sont évoquées plus loin dans ce cours. 

## Utilisation de let et const

Avant 2015, le seul moyen de déclarer une variable en JavaScript était d’utiliser ```var```. Cependant, depuis 2015, il est également possible d’utiliser ```const```, ainsi que ```let```, qui est similaire à ```var```, à ceci près que la portée d’une variable déclarée avec ```let``` est réduite. 

## Les identifiants

Le nom donné à une variable est appelé un identifiant (*identifier*, en anglais). Les identifiants doivent être uniques à chaque fois et peuvent être soit courts, comme x ou y, par exemple, ou plus descriptifs, comme nomUtilisateur ou ageMinimum. 

__Remarque__ : Pour des raisons de maintenabilité et de lisibilité du code, il est recommandé d’utiliser des noms de variable descriptif, ainsi, l’identifiant ```ageUtilisateur``` est préférable à ```uAge```.

Les identifiants de variables doivent respecter les règles suivantes :

- Ils peuvent contenir des lettres, des chiffres, des underscores (_) et des signes dollar ($)
- Ils doivent commencer par une lettre.
- Étant considérés comme des lettres, les identifiants peuvent également commencer par le signe dollar ($) ou un - ou plusieurs - underscores (_)
- Le JavaScript est sensible à la casse, c'est -à -dire qu’il fait la différence entre un nom de variable écrit en minuscule, et un nom écrit en majuscule (y et Y sont considéré par JavaScript comme deux noms de variables différents)
- Les “mots reservés”, comme JavaScript, const, etc., ne peuvent pas être utilisés comme identifiants.

## L’opérateur d’assignation

L’opérateur d’assignation - le signe égal (**=**), en JavaScript - permet d’assigner une valeur à une variable. 

__Remarque__ : L’opérateur d’assignation ne permet pas de tester une égalité ; il permet simplement d’attribuer une valeur à une variable. Pour tester une égalité, en JavaScript, il faut utiliser l’opérateur d’égalité : **==**.

Exemple :

``` js
var a = 5;
```

Dans cet exemple, la variable ```a``` se voit assigner la valeur 5.

## Les types de données

Le langage JavaScript permet de stocker plusieurs types de données dans des variables. Les plus connus sont les nombres et les chaînes de caractères. 

En langage informatique, une chaîne de caractères est désignée par son nom Anglais : *string*. En JavaScript, une chaîne de caractères est entourée de **guillemets simples** ou de **guillemets doubles**. 

Les nombres, quant à eux, sont écrits sans guillemets. Il est important de comprendre que **si des guillemets sont ajoutés autour d’un nombre**, ce dernier sera, en JavaScript, **considéré comme une chaîne de caractères**. 

Exemple :

``` js
var a = 5; // Variable contenant un nombre
var name = "Joe" // La variable name contient, ici, une chaîne de caractères placée entre guillemets doubles
var familyName = 'Bloe'; // Ici la variable familyName contient un string placé entre guillemets simples
```

## Déclarer une variable

Déclarer une variable, en informatique, signifie simplement créer une variable. Pour ce faire, il faut utiliser le mot clé var suivi du nom de la variable.

Ensuite, il y a deux possibilités. Soit le développeur connaît à l’avance le contenu à stocker dans la variable, auquel cas, il fait suivre le nom du signe égal puis du contenu à stocker, soit le développeur ne connaît pas d’avance le contenu d’une variable, auquel cas, il déclare une variable ne contenant aucune valeur (appelée communément ```undefined```), et assignera plus tard une valeur à cette variable.

__Remarque__ : Une bonne pratique consiste, autant que possible, à déclarer, au début de programme, les variables nécessaires.

Exemple :

``` js
var a = 5; // Ici la variable a contient le chiffre 5
var vehicule; // Ici la variable ne contient rien, elle est donc undefined.
vehicule = "camion"; // Par la suite, la variable véhicule se voit attribuer la valeur "camion"
```