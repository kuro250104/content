Comme beaucoup d’autres langages de programmation, le langage PHP met à disposition des développeurs toute une série de fonctions natives permettant d’effectuer des calculs mathématiques plus ou moins complexes. En PHP, ces fonctions sont assez similaires à celles proposées par le langage JavaScript.

Ces fonctions s’utilisent aussi bien avec les nombres de type **int**, que ceux de type **float**. 

## Fonctions mathématiques basiques

### La fonction abs()

Cette fonction prend en paramètre un chiffre ou un nombre et en retourne sa valeur absolue. 

Exemple :

``` php
abs(6); // Retourne 6   
abs(-8); // Retourne 8
```

### La fonction ceil()

Cette fonction prend en valeur un float et en retourne l’entier supérieur.

Exemple :

``` php
ceil(6.9); // Retourne 7
ceil(523.4); // Retourne 524
```

### La fonction floor()

Cette fonction - signifiant littéralement *sol* en français - prend en paramètre un nombre décimal et en retourne l’arrondi inférieur.

Exemple :

``` php
floor(9.8); // Retourne 9
floor(76,5); // Retourne 76
```

### La fonction round()

Cette fonction retourne le nombre arrondi le plus proche. Il prend en paramètre un float. En second paramètre, optionnel, cette fonction le nombre de chiffres après la virgule.

En second paramètre, ```round()``` accepte un chiffre négatif. Si tel est le cas, le nombre sera arrondi comme prévu et la fonction ajoutera, après la virgule, le nombre de 0 précisé en second paramètre, grâce au nombre négatif.

Exemple :

``` php
round(2.5); // Retourne 3
round(1.36931, 2); // Retourne 1.37
round(532.32, 0); // Retourne 532
round(65.254532, -2); // Retourne 65.254600
```

### La fonction pow()

Cette fonction prend 2 arguments et retourne le premier argument à la puissance de l’argument 2.

Exemple :

``` php
pow(0, 0); // Retourne 1
pow(2, 8); // Retourne 256
```

### La fonction max()

Cette fonction prend en paramètres une liste de nombres et en retourne le nombre le plus grand. 

Exemple :

``` php
max(1, 1502, 8, 952, 20); // Retourne 1502
```

### La fonction min()

Comme pour la fonction précédente, celle-ci prend également en paramètre une liste de nombres, mais en retourne le plus petit de la liste. 

Exemple :

``` php
min(1, 1502, 8, 952, 20); // Retourne 1
```

### La fonction log()

Cette fonction prend en paramètre un chiffre ou un nombre et en retourne le logarithme naturel.

Exemple :

``` php
log(2); // Retourne 0.69314718055995
```

### La fonction exp()

Cette fonction reçoit en paramètre un chiffre ou un nombre et en retourne l’exponentiel. 

Exemple :

``` php
exp(2); // Retourne 7.3890560989307
```

### La fonction sqrt()

Cette fonction retourne la racine carrée du nombre passé en paramètre.

Exemple :

``` php
sqrt(2); // Retourne 1.41421356237
```

### La fonction mt_rand()

Cette fonction ne reçoit pas forcément d’arguments. Si elle est utilisée comme telle, ```rand()``` retourne simplement un nombre aléatoire. 

Il est cependant possible de passer 2 paramètres à la fonction : le nombre minimum et le nombre maximum - dans cet ordre - entre lequel la fonction doit retourner le nombre aléatoire.

Exemple :

``` php
mt_rand(); // Retourne, ici, 59632214521
mt_rand(0, 10); /: Retourne, ici, 9
```

### La fonction pi()

Cette fonction ne reçoit rien en paramètre et retourne la valeur du nombre Pi.

Exemple :

``` php
pi(); // Retourne 3,14159265359
```