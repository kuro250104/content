## Introduction

Le paquet NumPy contient une bibliothèque de matrices numpy.matlib. Ce module possède des fonctions qui renvoient des matrices au lieu d'objets ndarray.

## matlib.empty()

La fonction ```matlib.empty()``` renvoie une nouvelle matrice sans initialiser les entrées. La fonction prend les paramètres suivants.

```python
numpy.matlib.empty(shape, dtype, order)
```

Où,

**Paramètre et description**

- **shape** - int ou tuple d'int définissant la forme de la nouvelle matrice
- **Dtype** - Facultatif. Type de données de la sortie
- **order** - C ou F

### Exemple

```python
import numpy.matlib 
import numpy as np 

print np.matlib.empty((2,2)) 
# filled with random data
```

Il produira le résultat suivant -

```python
[
    [ 2.12199579e-314,   4.24399158e-314] 
    [ 4.24399158e-314,   2.12199579e-314]
]
```

## numpy.matlib.zeros()

Cette fonction renvoie la matrice remplie de zéros.

### Exemple

```python
import numpy.matlib 
import numpy as np 
print np.matlib.zeros((2,2))
```

Il produira le résultat suivant -

```python
[
    [ 0.  0.] 
    [ 0.  0.]
]
```

## numpy.matlib.ones()

Cette fonction renvoie la matrice remplie de 1.

### Exemple

```python
import numpy.matlib 
import numpy as np 
print np.matlib.ones((2,2))
```

Il produira le résultat suivant -

```python
[
    [ 1.  1.] 
    [ 1.  1.]
]
```

## numpy.matlib.eye()

Cette fonction renvoie une matrice avec 1 le long des éléments diagonaux et les zéros ailleurs. La fonction prend les paramètres suivants.

```python
numpy.matlib.eye(n, M,k, dtype)
```

Où,

**Paramètre et description**

- **n** - Le nombre de lignes de la matrice résultante
- **M** - Le nombre de colonnes, la valeur par défaut est n.
- **k** - Indice de la diagonale
- **dtype** - Type de données de la sortie

### Exemple

```python
import numpy.matlib 
import numpy as np 
print np.matlib.eye(n = 3, M = 4, k = 0, dtype = float)
```

Il produira le résultat suivant -

```python
[
    [ 1.  0.  0.  0.] 
    [ 0.  1.  0.  0.] 
    [ 0.  0.  1.  0.]
]
```

## numpy.matlib.identity()

La fonction numpy.matlib.identity() retourne la matrice d'identité de la taille donnée. Une matrice d'identité est une matrice carrée dont tous les éléments diagonaux valent 1.

### Exemple

```python
import numpy.matlib 
import numpy as np 
print np.matlib.identity(5, dtype = float)
```

Il produira le résultat suivant -

```python
[
    [ 1.  0.  0.  0.  0.] 
    [ 0.  1.  0.  0.  0.] 
    [ 0.  0.  1.  0.  0.] 
    [ 0.  0.  0.  1.  0.] 
    [ 0.  0.  0.  0.  1.]
]
```

## numpy.matlib.rand()

La fonction ```numpy.matlib.rand()``` retourne une matrice de la taille donnée remplie de valeurs aléatoires.

### Exemple

```python
import numpy.matlib 
import numpy as np 
print np.matlib.rand(3,3)
```

Il produira le résultat suivant -

```python
[
    [ 0.82674464  0.57206837  0.15497519] 
    [ 0.33857374  0.35742401  0.90895076] 
    [ 0.03968467  0.13962089  0.39665201]
]
```

Notez qu'une matrice est toujours bidimensionnelle, alors que ndarray est un tableau à n dimensions. Les deux objets sont interconvertibles.

### Exemple

```python
import numpy.matlib 
import numpy as np  

i = np.matrix('1,2;3,4') 
print i
```

Il produira le résultat suivant -

```python
[
    [1  2] 
    [3  4]
]
```

### Exemple

```python
import numpy.matlib 
import numpy as np  

j = np.asarray(i) 
print j
```

Il produira le résultat suivant -

```python
[
    [1  2] 
    [3  4]
]
```

### Exemple

```python
import numpy.matlib 
import numpy as np  

k = np.asmatrix (j) 
print k
```

Il produira le résultat suivant -

```python
[
    [1  2] 
    [3  4]
]
```