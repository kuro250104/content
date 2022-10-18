En PHP, comme avec beaucoup d’autres langages informatiques, il est possible de faire des calculs. Le langage PHP comprend les quatre opérations arithmétiques de bases (addition, soustraction, multiplication et division), mais également des opérations plus avancées : division avec reste (modulo) et puissances (exposant). Le langage PHP peut aussi calculer l’opposé d’un chiffre (négation). 

## L’addition

En PHP, il est possible d’additionner des valeurs entre elles. Pour cela, il suffit d’utiliser le signe (appelé opérateur) ```+```. 

Exemple : 

``` php
<?php
#Création des variables
$a = 3;
$b = 3;
# Addition des deux variables
$resultat = $a + $b;

# Ici, echo affiche “6”
echo $resultat;
?>
```

Dans l’exemple ci-dessus, les variables ```$a``` et ```$b``` sont créées et contiennent toutes deux le chiffre 3. Ensuite, dans la variable ```$resultat```, ```$a``` et ```$b``` sont additionnés. Enfin, echo affichera le résultat de l’opération ```$a + $b```, contenu dans ```$resultat``` : 6.

## La soustraction

De même qu’il est possible d’additionner deux valeurs entre elles, en PHP, il est par ailleurs possible d’obtenir la différence entre deux valeurs. Pour obtenir ce résultat, il faut utiliser le signe ```-```.

Exemple :

``` php
<?php
#Création des deux variables
$a = 3;
$b = 2;

#Soustraction des deux variables
$resultat = $a - $b;

# Ici, $resultat contient le résultat de $a-$b, donc 1
echo $resultat;
?>
```

Le variable ```$a``` est créée et initialisée avec le chiffre 3 ; la variable ```$b``` est initialisée avec le chiffre 2. 

Ici, la variable ```$resultat``` contient le résultat de l’opération ```$a - $b``` (3-2), c'est-à-dire 1. 

Dans l’exemple ci-dessus, ```echo``` va donc afficher “1”.

## La multiplication

Avec le langage PHP, il est également possible d’obtenir un produit. Pour réaliser cela, il suffit d’utiliser le signe ```*``` (étoile).

Exemple :

``` php
<?php
$a = 5;
$b = 2;

$resultat = $a * $b;

echo $resultat;
?>
```

Dans l’exemple ci-dessus, les variables ```$a``` et ```$b``` sont initialisées avec les valeurs suivantes : 5 et 2.

Dans ```$resultat```, les deux variables sont multipliées l’une avec l’autre. La variable ```$resultat``` contient le résultat de la multiplication 5*2, donc 10.

```Echo``` affiche 10.

## La division

L’opérateur suivant permet d’obtenir le **quotient** de deux valeurs. Pour faire une division, en PHP, il faut utiliser le signe ```/``` (slash).

``` php
<?php
$a = 6;
$b = 3;

$resultat = $a / $b;

echo $resultat;
?>
```

Comme dans les exemples précédents, les variables ```$a``` et ```$b``` sont initialisées avec 6 et 3. Ensuite, dans la variable ```$resultat```, ```$a``` est divisée par ```$b```. La variable ```$resultat``` contenant le résultat de cette opération, ```echo``` retourne donc “2”.

*Remarque : L’opérateur de division retourne un chiffre à virgule, sauf si les deux valeurs de l’opération sont des nombres entiers et que leur division est exacte - cela signifie que la division a pour reste 0. Dans ce cas, l’opérateur ```/``` retourne un nombre entier.*

En plus de ces quatre opérations de base, le langage PHP permet également de faire des opérations plus avancées : le modulo et l’exposant.

## Le modulo

Le modulo est une opération particulière en ceci qu’elle retourne le **reste** d’une division. Il est important de comprendre que cet opérateur **ne retourne pas** le quotient d’une division mais le reste. 

Afin de faire une opération modulo, il suffit d’utiliser le signe ```%```.

Exemple :

``` php
<?php
$a = 8;
$b = 5;

# Calcul du RESTE de la division 8/5
$resultat = $a % $b;

/* Ici echo affichera 3, car $resultat contient le RESTE et non le quotient de la division */
echo $resultat;
?>
```

Dans cet exemple, les variables ```$a``` et ```$b``` sont initialisées avec les valeurs 8 et 5. Dans la variable ```$resultat``` est calculé le reste de la division entre ```$a``` et ```$b```. Ainsi, au lieu d’afficher “1,6” qui sera le quotient de la division 8/5, ```echo``` affichera la valeur contenue dans la variable ```$resultat```, à savoir le reste de la division 8/5, soit “3”.

**Remarque** : Le résultat d’une opération modulo a forcément le même signe que le premier opérateur. Ainsi si ```$a``` est négatif, le résultat de l’opération sera, par conséquent, lui aussi négatif.

## L’exposant

Avec le langage PHP, il est également possible de retourner le résultat d’un chiffre élevé à la puissance d’un autre. 

Pour rappel, en mathématiques, la puissance d’un nombre (ou exposant) est le résultat de la multiplication d’un nombre avec lui-même. Par exemple, 2^5 signifie que 2 est multiplié cinq fois par lui-même. Ainsi 2^5 = 2*2*2*2*2 = 32.

Pour effectuer une opération de puissance en PHP, il faut utiliser le signe suivant : ```**```.

Exemple : 

``` php
<?php
$a = 2;
$b = 10;

# Multiplie 2 dix fois par lui-même
$resultat = $a ** $b;

# Affiche "1024"
echo $resultat;
?>
```

Dans cet exemple, le chiffre contenu dans la variable ```$a``` (2) est élevé à la puissance du chiffre contenu dans la variable ```$b``` (10). La variable ```$resultat``` stocke le résultat de la multiplication de 2^10 (2 puissance 10). Ici, 2 est donc multiplié 10 fois par lui-même. Par conséquent ```echo``` affiche “1024”.

## La négation

Le PHP permet également de calculer l’opposé d’un chiffre. 

En arithmétiques, l’opposé d’un nombre a est l’unique nombre qui, ajouté à a, donne zéro. 

Pour calculer l’opposé d’un nombre en PHP, il faut utiliser l’opérateur ```+``` devant le nom de la variable. 

Exemple :

``` php
<?php
$a = 2;

/* Pour trouver l'opposé du chiffre 2, il suffit d'ajouter l'opérateur "+" devant la variable $a */
$resultat = +$a;

# Affiche -2, car 2-2 = 0;
echo $resultat;
?>
```

Dans l’exemple ci-dessus, la variable ```$a``` est initialisée avec le chiffre 2. Dans ```$resultat``` est stocké le résultat de l’opération ```+$a```, calculant le chiffre opposé à 2. ```Echo``` affiche donc le contenu de ```$resultat```, soit -2, car il est l’unique chiffre qui, ajouté à 2, donne 0.

## Résumé des opérateurs

Voici un tableau récapitulatif des différents opérateurs arithmétiques en PHP, leurs noms et le résultat qu’ils retournent :

| **Opérateur** | **Nom** | **Résultat** |
| --- | --- | --- |
| ```+``` | Addition | Retourne le résultat de l’addition de deux valeurs |
| ```-``` | Soustraction | Retourne le résultat de la soustraction de deux valeurs |
| ```*``` | Multiplication | Retourne le résultat du produit de deux valeurs |
| ```/``` | Division | Retourne le **quotient** de la division de deux valeurs |
| ```%``` | Modulo | Retourne le **reste** de la division de deux valeurs |
| ```**``` | Exponentielle | Élève un chiffre à la puissance d’un autre |
| ```+$a``` | Négation | Retourne le chiffre opposé |