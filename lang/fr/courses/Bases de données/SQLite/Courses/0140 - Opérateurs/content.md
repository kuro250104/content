## Qu'est-ce qu'un opérateur en SQLite ?

Un opérateur est un mot réservé ou un caractère utilisé principalement dans la clause WHERE d'une instruction SQLite pour effectuer une ou plusieurs opérations, telles que des comparaisons et des opérations arithmétiques.

Les opérateurs sont utilisés pour spécifier des conditions dans une instruction SQLite et pour servir de conjonctions pour des conditions multiples dans une instruction.

- Opérateurs arithmétiques
- Opérateurs de comparaison
- Opérateurs logiques
- Opérateurs binaires

## Opérateurs arithmétiques SQLite

Supposons que la variable a ait une valeur de 10 et que la variable b ait une valeur de 20, alors les opérateurs arithmétiques de SQLite seront utilisés comme suit : -.

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| + (Addition) | Ajoute des valeurs de part et d'autre de l'opérateur | a + b donnent 30 |
| - (Soustraction) | Soustrait l'opérande de droite de l'opérande de gauche. |  - b donnera -10 |
| * (Multiplication) | Multiplie les valeurs de part et d'autre de l'opérateur | a * b donnera 200 |
| / (Division) | Divise l'opérande de gauche par l'opérande de droite. | b / a donnera 2 |
| % (Modulus) | Divise l'opérande de gauche par l'opérande de droite et renvoie le reste. | b % a donnera 0 |

## Opérateurs de comparaison SQLite

Supposons que la variable a contient 10 et la variable b contient 20, alors les opérateurs de comparaison SQLite seront utilisés comme suit

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` == ``` | Vérifie si les valeurs de deux opérandes sont égales ou non, si oui, la condition devient vraie. | (a == b) n'est pas vrai. |
| ``` = ``` | Vérifie si les valeurs de deux opérandes sont égales ou non, si oui, la condition devient vraie. | (a = b) n'est pas vrai. |
| ``` != ``` | Vérifie si les valeurs de deux opérandes sont égales ou non, si les valeurs ne sont pas égales, alors la condition devient vraie. | (a != b) est vrai. |
| ``` <> ``` | Vérifie si les valeurs de deux opérandes sont égales ou non, si les valeurs ne sont pas égales, alors la condition devient vraie. | (a <> b) est vrai. |
| ``` > ``` | Vérifie si la valeur de l'opérande de gauche est supérieure à la valeur de l'opérande de droite, si oui, la condition devient vraie. | (a > b) n'est pas vrai. |
| ``` < ``` | Vérifie si la valeur de l'opérande de gauche est inférieure à la valeur de l'opérande de droite, si oui, la condition devient vraie. | (a < b) est vrai. |
| ``` >= ``` | Vérifie si la valeur de l'opérande de gauche est supérieure ou égale à la valeur de l'opérande de droite, si oui, la condition devient vraie. | (a >= b) n'est pas vrai. |
| ``` <= ``` | Vérifie si la valeur de l'opérande de gauche est inférieure ou égale à la valeur de l'opérande de droite, si oui, la condition devient vraie. | (a <= b) est vrai. |
| ``` !< ``` | Vérifie si la valeur de l'opérande de gauche n'est pas inférieure à la valeur de l'opérande de droite, si oui, la condition devient vraie. | (a !< b) est faux. |
| ``` !> ``` | Vérifie si la valeur de l'opérande de gauche n'est pas supérieure à la valeur de l'opérande de droite, si oui, la condition devient vraie. | (a !> b) est vrai. |

## Opérateurs logiques SQLite

Voici une liste de tous les opérateurs logiques disponibles dans SQLite.

**Opérateur et description**

- ```AND``` - L'opérateur AND permet l'existence de plusieurs conditions dans la clause WHERE d'une instruction SQL.
- ```BETWEEN``` - L'opérateur BETWEEN est utilisé pour rechercher les valeurs qui se trouvent dans un ensemble de valeurs, étant donné la valeur minimale et la valeur maximale.
- ```EXISTS``` - L'opérateur EXISTS est utilisé pour rechercher la présence d'une ligne dans une table spécifiée qui répond à certains critères.
- ```IN``` - L'opérateur IN est utilisé pour comparer une valeur à une liste de valeurs littérales qui ont été spécifiées.
- ```NOT IN``` - La négation de l'opérateur IN qui est utilisé pour comparer une valeur à une liste de valeurs littérales qui ont été spécifiées.
- ```LIKE``` - L'opérateur LIKE est utilisé pour comparer une valeur à des valeurs similaires en utilisant des opérateurs génériques.
- ```GLOB``` - L'opérateur GLOB est utilisé pour comparer une valeur à des valeurs similaires à l'aide d'opérateurs génériques. En outre, GLOB est sensible à la casse, contrairement à LIKE.
- ```NOT``` - L'opérateur NOT inverse le sens de l'opérateur logique avec lequel il est utilisé. Par exemple : NOT EXISTS, NOT BETWEEN, NOT IN, etc. C'est l'opérateur de négation.
- ```OR``` - L'opérateur OR est utilisé pour combiner plusieurs conditions dans la clause WHERE d'une instruction SQL.
- ```IS NULL``` - L'opérateur NULL est utilisé pour comparer une valeur avec une valeur NULL.
- ```IS``` - L'opérateur IS fonctionne comme suit : =
- ```IS NOT``` - L'opérateur IS fonctionne comme !=
- ```||``` - Ajoute deux chaînes de caractères différentes et en crée une nouvelle..
- ```UNIQUE``` - L'opérateur UNIQUE recherche l'unicité de chaque ligne d'une table spécifiée (pas de doublons).

## Opérateurs Bitwise de SQLite

L'opérateur bitwise travaille sur les bits et effectue des opérations bit par bit. Voici la table de vérité de ```&``` et ```|```.

| **p** | **q** | **p & q** | **p | q** |
| --- | --- | --- | --- |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 |

Supposons que A = 60 ; et B = 13, alors en format binaire, ils seront comme suit -

```bash
A = 0011 1100
B = 0000 1101
-----------------
A&B = 0000 1100
A|B = 0011 1101
~A = 1100 0011
```

Les opérateurs Bitwise supportés par le langage SQLite sont listés dans le tableau suivant. Supposons que la variable A contient 60 et la variable B contient 13, alors -

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` & ``` | L'opérateur ET binaire copie un bit dans le résultat, s'il existe dans les deux opérandes. | (A & B) donnera 12 qui est 0000 1100 |
| ``` | ``` | L'opérateur OU binaire copie un bit, s'il existe dans l'un ou l'autre des opérandes. | (A | B) donnera 61 qui est 0011 1101 |
| ``` ~ ``` | L'opérateur de complémentation binaire à un est unaire et a pour effet de "retourner" les bits. | (~A ) donnera -61 qui est 1100 0011 en complément à 2 en raison d'un nombre binaire signé. |
| ``` << ``` | Opérateur de décalage binaire vers la gauche. La valeur de l'opérande de gauche est déplacée vers la gauche du nombre de bits spécifié par l'opérande de droite. | A << 2 donnera 240, soit 1111 0000. |
| ``` >> ``` | Opérateur de décalage binaire à droite. La valeur de l'opérande de gauche est déplacée vers la droite du nombre de bits spécifié par l'opérande de droite. | A >> 2 donnera 15 qui est 0000 1111 |