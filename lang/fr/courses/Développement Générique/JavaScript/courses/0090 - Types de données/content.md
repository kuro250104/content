Comme évoqué dans le cours sur les variables, il existe plusieurs types de données, tels que les nombres, les chaînes de caractères, les tableaux, les booléens, etc.

## Le principe des types de données

Les types de données, en informatiques, est un concept important. En effet, un ordinateur a besoin de savoir quel type de donnée est contenu dans une variable afin que le programme puisse fonctionner correctement. 

Quand plusieurs valeurs sont contenues dans une seule variable - grâce à l’opérateur + -, le langage JavaScript lit l’expression de gauche à droite et retourne un résultat en fonction. 

__Remarque__ : Quand un string et des nombres sont contenus dans une même variable, les nombres seront considérés, par JavaScript, comme des chaînes de caractères. 

Exemple :

``` js
var a = 5 + 10 + "Hello World";
```

Dans cet exemple, la variable a contient donc la chaîne de caractères suivante : ```15Hello World```.

## Les types de données sont dynamiques.

Contrairement à beaucoup d’autres langages informatiques tels que le C, C++, etc., le langage JavaScript n’exige pas que le type de données contenues dans la variable soit précisé lors de la déclaration de celle-ci. Cela rend possible le principe de type de données dynamique, ce qui signifie qu’une variable peut, dans un premier temps, contenir un nombre, et plus loin dans le programme, se voir réassigner une donnée de type string.

Exemple :

``` js
var a = 5;
a = "Joe";
```

## Les chaînes de caractères

Une chaîne de caractère est un mot ou une phrase, inséré entre guillemets doubles ou simples. Cette chaîne de caractère peut être stockée dans une variable afin d’être réutilisée plus tard dans le programme.

__Remarque__ : Il est possible d’utiliser des guillemets au sein d’un string. La seule règle à respecter est que ceux-ci ne doivent pas correspondre à ceux qui entourent la chaîne de caractères. Ainsi, si un string est entouré par des guillemets doubles, alors des guillemets simples sont utilisables au sein de la chaîne de caractères.