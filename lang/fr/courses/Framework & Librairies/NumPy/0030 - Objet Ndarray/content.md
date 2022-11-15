## Introduction

L'objet le plus important défini dans NumPy est un type de tableau à N dimensions appelé ndarray. Il décrit la collection d'éléments du même type. Les éléments de la collection sont accessibles à l'aide d'un index basé sur zéro.

Chaque élément d'un ndarray prend la même taille de bloc dans la mémoire. Chaque élément d'un ndarray est un objet de type données (appelé dtype).

Tout élément extrait de l'objet ndarray (par découpage) est représenté par un objet Python de l'un des types scalaires de tableau.

Une instance de la classe ndarray peut être construite par différentes routines de création de tableau décrites plus loin dans le tutoriel. Le tableau de base ndarray est créé à l'aide d'une fonction de tableau dans NumPy, comme suit -

```python
numpy.array 
```

Elle crée un ndarray à partir de n'importe quel objet exposant l'interface array, ou à partir de n'importe quelle méthode qui retourne un array.

```python
numpy.array(object, dtype = None, copy = True, order = None, subok = False, ndmin = 0)
```

Le constructeur ci-dessus prend les paramètres suivants -

**Paramètres & Description**

- **object** - Tout objet exposant la méthode de l'interface array renvoie un array, ou toute séquence (imbriquée).
- **dtype** - Type de données souhaité pour le tableau, facultatif
- **copy** - Facultatif. Par défaut (true), l'objet est copié.
- **order** - C (majeure de la ligne) ou F (majeure de la colonne) ou A (quelconque) (par défaut)
- **subok** - Par défaut, le tableau retourné est forcé d'être un tableau de classe de base. Si vrai, les sous-classes passées par
- **ndmin** - Spécifie les dimensions minimales du tableau résultant

Jetez un coup d'œil aux exemples suivants pour mieux comprendre.

### Exemple 1

```python
import numpy as np 
a = np.array([1,2,3]) 
print a
```

Le résultat est le suivant -

```python
[1, 2, 3]
```

### Example 2

```python
# more than one dimensions 
import numpy as np 
a = np.array([[1, 2], [3, 4]]) 
print a
```

Le résultat est le suivant -

```python
[
    [1, 2] 
    [3, 4]
]
```

### Example 3

```python
# minimum dimensions 
import numpy as np 
a = np.array([1, 2, 3,4,5], ndmin = 2) 
print a
```

Le résultat est le suivant -

```python
[[1, 2, 3, 4, 5]]
```

### Example 4

```python
# dtype parameter 
import numpy as np 
a = np.array([1, 2, 3], dtype = complex) 
print a
```

Le résultat est le suivant -

```python
[ 1.+0.j,  2.+0.j,  3.+0.j]
```

L'objet ndarray consiste en un segment unidimensionnel contigu de la mémoire de l'ordinateur, associé à un schéma d'indexation qui fait correspondre chaque élément à un emplacement dans le bloc de mémoire. Le bloc de mémoire contient les éléments dans un ordre de rangée majeure (style C) ou un ordre de colonne majeure (style FORTRAN ou MatLab).