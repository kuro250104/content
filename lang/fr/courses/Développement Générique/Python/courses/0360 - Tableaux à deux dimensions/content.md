Un tableau à deux dimensions est un tableau dans un tableau. C'est un tableau de tableaux. Dans ce type de tableau, la position d'un élément de données est indiquée par deux indices au lieu d'un. Il représente donc un tableau avec des rangées et des colonnes de données.

Dans l'exemple ci-dessous d'un tableau à deux dimensions, observez que chaque élément du tableau est également un tableau.

Prenons l'exemple de l'enregistrement des températures 4 fois par jour, tous les jours. Parfois, l'instrument d'enregistrement peut être défectueux et nous n'enregistrons pas les données. Ces données pour 4 jours peuvent être présentées sous la forme d'un tableau à deux dimensions comme ci-dessous.

```bash
Day 1 - 11 12 5 2 
Day 2 - 15 6 10 
Day 3 - 10 8 12 5 
Day 4 - 12 15 8 6 
```

Les données ci-dessus peuvent être représentées comme un tableau à deux dimensions comme ci-dessous.

```python
T = [[11, 12, 5, 2], [15, 6,10], [10, 8, 12, 5], [12,15,8,6]]
```

## Accès aux valeurs

Les éléments de données des tableaux à deux dimensions sont accessibles à l'aide de deux indices. Un indice se référant au tableau principal ou parent et un autre indice se référant à la position de l'élément de données dans le tableau interne. Si nous ne mentionnons qu'un seul indice, le tableau interne entier est imprimé pour cette position d'indice.

### Exemple

L'exemple ci-dessous illustre son fonctionnement.

```python
from array import *

T = [[11, 12, 5, 2], [15, 6,10], [10, 8, 12, 5], [12,15,8,6]]

print(T[0])

print(T[1][2])
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
[11, 12, 5, 2]
10
```

Pour imprimer l'intégralité d'un tableau à deux dimensions, nous pouvons utiliser la boucle for de Python comme indiqué ci-dessous. Nous utilisons la fin de ligne pour imprimer les valeurs dans les différentes lignes.

### Exemple

```python
from array import *

T = [[11, 12, 5, 2], [15, 6,10], [10, 8, 12, 5], [12,15,8,6]]
for r in T:
    for c in r:
        print(c,end = " ")
    print()
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
11 12  5 2 
15  6 10 
10  8 12 5 
12 15  8 6 
```

## Insertion de valeurs

Nous pouvons insérer de nouveaux éléments de données à une position spécifique en utilisant la méthode ```insert()``` et en spécifiant l'index.

### Exemple

Dans l'exemple ci-dessous, un nouvel élément de données est inséré à la position d'index 2.

```python
from array import *
T = [[11, 12, 5, 2], [15, 6,10], [10, 8, 12, 5], [12,15,8,6]]

T.insert(2, [0,5,11,13,6])

for r in T:
    for c in r:
        print(c,end = " ")
    print()
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
11 12  5  2 
15  6 10 
0  5 11 13 6 
10  8 12  5 
12 15  8  6 
```

## Mise à jour des valeurs

Nous pouvons mettre à jour l'ensemble du tableau interne ou certains éléments de données spécifiques du tableau interne en réaffectant les valeurs à l'aide de l'index du tableau.

### Exemple

```python
from array import *

T = [[11, 12, 5, 2], [15, 6,10], [10, 8, 12, 5], [12,15,8,6]]

T[2] = [11,9]
T[0][3] = 7
for r in T:
    for c in r:
        print(c,end = " ")
    print()
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
11 12 5  7 
15  6 10 
11  9 
12 15 8  6 
```

## Suppression des valeurs

Nous pouvons supprimer l'ensemble du tableau interne ou certains éléments de données spécifiques du tableau interne en affectant les valeurs à l'aide de la méthode ```del()``` avec index. Mais si vous devez supprimer des éléments de données spécifiques dans l'un des tableaux internes, utilisez le processus de mise à jour décrit ci-dessus.

### Exemple

```python
from array import *
T = [[11, 12, 5, 2], [15, 6,10], [10, 8, 12, 5], [12,15,8,6]]

del T[3]

for r in T:
    for c in r:
        print(c,end = " ")
    print()
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
11 12 5 2 
15 6 10 
10 8 12 5 
```
