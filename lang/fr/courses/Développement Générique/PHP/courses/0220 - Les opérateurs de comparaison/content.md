Les opérateurs de comparaisons sont, comme leurs noms l'indiquent, des moyens de comparer différentes valeurs. Il en existe différents, mais ils ont pour points communs de toujours renvoyer “vrai” ou “faux” selon les comparaisons effectuées. Ils sont très souvent utilisés dans des conditions et permettent de définir les actions à mener en fonction des valeurs comparées.

## Les différents opérateurs

### L’opérateur “==” - “égal”

Cet opérateur de comparaison permet d’établir un lien d’égalité entre deux valeurs. Ainsi si la première valeur est égale à la deuxième, alors l’opérateur retourne “vrai”. Dans le cas contraire, il renvoie “faux”. Cet opérateur ne compare QUE les valeurs, et pas les types, de telle sorte que le nombre “1” et le caractère “1” (donc en tant que texte) sont considérés égaux. Par exemple :

```php
echo( 1 == 2 );
# renvoie Faux, car les valeurs ne sont pas identiques

echo( 2 == 2 );
# renvoie Vrai, car les valeurs sont identiques

echo( 2 == "2" );
# renvoie Vrai, car les valeurs sont identiques - même si les types ne 
# ne sont pas les mêmes
```

### L’opérateur “===“ - “strictement égal”

Cet opérateur permet comme le précédent d'établir un lien d'égalité entre deux valeurs. Cependant, celui-ci compare non seulement les deux valeurs, mais également leurs types. De la sorte, le nombre “1” et le caractère “1” ne seront pas considérés comme égaux, puisque l’un est un nombre, tandis que l’autre est un caractère.

```php
echo( 1 === 2 );
# renvoie Faux, car les valeurs ne sont pas identiques


echo( 2 === 2 );
# renvoie Vrai, car les valeurs et les types sont identiques

echo( 2 === "2" );
# renvoie Faux, car même si les valeurs sont identiques, les types ne le sont pas
```

### L’opérateur “!=” - “différent”

Cet opérateur de comparaison vérifie que les valeurs testées soient bien différentes. Ici, seules les valeurs sont prises en compte, et non leur type.

```php
echo( 1 != 2 );
# renvoie Vrai, car les valeurs ne sont pas identiques

echo( 2 != 2 );
# renvoie Faux, car les valeurs sont identiques

echo( 2 != "2" );
# renvoie Faux, car les valeurs sont identiques - même si les types ne 
# ne sont pas les mêmes
```

### L’opérateur “!==” - “strictement différent”

Cet opérateur de comparaison est similaire au précédent, à ceci près qu’il teste les valeurs ainsi que les types, sur le même schéma que l’opérateur “ === ”.

```php
echo( 1 !== 2 );
# renvoie Vrai, car les valeurs ne sont pas identiques

echo( 2 !== 2 );
# renvoie Faux, car les valeurs sont identiques et leur type également

echo( 2 !== "2" );
# renvoie Vrai, car les valeurs sont identiques, mais pas leur type
```

### L’opérateur “<” - “strictement inférieur”

C’est l’opérateur traditionnellement appelé “strictement inférieur à”, issu des notations mathématiques. Il permet de vérifier que la première valeur (placée à gauche du symbole), soit bien inférieure à la seconde (placée à droite du symbole). Attention, le “strictement” est ici important puisque si les deux valeurs comparées sont identiques, alors l’une ne sera pas strictement inférieure à l’autre et la comparaison retournera “faux”.

De même, pour comparer si une valeur est strictement inférieure à une autre, il faut que les deux valeurs soient du même type, ou bien au moins que PHP soit à même de comparer les deux valeurs. De la sorte, si un nombre est comparé  à un caractère, une erreur est retournée. Par contre, si un nombre entier est comparé à un nombre à virgule, alors la comparaison pourra bien s’effectuer puisque les deux valeurs testées sont bien des nombres.

```php
echo( 1 < 2 );
# renvoie Vrai, car 1 est bien strictement inférieur à 2

echo( 2 < 2 );
# renvoie Faux, car les deux valeurs sont identiques

echo( 2 < "3" );
# renvoie une erreur puisque la comparaison concerne un nombre et un 
# caractère

echo( 1,1 < 5 );
# renvoie Vrai, car PHP sait comparer des nombres à virgule avec des 
# nombres entiers
```

### L’opérateur “<=” - “inférieur ou égal”

Cet opérateur est le même que le précédent, à ceci près qu’il va prendre en compte l’égalité entre les deux valeurs. Ainsi si les deux valeurs sont égales, alors “vrai” sera retourné.

```php
echo( 1 <= 2 );
# renvoie Vrai, car 1 est bien inférieur ou égal à 2

echo( 2 <= 2 );
# renvoie Vrai, car les deux valeurs sont égales

echo( 2 <= "3" );
# renvoie une erreur puisque la comparaison concerne un nombre et un 
# caractère

echo( 1,1 <= 5 );
# renvoie Vrai, car PHP sait comparer des nombres à virgule avec des 
# nombres entiers
```

### L’opérateur “>” - “strictement supérieur”

Il est l’exact opposé de l’opérateur “strictement inférieur” (<). Ainsi il renvoie vrai si la première valeur (à gauche du symbole) est strictement supérieure à la seconde (à droite du symbole). Les mêmes restrictions s’appliquent quant aux valeurs égales (qui renvoient donc faux), et à la comparaison d’un nombre et d’un caractère (qui renvoie une erreur).

```php
echo( 2 > 1 );
# renvoie Vrai, car 1 est bien strictement supérieur à 2

echo( 2 > 2 );
# renvoie Faux, car les deux valeurs sont identiques

echo( 2 > "3" );
# renvoie une erreur puisque la comparaison concerne un nombre et un 
# caractère

echo( 5 > 1,1 );
# renvoie Vrai, car PHP sait comparer des nombres à virgule avec des 
# nombres entiers
```

### L’opérateur “>=” - “supérieur ou égal”

Cet opérateur est le même que le précédent, à ceci près qu’il prend en compte l’égalité entre les deux valeurs. Ainsi, si les deux valeurs sont égales, alors il renvoie “vrai”.

```php
echo( 2 >= 1 );
# renvoie Vrai, car 1 est bien strictement supérieur à 2

echo( 2 >= 2 );
# renvoie Vrai, car les deux valeurs sont identiques

echo( 2 >= "3" );
# renvoie une erreur puisque la comparaison concerne un nombre et un 
# caractère

echo( 5 >= 1,1 );
# renvoie Vrai, car PHP sait comparer des nombres à virgule avec des 
# nombres entiers
```