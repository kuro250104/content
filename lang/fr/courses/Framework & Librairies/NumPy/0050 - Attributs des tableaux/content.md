## Introduction

Dans ce cours, nous allons aborder les différents attributs de tableaux de NumPy.

## ndarray.shape

Cet attribut de tableau renvoie un tuple composé des dimensions du tableau. Il peut également être utilisé pour redimensionner le tableau.

### Exemple 1

```python
import numpy as np 
a = np.array([[1,2,3],[4,5,6]]) 
print a.shape
```

Le résultat est le suivant -

```python
(2, 3)
```

### Exemple 2

```python
# this resizes the ndarray 
import numpy as np 

a = np.array([[1,2,3],[4,5,6]]) 
a.shape = (3,2) 
print a
```

Le résultat est le suivant -

```python
[
    [1, 2] 
    [3, 4] 
    [5, 6]
]
```

### Exemple 3

NumPy also provides a reshape function to resize an array.

```python
import numpy as np 
a = np.array([[1,2,3],[4,5,6]]) 
b = a.reshape(3,2) 
print b
```

Le résultat est le suivant -

```python
[
    [1, 2] 
    [3, 4] 
    [5, 6]
]
```

## ndarray.ndim

Cet attribut de tableau renvoie le nombre de dimensions du tableau.

### Exemple 1

```python
# an array of evenly spaced numbers 
import numpy as np 
a = np.arange(24) 
print a
```

Le résultat est le suivant -

```python
[0 1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16 17 18 19 20 21 22 23] 
```

### Exemple 2

```python
# this is one dimensional array 
import numpy as np 
a = np.arange(24) 
a.ndim  

# now reshape it 
b = a.reshape(2,4,3) 
print b 
# b is having three dimensions
```

Le résultat est le suivant -

```python
[
    [
        [ 0,  1,  2] 
        [ 3,  4,  5] 
        [ 6,  7,  8] 
        [ 9, 10, 11]
    ]  
    [
        [12, 13, 14] 
        [15, 16, 17]
        [18, 19, 20] 
        [21, 22, 23]
    ]
] 
```

## numpy.itemsize

Cet attribut de tableau renvoie la longueur de chaque élément du tableau en octets.

### Exemple 1

```python
# dtype of array is int8 (1 byte) 
import numpy as np 
x = np.array([1,2,3,4,5], dtype = np.int8) 
print x.itemsize
```

Le résultat est le suivant -

```python
1
```

### Exemple 2

```python
# dtype of array is now float32 (4 bytes) 
import numpy as np 
x = np.array([1,2,3,4,5], dtype = np.float32) 
print x.itemsize
```

Le résultat est le suivant -

```python
4
```

## numpy.flags

L'objet ndarray possède les attributs suivants. Ses valeurs actuelles sont retournées par cette fonction.

**Attribut et description**

- **C_CONTIGUOUS (C)** - Les données sont dans un seul segment contigu de type C.
- **F_CONTIGUOUS (F)** - Les données sont dans un seul segment contigu, de type Fortran.
- **OWNDATA (O)** - Le tableau possède la mémoire qu'il utilise ou l'emprunte à un autre objet.
- **WRITEABLE (W)** - La zone de données peut être écrite. La valeur False verrouille les données et les rend accessibles en lecture seule.
- **ALIGNED (A)** - Les données et tous les éléments sont alignés de manière appropriée pour le matériel.
- **UPDATEIFCOPY (U)** - Ce tableau est une copie d'un autre tableau. Lorsque ce tableau est désalloué, le tableau de base sera mis à jour avec le contenu de ce tableau.

### Exemple

L'exemple suivant montre les valeurs actuelles des drapeaux.

```python
import numpy as np 
x = np.array([1,2,3,4,5]) 
print x.flags
```

Le résultat est le suivant -

```python
C_CONTIGUOUS : True 
F_CONTIGUOUS : True 
OWNDATA : True 
WRITEABLE : True 
ALIGNED : True 
UPDATEIFCOPY : False
```