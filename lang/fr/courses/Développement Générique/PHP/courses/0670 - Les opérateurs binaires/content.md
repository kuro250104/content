Les opérateurs Bitwise sont utilisés pour effectuer des opérations au niveau du bit sur les opérandes. Les opérateurs sont d'abord convertis au niveau du bit, puis le calcul est effectué sur les opérandes. Les opérations mathématiques telles que l'addition, la soustraction, la multiplication, etc. peuvent être effectuées au niveau du bit pour un traitement plus rapide. En PHP, les opérateurs qui fonctionnent au niveau du bit sont :

## & (ET Binaire)

C'est un opérateur binaire, c'est-à-dire qu'il fonctionne sur deux opérandes. L'opérateur ET binaire en PHP prend deux nombres comme opérandes et effectue un ET sur chaque bit des deux nombres. Le résultat du ET est 1 seulement si les deux bits sont 1.

### Syntaxe

```php
$Premier & $Second
```

Cela retournera un autre nombre dont les bits sont activés si les bits du premier et du second sont activés.

### Exemple

```php
Entrée : $Premier = 5,  $Second = 3
Réponse : Le & binaire de ces deux valeurs sera 1.
```

La représentation binaire de 5 est 0101 et 3 est 0011. Par conséquent, leur bit & sera 0001 (c'est-à-dire qu'il sera activé si le premier et le second ont tous deux leur bit activé).

## | (OU Binaire)

Il s'agit également d'un opérateur binaire, c'est-à-dire qu'il fonctionne sur deux opérandes. L'opérateur OU par bit prend deux nombres comme opérandes et effectue un OU sur chaque bit des deux nombres. Le résultat de l'opération OU est 1 si l'un des deux bits est 1.

### Syntaxe

```php
$Premier | $Second
```

Cela retournera un autre nombre dont les bits sont activés si le bit du premier ou du second est activé.

### Exemple

```php
Entrée : Premier = 5, Second = 3
Réponse : Le OU binaire de ces deux valeurs sera 7.
```

La représentation binaire de 5 est 0101 et 3 est 0011. Par conséquent, leur combinaison binaire sera 0111 (c'est-à-dire qu'elle sera activée si le premier ou le second ont leur bit activé).

## ^ (OU exclusif Binaire)

Il s'agit également d'un opérateur binaire, c'est-à-dire qu'il fonctionne sur deux opérandes. Il est également connu sous le nom d'opérateur OU exclusif. L'opérateur XOR par bit prend deux nombres comme opérandes et effectue le XOR sur chaque bit des deux nombres. Le résultat de l'opération XOR est 1 si les deux bits sont différents.

### Syntaxe

```php
$Premier ^ $Second
```

Cela renvoie un autre nombre dont les bits sont activés si l'un des bits du premier ou du deuxième est activé, mais pas les deux.

### Exemple

```php
Entrée : Premier = 5, Second = 3
Réponse : La OU exclusif Binaire de ces deux valeurs sera 6.
```

La représentation binaire de 5 est 0101 et 3 est 0011. Par conséquent, leur ^ binaire sera 0110 (c'est-à-dire qu'il sera activé si le premier ou le second ont leur bit activé mais pas les deux).

## ~ (NON Binaire)

Il s'agit d'un opérateur unitaire, c'est-à-dire qu'il ne fonctionne que sur un seul opérande. L'opérateur NON Binaire prend un nombre et inverse tous les bits de celui-ci.

### Syntaxe

```php
~$number
```

Cela va inverser tous les bits de $number.

### Exemple

```php
Entrée : nombre = 5
Réponse : Le ~ binaire de ce nombre sera -6.
```

La représentation binaire de 5 est 0101. Par conséquent, la représentation binaire de 5 sera 1010 (inverse tous les bits du nombre d'entrée).

## << (Décalage binaire à gauche)

Il s'agit d'un opérateur binaire, c'est-à-dire qu'il travaille sur deux opérandes. L'opérateur Décalage binaire à gauche (*Bitwise Left Shift* en anglais) prend deux nombres, décale à gauche les bits du premier opérande, le second opérande décide du nombre de positions à décaler.

### Syntaxe

```php
$Premier << $Second
```

Cela va décaler les bits de ```$Premier``` vers la gauche. ```$Second``` décide du nombre de fois que les bits seront décalés.

### Exemple

```php
Entrée : Premier = 5, Second = 1
Réponse : Le << binaire de ces deux valeurs sera 10.
```

La représentation binaire de 5 est 0101 . Par conséquent, le << binaire décalera les bits de 5 une fois vers la gauche (c'est-à-dire 01010).

*Remarque : le décalage à gauche d'un bit est équivalent à une multiplication par 2.*

## >> (Décalage binaire à droite)

Il s'agit également d'un opérateur binaire, c'est-à-dire qu'il fonctionne sur deux opérandes. L'opérateur Décalage binaire à droite (*Bitwise Right Shift* en anglais) prend deux nombres, décale à droite les bits du premier opérande, le second opérande décide du nombre de positions à décaler.

### Syntaxe

```php
$Premier >> $Second
```

Cela va décaler les bits de ```$Premier``` vers la droite. ```$Second``` décide du nombre de fois que les bits seront décalés.

### Exemple

```php
Entrée : Premier = 5, Second = 1
Réponse : La combinaison >> binaire de ces deux valeurs sera 2.
```

La représentation binaire de 5 est 0101 . Par conséquent, le >> binaire déplacera les bits de 5 une fois vers la droite (c'est-à-dire 010).

*Remarque : Le décalage vers la droite d'un bit est équivalent à une division par 2.*