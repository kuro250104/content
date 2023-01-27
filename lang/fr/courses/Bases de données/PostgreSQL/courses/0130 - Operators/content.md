## Qu'est-ce qu'un opérateur dans PostgreSQL ?

Un opérateur est un mot réservé ou un caractère utilisé principalement dans la clause **WHERE** d'une instruction PostgreSQL pour effectuer une ou plusieurs opérations, telles que des comparaisons et des opérations arithmétiques.

Les opérateurs sont utilisés pour spécifier des conditions dans une instruction PostgreSQL et pour servir de conjonctions pour des conditions multiples dans une instruction.

- Arithmetic operators
- Comparison operators
- Logical operators
- Bitwise operators

## Les opérateurs arithmétiques

Si la variable ```a``` vaut 2 et la variable ```b``` vaut 3, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` + ``` | Addition - Ajoute les valeurs de part et d'autre de l'opérateur. | a + b  donnera 5 |
| ``` - ``` | Soustraction - Soustrait l'opérande de droite de l'opérande de gauche. | a - b donnera -1 |
| ``` * ``` | Multiplication - Multiplie les valeurs de part et d'autre de l'opérateur. | a * b  donnera 6 |
| ``` / ``` | Division - Divise l'opérande de gauche par l'opérande de droite. | b / a  donnera 1 |
| ``` % ``` | Modulus - Divise l'opérande de gauche par l'opérande de droite et renvoie le reste. | b % a  donnera 1 |
| ``` ^ ``` | Exponentiation - Cela donne la valeur de l'exposant de l'opérande de droite. | a ^ b  donnera 8 |
| ``` \|/ ``` | Racine carrée. | |/ 25.0  donnera 5 |
| ``` \|\|/ ``` | Racine cubique. | ||/ 27.0 donnera 3 |
| ``` ! ``` | Factorielle. | 5 ! donnera 120 |
| ``` !! ``` | Factorielle (opérateur préfixe). | 5 !! donnera 120 |

## Les opérateurs de comparaison

Si la variable ```a``` détient 10 et la variable ```b``` détient 20, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` = ``` | Vérifie si les valeurs de deux opérandes sont égales ou non, si oui, la condition devient vraie. | (a = b) n'est pas vrai. |
| ``` != ``` | Vérifie si les valeurs de deux opérandes sont égales ou non, si les valeurs ne sont pas égales alors la condition devient vraie. | (a != b)  est vrai. |
| ``` <> ``` | Vérifie si les valeurs de deux opérandes sont égales ou non, si les valeurs ne sont pas égales alors la condition devient vraie. | (a <> b)  est vrai. |
| ``` > ``` | Vérifie si la valeur de l'opérande gauche est supérieure à la valeur de l'opérande droit, si oui, la condition devient vraie. | (a > b) n'est pas vrai. |
| ``` < ``` | Vérifie si la valeur de l'opérande gauche est inférieure à la valeur de l'opérande droit, si oui, la condition devient vraie. | (a < b) est vrai. |
| ``` >= ``` | Vérifie si la valeur de l'opérande gauche est supérieure ou égale à la valeur de l'opérande droit, si oui, la condition devient vraie. | (a >= b) n'est pas vrai. |
| ``` <= ``` | Vérifie si la valeur de l'opérande gauche est inférieure ou égale à la valeur de l'opérande droit, si oui, la condition devient vraie. | (a <= b) est vrai. |

## Les opérateurs logiques


Voici une liste de tous les opérateurs logiques disponibles dans PostgresSQL.

**Opérateur et description :**

- **AND** - L'opérateur **AND** permet l'existence de plusieurs conditions dans la clause **WHERE** d'une instruction PostgresSQL.
- **NOT** - L'opérateur **NOT** inverse le sens de l'opérateur logique avec lequel il est utilisé. Par exemple : **NOT EXISTS**, **NOT BETWEEN**, **NOT IN**, etc. C'est l'opérateur de négation.
- **OR** - L'opérateur **OR** est utilisé pour combiner plusieurs conditions dans la clause **WHERE** d'une instruction PostgresSQL.

## Les opérateurs bitwise

L'opérateur ```bitwise``` travaille sur les bits et effectue une opération bit par bit. La table de vérité pour ```&``` et ```|``` est la suivante :

| **p** | **q** | **p & q** | **p \| q** |
| --- | --- | --- | --- |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 |

Supposons que ```A = 60``` ; et ```B = 13``` ; Maintenant, en format binaire, ils seront les suivants :

```bash
A = 0011 1100
B = 0000 1101
-----------------
A&B = 0000 1100
A|B = 0011 1101
~A  = 1100 0011
```

Les opérateurs **Bitwise** supportés par PostgreSQL sont listés dans le tableau suivant :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` & ``` | L'opérateur **ET** binaire copie un bit dans le résultat s'il existe dans les deux opérandes. | (A & B) donnera 12 qui est 0000 1100 |
| ``` \| ``` | L'opérateur **OU** binaire copie un bit s'il existe dans l'un ou l'autre des opérandes. | (A | B) donnera 61 qui est 0011 1101 |
| ``` ~ ``` | L'opérateur de complémentation binaire à un est unaire et a pour effet de "retourner" les bits. | (~A ) donnera -61 qui est 1100 0011 en complément à 2 en raison d'un nombre binaire signé. |
| ``` << ``` | Opérateur de décalage binaire vers la gauche. La valeur de l'opérande de gauche est déplacée vers la gauche du nombre de bits spécifié par l'opérande de droite. | A << 2 donnera 240, soit 1111 0000. |
| ``` >> ``` | Opérateur de décalage binaire à droite. La valeur de l'opérande de gauche est déplacée vers la droite du nombre de bits spécifié par l'opérande de droite. | A >> 2 donnera 15 qui est 0000 1111 |
| ``` # ``` | XOR par bit. | A # B donnera 49 qui est 00110001 |
