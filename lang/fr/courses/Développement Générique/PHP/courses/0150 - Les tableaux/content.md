## Qu’est-ce qu’un tableau ?

Un tableau, aussi appelé “*Array*”, est une structure de données. Il peut contenir zéro, une, ou plusieurs informations de n’importe quel type (nombre, texte, date, etc…). Il peut être organisé ou non, contenir lui-même d’autres tableaux et est dynamique tout comme l’est une variable. Son contenu peut donc évoluer au fur et à mesure de l’avancement de l’interprétation d’un script. Afin de pouvoir récupérer, créer, modifier ou supprimer des données spécifiques à l’intérieur de ceux-ci, les tableaux incluent des “**indices**”.

La compréhension d’un tableau en PHP s'apparente à la compréhension d’un tableau Excel. Pour distinguer les cases d’un tableau Excel, il faut s’appuyer sur ses coordonnées (A1, A2, A3, A4, etc.). Les “**indices**” sont de ce fait l’équivalent en PHP de ce que sont les coordonnées dans Excel.

## Les tableaux dans du code PHP

### Déclaration

Un tableau est un élément qui est contenu dans une variable. Pour le déclarer, il faut ainsi  commencer par définir une variable, puis lui affecter la valeur d’un tableau vide. Il existe 2 manières différentes de déclarer un tableau vide : 

```php
# méthode 1
$tableau : array();
```

```php
# méthode 2
$tableau = [ ];
```

Il est également possible de directement déclarer un tableau en lui affectant des valeurs. Il n’y a à ce jour plus de réelle règle quant à la nécessité de déclarer un tableau vide avant de lui insérer des valeurs plutôt que de déclarer un nouveau tableau avec les valeurs directement. Notez toutefois qu’aux débuts du développement, on ne pouvait pas se servir d’un élément non déclaré préalablement. La manière de déclarer un tableau (avec ou sans données) dépendra donc vraisemblablement des développeurs avec lesquels vous serez amenés à travailler.

Il existe plusieurs types de tableaux en PHP, et il est important de bien les connaître et les différencier pour les exploités du mieux possible par la suite.

### Tableau à index numérique

Le tableau à index numérique est le plus basique de tous les tableaux. Il consiste uniquement en une suite de valeurs, chacune d’entre elles séparée par une virgule. Comme expliqué en introduction et comme l’indique le titre de cette partie, chaque tableau à index numérique dispose d’un ou plusieurs index permettant d’identifier les valeurs contenues. Les index sont ici des nombres, qui commencent à 0 (zéro), et qui s’incrémentent de 1 à chaque nouvelle valeur du tableau.

Attention, la première case d’un tableau porte l’index “0”, et non “1”. Ce qui veut dire que la première valeur d’un tableau se situe à l’index “0”, la deuxième valeur se situe à l’index “1”, et la troisième valeur se situe à l’index “2”. Ceci est souvent problématique chez les néophytes et entraîne de nombreuses erreurs !

#### Déclaration

Pour déclarer un tableau à index numérique en insérant des valeurs lors de sa création, il faut procéder comme expliqué ci-dessus, en ajoutant l’ensemble de vos valeurs entre les parenthèses qui suivent “*array*”, en les séparant par des virgules. Voici un exemple :

```php
# $tableau représente le nom de la variable qui contient le tableau.

# array() permet de définir un tableau

# 'val1', 'val2', 'val3'  sont les valeurs qui constituent le 
# contenu du tableau
$tableau = array('val1', 'val2', 'val3');
```

Il est également possible d’utiliser la deuxième méthode de déclaration d’un tableau : 

```php
# $tableau représente le nom de la variable qui contient le tableau.

# les crochets permettent de définir un tableau

# 'val1', 'val2', 'val3'  sont les valeurs qui constituent le contenu du 
# tableau
$tableau = ['val1', 'val2', 'val3'];
```

#### Ajout d’une valeur à la fin du tableau

Il n’existe ici encore pas qu’une seule manière d’ajouter une valeur à un tableau à index numérique. Il est possible de procéder comme suit : 

```php
# déclaration d'un tableau initial
$tableau = array('val1', 'val2', 'val3');

# ajout d'une valeur à la fin du tableau
$tableau[] = 'val4';
```

Une autre solution peut être d’utiliser une fonction fournie par PHP pour les tableaux : ```append()``` :

```php
# déclaration d'un tableau initial
$tableau = array('val1', 'val2', 'val3');

# ajout d'une valeur à la fin du tableau
$tableau->append('val4');
```

#### Modification d’un index précis

Dans le cadre de l’utilisation de tableaux en PHP, il est courant de devoir modifier des valeurs à des index précis du tableau. En reprenant l’exemple du tableau ci-dessus : ```$tableau = array('val1', 'val2', 'val3');``` et pour modifier la valeur de la deuxième case, alors il faut modifier l’index “1” comme suit : 

```php
# création du tableau initial
$tableau = array('val1', 'val2', 'val3');

# modification de la deuxième case.

# Les index commençant par "0", la deuxième case correspond donc à 
# l'index "1".

# il faut donc préciser l'affectation d'une valeur à cet index : 
$tableau[1] = 'val4';

# le tableau vaudra maintenant : 
# array('val1', 'val4', 'val3');
```

Attention, si jamais l’index choisi n’existe pas, alors il sera créé et la valeur désirée y sera affectée.

#### Récupération et affichage d’un élément du tableau

Afin de pouvoir exploiter l’ensemble des informations stockées dans un tableau, il faut pouvoir accéder à chacune de ses cases. Tout comme pour la modification d’une case, il est nécessaire de se servir de l’index de la case. Par exemple, pour afficher la dernière case du tableau suivant : 

```php
# création du tableau initial
$tableau = array('val1', 'val2', 'val3');

# Le tableau contient 3 cases, le dernier index est donc le "2"
# Utilisation de "echo()" pour l'affichage :

echo($tableau[2]);
# affichera : "val3"
```

#### Supprimer un élément d’un tableau

Pour supprimer un élément, il existe la fonction PHP “**unset()**”. Pour l’utiliser, il faut lui stipuler l’élément du tableau à supprimer en utilisant ici encore son indice. Par exemple, pour supprimer la première case d’un tableau :

```php
# création du tableau initial
$tableau = array('val1', 'val2', 'val3');

# suppression de la première case
# suppression donc de l'indice "0" (zéro)
unset($tableau[0]);
```

### Tableau associatif

Un tableau associatif est semblable à un tableau à index numérique, à ceci près que l’index n’est pas forcément numérique, et qu’il peut être défini par d’autres types que le type numérique. Cette organisation d’information est appelée une paire de “clé - valeur”. La clé joue le rôle d’index, tandis que la valeur représente l’élément qui y est lié.

En y réfléchissant davantage, il s’avère qu’un tableau à index numérique s’apparente également à un tableau associatif : la seule différence est que la clé utilisée dans le système de “clé - valeur” est gérée automatiquement par PHP et est numérique.

#### Déclaration d’un tableau avec des valeurs

La déclaration est assez similaire à un tableau à index numérique. Il faut créer une variable de la même manière, utiliser la méthode “**array()**” et séparer les “cases” par des virgules. La différence ici va se situer sur ce qu’il faut spécifier entre les parenthèses de “**array()**”. Pour symboliser un système de “clé - valeur”, il faut utiliser le symbole de la double flèche “**=>**”. À gauche de celle-ci est placée la clé, tandis que la valeur est disposée à sa droite. Voici un exemple de déclaration de tableau associatif :

```php
# Création d'un tableau associatif
$tableau = array(
    1 => "Hello World",
    "name" => "microlead",
    "useful" => True
);
```

Prenons le temps d’expliquer chacune des lignes : 

- ligne 0 : Commentaire simple.
- ligne 1 : Déclaration de la variable “*tableau*” et affectation d’un tableau
- ligne 2 : Affectation de la première paire “clé-valeur” au tableau. La clé est “**1**” (nombre entier), et la valeur est “**Hello World**” (chaine de caractère).
- ligne 3 : deuxième paire, la clé est “**name**” (chaine de caractère) et la valeur est “**microlead**” (chaine de caractère).
- ligne 4 : troisième paire, la clé est “**usefull**” (chaine de caractère) et la valeur est “**True**” (booléen)
- ligne 5 : Fin de déclaration du tableau

A noter qu’il est également possible d’utiliser la notation avec crochets pour créer le même tableau que présenté ci-dessus : 

```php
# Création d'un tableau associatif
$tableau = [
    1 => "Hello World",
    "name" => "microlead",
    "useful" => True
];
```

#### Ajout / Modification d’une valeur

Le principe est le même que pour les tableaux à index numérique. Pour ajouter ou modifier une valeur dans un tableau associatif, il faut spécifier l’index souhaité, puis lui affecter la valeur désirée. Par exemple : 

```php
# Ajout / modification d'une valeur dans un tableau associatif
$tableau["nouvelle_cle"] = "nouvelle valeur"
```

Dans cet exemple, si une clé “**nouvelle_cle**” est déjà existante dans le tableau ```$tableau```, alors la valeur “**nouvelle valeur**” va remplacer l’existante. L’ancienne valeur sera donc écrasée.

A contrario, si cette clé “**nouvelle_cle**” n’existe pas dans le tableau, alors elle va être créée et la valeur “**nouvelle valeur**” affectée. Il en résultera l’ajout d’une case au tableau.

#### Récupération et affichage d’un élément du tableau

Le principe de récupération d’un élément du tableau est ici aussi basé sur son index. Dans le contexte d’un tableau associatif, il est nécessaire de bien connaître la structure du tableau contenant l’élément qu’il faut afficher.

Si le tableau dispose d’une paire de “*clé-valeur*” spécifique, dont il faut afficher la “*valeur*”, il sera nécessaire d’appeler le tableau en passant entre crochets la “*clé*” associée. Par exemple : 

```php
# Création d'un tableau associatif
$tableau = array(
    1 => "Hello World",
    "name" => "microlead",
    "useful" => True
);

# Récupération de la valeur "Hello World" :
$tableau[1];

# Récupération de la valeur "microlead" :
$tableau["name"];

# Récupération de la valeur "True" :
$tableau["useful"];
```

#### Suppression d’un élément

La suppression d’un élément s’effectue ici encore de la même manière que pour les tableaux à index numérique à ceci près que l’index correspond à la “clé” pour chaque paire de “clé-valeur”. L’utilisation de la fonction ```unset()``` est donc toujours préconisée, en lui passant entre les parenthèses le tableau et en lui spécifiant la clé souhaitée : 

```php
# Création d'un tableau associatif
$tableau = array(
    1 => "Hello World",
    "name" => "microlead",
    "useful" => True
);

# suppression de l'index "name" et de la valeur associée :
unset($tableau[1]);

# suppression de l'index "usefull" et de la valeur associée :
unset($tableau["useful"]);
```

À l'issue de la suppression des deux index “**1**” et “**usefull**”, le tableau ne contiendra donc plus qu’une paire de “clé-valeur” : ```“name” => “microlead”```.