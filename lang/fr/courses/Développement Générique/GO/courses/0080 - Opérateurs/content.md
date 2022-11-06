Un opérateur est un symbole qui indique au compilateur d'effectuer des manipulations mathématiques ou logiques spécifiques. Le langage Go est riche en opérateurs intégrés et fournit les types d'opérateurs suivants : 

- Opérateurs arithmétiques
- Opérateurs relationnels
- Opérateurs logiques
- Opérateurs binaires
- Opérateurs d'affectation
- Opérateurs divers

Ce tutoriel explique un par un les opérateurs arithmétiques, relationnels, logiques, binaires, d'affectation et autres.

## Opérateurs arithmétiques

Le tableau suivant montre tous les opérateurs arithmétiques supportés par le langage Go. Supposons que la variable A contient 10 et la variable B contient 20, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` + ``` | Additionne deux opérandes | A + B donne 30 |
| ``` - ``` | Soustrait le deuxième opérande du premier | A - B donne -10 |
| ``` * ``` | Multiplie les deux opérandes | A * B donne 200 |
| ``` / ``` | Divise le numérateur par le dénominateur | B / A donne 2 |
| ``` % ``` | Opérateur modulo ; donne le reste après une division entière | B % A donne 0 |
| ``` ++ ``` | Opérateur d'incrémentation. Il augmente la valeur entière de un | A++ donne 11 |
| ``` -- ``` | Opérateur de décrémentation. Il diminue la valeur du nombre entier de un | A-- donne 9 |

## Opérateurs relationnels

Le tableau suivant liste tous les opérateurs relationnels supportés par le langage Go. Supposons que la variable A contient 10 et la variable B contient 20, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` == ``` | Il vérifie si les valeurs de deux opérandes sont égales ou non ; si oui, la condition devient vraie. | (A == B) est faux |
| ``` != ``` | Il vérifie si les valeurs de deux opérandes sont égales ou non ; si les valeurs ne sont pas égales, alors la condition devient vraie. | (A != B) est vrai |
| ``` > ``` | Il vérifie si la valeur de l'opérande de gauche est supérieure à la valeur de l'opérande de droite ; si oui, la condition devient vraie. | (A > B) est faux |
| ``` < ``` | Il vérifie si la valeur de l'opérande de gauche est inférieure à la valeur de l'opérande de droite ; si oui, la condition devient vraie. | (A < B) est vrai |
| ``` >= ``` | Elle vérifie si la valeur de l'opérande de gauche est supérieure ou égale à la valeur de l'opérande de droite ; si oui, la condition devient vraie. | (A >= B) est faux |
| ``` <= ``` | Il vérifie si la valeur de l'opérande de gauche est inférieure ou égale à la valeur de l'opérande de droite ; si oui, la condition devient vraie. | (A <= B) est vrai |

## Opérateurs logiques

Le tableau suivant liste tous les opérateurs logiques supportés par le langage Go. Supposons que la variable A vaut 1 et que la variable B vaut 0, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` && ``` | Appelé opérateur ET logique. Si les deux opérandes sont différents de zéro, alors la condition devient vraie. | (A && B) est faux |
| ``` || ``` | Appelé opérateur OU logique. Si l'un des deux opérandes est différent de zéro, alors la condition devient vraie. | (A || B) est vrai |
| ``` ! ``` | Appelé opérateur logique NOT. Il est utilisé pour inverser l'état logique de son opérande. Si une condition est vraie, l'opérateur logique NOT rendra faux. | !(A && B) est vrai |

Le tableau suivant montre tous les opérateurs logiques supportés par le langage Go. Supposons que la variable A est vraie et que la variable B est fausse, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` && ``` | Appelé opérateur ET logique. Si les deux opérandes sont différents de zéro, alors la condition devient vraie. | (A && B) est faux |
| ``` || ``` | Appelé opérateur OU logique. Si l'un des deux opérandes est différent de zéro, alors la condition devient vraie. | (A || B) est vrai |
| ``` ! ``` | Appelé opérateur logique NOT. Il est utilisé pour inverser l'état logique de son opérande. Si une condition est vraie, l'opérateur logique NOT rendra faux. | !(A && B) est vrai |

## Opérateurs binaires

Les opérateurs bit à bit travaillent sur les bits et effectuent des opérations bit à bit. Les tables de vérité pour ```&```, ```|```, et ```^``` sont les suivantes :

| **p** | **q** | **p & q** | **p | q** | **p ^ q** |
| --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 | 1 |

Supposons que A = 60 ; et B = 13. En format binaire, ils seront les suivants :

```bash
A = 0011 1100

B = 0000 1101

-----------------

A&B = 0000 1100

A|B = 0011 1101

A^B = 0011 0001

~A = 1100 0011
```

Les opérateurs Bitwise pris en charge par le langage C sont énumérés dans le tableau suivant. Supposons que la variable A contient 60 et la variable B contient 13, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` & ``` | L'opérateur binaire “ET” copie un bit dans le résultat s'il existe dans les deux opérandes. | (A & B) donne 12, soit 0000 1100 |
| ``` | ``` | L'opérateur binaire “OU” copie un bit s'il existe dans l'un ou l'autre des opérandes. | (A | B) donne 61, soit 0011 1101 |
| ``` ^ ``` | L'opérateur binaire “XOR” copie le bit s'il est activé dans un opérande mais pas dans les deux. | (A ^ B) donne 49, soit 0011 0001 |
| ``` << ``` | Opérateur de décalage binaire vers la gauche. La valeur de l'opérande de gauche est déplacée vers la gauche du nombre de bits spécifié par l'opérande de droite.  | A << 2 donne 240 soit 1111 0000 |
| ``` >> ``` | Opérateur de décalage binaire à droite. La valeur de l'opérande de gauche est déplacée vers la droite du nombre de bits spécifié par l'opérande de droite. | A >> 2 donne 15 soit 0000 1111 |

## Opérateurs d'assignation

Le tableau suivant liste tous les opérateurs d'affectation supportés par le langage Go :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` = ``` | Opérateur d'affectation simple, affecte les valeurs des opérandes de droite aux opérandes de gauche. | C = A + B assigne la valeur de A + B dans C |
| ``` += ``` | Opérateur d'affectation ET d’addition, il ajoute l'opérande de droite à l'opérande de gauche et assigne le résultat à l'opérande de gauche. | C += A est équivalent à C = C + A |
| ``` -= ``` | Opérateur d'affectation ET soustracteur, il soustrait l'opérande de droite de l'opérande de gauche et affecte le résultat à l'opérande de gauche. | C -= A est équivalent à C = C - A |
| ``` *= ``` | Opérateur d'affectation ET de multiplication, il multiplie l'opérande de droite par l'opérande de gauche et affecte le résultat à l'opérande de gauche. | C *= est équivalent à C = C * A |
| ``` /= ``` | Opérateur d'affectation ET de division, il divise l'opérande gauche avec l'opérande droite et affecte le résultat à l'opérande gauche. | C /= A est équivalent à C = C / A |
| ``` %= ``` | Opérateur d'affectation ET de modulo, il prend le modulo en utilisant deux opérandes et affecte le résultat à l'opérande de gauche. | C %= A est équivalent à C = C % A |
| ``` <<= ``` | Opérateur d'affectation ET de décalage vers la gauche | C <<= 2 est identique à C = C << 2 |
| ``` >>= ``` | Opérateur d'affectation ET de décalage vers la droite | C >>= 2 est identique à C = C >> 2 |
| ``` &= ``` | Opérateur d'affectation ET binaire | C &= 2 est identique à C = C & 2 |
| ``` ^= ``` | opérateur OU exclusif bit à bit et opérateur d'affectation | C ^= 2 est identique à C = C ^ 2 |
| ``` |= ``` | opérateur OU inclusif par bit et opérateur d'affectation | C |= 2 est identique à C = C | 2 |

## Opérateurs divers

Il existe quelques autres opérateurs importants supportés par le langage Go, notamment :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ``` & ``` | Renvoie l'adresse d'une variable. | &a ; fournit l'adresse réelle de la variable. |
| ``` * ``` | Pointer to a variable. | Pointeur vers une variable. |

## Prédominance des opérateurs en Go

La précédence des opérateurs détermine le regroupement des termes dans une expression. Cela affecte la manière dont une expression est évaluée. Certains opérateurs ont une préséance plus élevée que d'autres ; par exemple, l'opérateur de multiplication a une préséance plus élevée que l'opérateur d'addition.

Par exemple, x = 7 + 3 * 2 ; ici, on attribue à x la valeur 13, et non 20, car l'opérateur * a une priorité plus élevée que +, de sorte qu'il est d'abord multiplié par 3*2, puis additionné à 7.

Ici, les opérateurs ayant la plus haute priorité apparaissent en haut du tableau, ceux ayant la plus faible priorité apparaissent en bas. Dans une expression, les opérateurs ayant la plus haute priorité seront évalués en premier.

| **Catégorie** | **Opérateur** | **Associativité** |
| --- | --- | --- |
| Postfix ``` () [] -> . ++ - - ``` | Gauche à droite |
| Unaire ``` + - ! ~ ++ - - (type)* & sizeof ``` | Droite à gauche |
| Multiplicatif ``` XXX ``` | Gauche à droite |
| Additif ``` + - ``` | Gauche à droite |
| Décalage ``` << >> ``` | Gauche à droite |
| Relationnel ``` < <= > >= ``` | Gauche à droite |
| Égalité ``` == != ``` | Gauche à droite |
| ET binaire ``` & ``` | Gauche à droite |
| XOR binaire ``` ^ ``` | Gauche à droite |
| OR binaire ``` | ``` | Gauche à droite |
| ET Logique ``` && ``` | Gauche à droite |
| OU logique ``` || ``` | Gauche à droite |
| Affectation ``` = += -= *= /= %=>>= <<= &= ^= |= ``` | Droite à gauche |
| Virgule ``` , ``` | Gauche à droite |