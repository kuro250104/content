Les opérateurs sont des constructions qui peuvent manipuler la valeur des opérandes. Considérons l'expression ```4 + 5 = 9```. Ici, ```4``` et ```5``` sont appelés **les opérandes** et ```+``` est appelé l'**opérateur**.

## Types d'opérateurs

Le langage Python prend en charge les types d'opérateurs suivants :

- Opérateurs arithmétiques
- Opérateurs de comparaison (relationnels)
- Opérateurs d'affectations
- Opérateurs logiques
- Opérateurs binaires
- Opérateurs d'appartenance
- Opérateurs d'identité

Examinons tous les opérateurs un par un.

## Opérateurs arithmétiques Python

Supposons que la variable ```a``` contient la valeur ```10``` et que la variable ```b``` contient la valeur ```21```, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ```+ Addition``` | Ajoute l’opérande de droite à l’opérande de gauche. | a + b = 31 |
| ```- Soustraction``` | Soustrait l'opérande de droite de l'opérande de gauche. | a – b = -11 |
| ```* Multiplication``` | Multiplie l'opérande de droite de l'opérande de gauche. | a * b = 210 |
| ```/ Division``` | Divise l'opérande de gauche par l'opérande de droite. | b / a = 2.1 |
| ```% Modulus``` | Divise l'opérande de gauche par l'opérande de droite et renvoie le reste. | b % a = 1 |
| ```** Exposant```| Effectue un calcul exponentiel (puissance) sur les opérateurs. | a**b = 10 puissances 20 |
| ```// Division plancher```| La division d'opérandes où le résultat est le quotient dans lequel les chiffres après la virgule sont supprimés. Mais si l'un des opérandes est négatif, le résultat est flotté, c'est-à-dire arrondi à partir de zéro (vers l'infini négatif). | 9//2 = 4 et 9.0//2.0 = 4.0, -11//3 = -4, -11.0//3 = -4.0 |

## Opérateurs de comparaison Python

Ces opérateurs comparent les valeurs de part et d'autre et décident de la relation entre elles. Ils sont également appelés opérateurs relationnels.

Supposons que la variable ```a``` possède la valeur ```10``` et que la variable ```b``` possède la valeur ```20```, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ```==``` | Si les valeurs de deux opérandes sont égales, alors la condition devient vraie. | (a == b) n'est pas vrai. |
| ```!=``` | Si les valeurs des deux opérandes ne sont pas égales, alors la condition devient vraie. | (a != b) est vrai. |
| ```>``` | Si la valeur de l'opérande de gauche est supérieure à la valeur de l'opérande de droite, alors la condition devient vraie. | (a > b) n'est pas vrai. |
| ```<``` | Si la valeur de l'opérande de gauche est inférieure à la valeur de l'opérande de droite, alors la condition devient vraie. | (a < b) est vrai. |
| ```>=``` | Si la valeur de l'opérande de gauche est supérieure ou égale à la valeur de l'opérande de droite, alors la condition devient vraie. | (a >= b) n'est pas vrai. |
| ```<=``` | Si la valeur de l'opérande de gauche est inférieure ou égale à la valeur de l'opérande de droite, alors la condition devient vraie. | (a <= b) est vrai. |

## Opérateurs d'assignation Python

Supposons que la variable ```a``` contient la valeur ```10``` et que la variable ```b``` contient la valeur ```20```, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ```=``` | Affecte les valeurs des opérandes de droite aux opérandes de gauche. | c = a + b affecte la valeur de a + b à c |
| ```+= Ajoute AND``` | Il ajoute l'opérande de droite à l'opérande de gauche et assigne le résultat à l'opérande de gauche. | c += a est équivalent à c = c + a |
| ```-= Soustraire AND``` | Il soustrait l'opérande de droite de l'opérande de gauche et assigne le résultat à l'opérande de gauche. | c -= est équivalent à c = c - a |
| ```*= Multiplie AND``` | Il multiplie l'opérande de droite par l'opérande de gauche et assigne le résultat à l'opérande de gauche. | c *= est équivalent à c = c * a |
| ```/= Divise AND``` | Il divise l'opérande gauche avec l'opérande droite et assigne le résultat à l'opérande gauche. | c /= est équivalent à c = c / ac /= est équivalent à c = c / a |
| ```%= Modulus AND``` | Il prend le modulus en utilisant deux opérandes et assigne le résultat à l'opérande de gauche. | c %= est équivalent à c = c % a |
| ```**= Exponent AND``` | Effectue un calcul exponentiel (puissance) sur les opérateurs et attribue une valeur à l'opérande de gauche. | c **= est équivalent à c = c ** a |
| ```//= Division plancher``` | Il effectue une division plancher sur les opérateurs et attribue une valeur à l'opérande de gauche. | c //= est équivalent à c = c // a |

## Opérateurs Bitwise de Python

L'opérateur Bitwise fonctionne sur les bits et effectue des opérations bit par bit. Supposons que ```a = 60``` ; et ```b = 13``` ; Maintenant, en format binaire, ils seront comme suit :

```bash
a = 0011 1100
b = 0000 1101
-----------------
a&b = 0000 1100
a|b = 0011 1101
a^b = 0011 0001
~a = 1100 0011
```

La fonction intégrée de Python ```bin()``` peut être utilisée pour obtenir la représentation binaire d'un nombre entier.

Les opérateurs Bitwise suivants sont supportés par le langage Python :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ```& Binaire AND``` | L'opérateur copie un bit dans le résultat, s'il existe dans les deux opérandes. | (a & b) (signifie 0000 1100) |
| ```| Binaire OR``` | Il copie un bit, s'il existe dans l'un ou l'autre des opérandes. | (a | b) = 61 (signifie 0011 1101) |
| ```^ Binaire XOR``` | Il copie le bit, s'il est activé dans un opérande mais pas dans les deux. | (a ^ b) = 49 (signifie 0011 0001) |
| ```~ Complément binaire à un``` | Il est unaire et a pour effet de "retourner" les bits. | (~a ) = -61 (signifie 1100 0011 sous forme de complément à 2 en raison d'un nombre binaire signé) |
| ```<< Décalage binaire à gauche``` | La valeur de l'opérande de gauche est déplacée vers la gauche du nombre de bits spécifié par l'opérande de droite. | a << 2 = 240 (signifie 1111 0000) |
| ```>> Décalage binaire à droite``` | La valeur de l'opérande de gauche est déplacée vers la droite du nombre de bits spécifié par l'opérande de droite. | a >> 2 = 15 (signifie 0000 1111) |

## Opérateurs logiques Python

Les opérateurs logiques suivants sont supportés par le langage Python. Supposons que la variable ```a``` soit ```vraie``` et que la variable ```b``` soit ```fausse```, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ```et Logique AND``` | Si les deux opérandes sont vrais, alors la condition devient vraie. | (a and b) est faux. |
| ```ou Logique OR``` | Si l'un des deux opérandes est différent de zéro, la condition devient vraie. | (a or b) est vrai. |
| ```non Logique NOT``` | Utilisé pour inverser l'état logique de son opérande. | Pas(a et b) est Vrai. |

## Opérateurs d'appartenance Python

Les opérateurs d'appartenance de Python testent l'appartenance à une séquence, telle que des chaînes de caractères, des listes ou des tuples. Il existe deux opérateurs d'appartenance, comme expliqué ci-dessous :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ```in``` | Évalue à true si elle trouve une variable dans la séquence spécifiée et false sinon. | x dans y, ici en résulte un 1 si x est un membre de la séquence y. |
| ```not in``` | Évalue à true s'il ne trouve pas de variable dans la séquence spécifiée et à false sinon. | x pas dans y, ici pas en résulte un 1 si x n'est pas un membre de la séquence y. |

## Opérateurs d'identité Python

Les opérateurs d'identité comparent les emplacements mémoire de deux objets. Il existe deux opérateurs d'identité, comme expliqué ci-dessous :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ```is``` | Évalue à true si les variables de part et d'autre de l'opérateur pointent vers le même objet et à false sinon. | x est y, ici le résultat est 1 si id(x) est égal à id(y). |
| ```is not``` | Donne la valeur false si les variables de part et d'autre de l'opérateur pointent vers le même objet et true sinon. | x n'est pas y, Ici, il n'y a pas de résultats en 1 si id(x) n'est pas égal à id(y). |

## Prédominance des opérateurs Python

Le tableau suivant répertorie tous les opérateurs, de la plus haute préséance à la plus basse :

| **Opérateur** | **Déscription** |
| --- | --- |
| ```**``` | Exponentiation (augmentation à la puissance). |
| ```~ + -``` | Complément, unaire plus et moins (les noms de méthode pour les deux derniers sont +@ et -@). |
| ```* / % //``` | Multiplier, diviser, modulo et division plancher. |
| ```+ -``` | Addition et soustraction. |
| ```>> <<``` | Décalage binaire à droite et à gauche. |
| ```&``` | AND binaire. |
| ```^``` | "OR" exclusif binaire et "OR" ordinaire. |
| ```<= < > >=``` | Opérateurs de comparaison. |
| ```<> == !=``` | Opérateurs d'égalité. |
| ```= %= /= //= -= += *= **=``` | Opérateurs d'assignation. |
| ```is is not``` | Opérateurs d'identité. |
| ```in not in``` | Opérateurs d'adhésion. |
| ```not or and``` | Opérateurs logiques. |
