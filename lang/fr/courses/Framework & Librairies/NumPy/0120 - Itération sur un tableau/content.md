## Introduction

Le paquet NumPy contient un objet itérateur ```numpy.nditer```. Il s'agit d'un objet itérateur multidimensionnel efficace qui permet d'itérer sur un tableau. Chaque élément d'un tableau est visité en utilisant l'interface standard Iterator de Python.

Créons un tableau 3X4 en utilisant la fonction ```arange()``` et itérons-le en utilisant ```nditer```.

### Exemple 1

```python
import numpy as np
a = np.arange(0,60,5)
a = a.reshape(3,4)

print 'Original array is:'
print a
print '\n'

print 'Modified array is:'
for x in np.nditer(a):
    print x,
```

La sortie de ce programme est la suivante -

```python
Original array is:
[
    [ 0 5 10 15]
    [20 25 30 35]
    [40 45 50 55]
]

Modified array is:
0 5 10 15 20 25 30 35 40 45 50 55
```

### Exemple 2

L'ordre d'itération est choisi pour correspondre à la disposition de la mémoire d'un tableau, sans tenir compte d'un ordre particulier. Cela peut être vu en itérant sur la transposée du tableau ci-dessus.

```python
import numpy as np 
a = np.arange(0,60,5) 
a = a.reshape(3,4) 

print 'Original array is:'
print a 
print '\n'  

print 'Transpose of the original array is:' 
b = a.T 
print b 
print '\n'  

print 'Modified array is:' 
for x in np.nditer(b): 
    print x,
```

La sortie du programme ci-dessus est la suivante -

```python
Original array is:
[
    [ 0 5 10 15]
    [20 25 30 35]
    [40 45 50 55]
]

Transpose of the original array is:
[
    [ 0 20 40]
    [ 5 25 45]
    [10 30 50]
    [15 35 55]
]

Modified array is:
0 5 10 15 20 25 30 35 40 45 50 55
```

## Ordre d'itération

Si les mêmes éléments sont stockés dans un ordre de type F, l'itérateur choisit la manière la plus efficace d'itérer sur un tableau.

### Example 1

```python
import numpy as np
a = np.arange(0,60,5)
a = a.reshape(3,4)
print 'Original array is:'
print a
print '\n'

print 'Transpose of the original array is:'
b = a.T
print b
print '\n'

print 'Sorted in C-style order:'
c = b.copy(order = 'C')
print c
for x in np.nditer(c):
    print x,

print '\n'

print 'Sorted in F-style order:'
c = b.copy(order = 'F')
print c
for x in np.nditer(c):
    print x,
```

Sa sortie serait la suivante -

```python
Original array is:
[
    [ 0 5 10 15]
    [20 25 30 35]
    [40 45 50 55]
]

Transpose of the original array is:
[
    [ 0 20 40]
    [ 5 25 45]
    [10 30 50]
    [15 35 55]
]

Sorted in C-style order:
[
    [ 0 20 40]
    [ 5 25 45]
    [10 30 50]
    [15 35 55]
]
0 20 40 5 25 45 10 30 50 15 35 55

Sorted in F-style order:
[
    [ 0 20 40]
    [ 5 25 45]
    [10 30 50]
    [15 35 55]
]
0 5 10 15 20 25 30 35 40 45 50 55
```

### Exemple 2

Il est possible de forcer l'objet **nditer** à utiliser un ordre spécifique en le mentionnant explicitement.

```python
import numpy as np 
a = np.arange(0,60,5) 
a = a.reshape(3,4) 

print 'Original array is:' 
print a 
print '\n'  

print 'Sorted in C-style order:' 
for x in np.nditer(a, order = 'C'): 
    print x,  
print '\n' 

print 'Sorted in F-style order:' 
for x in np.nditer(a, order = 'F'): 
    print x,
```

Sa sortie serait -

```python
Original array is:
[
    [ 0 5 10 15]
    [20 25 30 35]
    [40 45 50 55]
]

Sorted in C-style order:
0 5 10 15 20 25 30 35 40 45 50 55

Sorted in F-style order:
0 20 40 5 25 45 10 30 50 15 35 55
```

## Modifier les valeurs d'un tableau

L'objet **nditer** possède un autre paramètre optionnel appelé **op_flags**. Sa valeur par défaut est read-only, mais il peut être défini en mode read-write ou write-only. Cela permettra de modifier les éléments du tableau en utilisant cet itérateur.

### Exemple

```python
import numpy as np
a = np.arange(0,60,5)
a = a.reshape(3,4)
print 'Original array is:'
print a
print '\n'

for x in np.nditer(a, op_flags = ['readwrite']):
    x[...] = 2*x
print 'Modified array is:'
print a
```

Sa sortie est la suivante -

```python
Original array is:
[
    [ 0 5 10 15]
    [20 25 30 35]
    [40 45 50 55]
]

Modified array is:
[
    [ 0 10 20 30]
    [ 40 50 60 70]
    [ 80 90 100 110]
]
```

## Boucle externe

Le constructeur de la classe nditer possède un paramètre '**flags**', qui peut prendre les valeurs suivantes -

**Paramètre et description**

- **c_index** - L'indice C_order peut être suivi
- **f_index** - L'index Fortran_order est suivi
- **multi-index** - Possibilité de suivre le type d'index avec un par itération
- **external_loop** - Les valeurs données sont des tableaux unidimensionnels à valeurs multiples au lieu de tableaux à dimension zéro.

### Exemple

Dans l'exemple suivant, les tableaux unidimensionnels correspondant à chaque colonne sont parcourus par l'itérateur.

```python
import numpy as np 
a = np.arange(0,60,5) 
a = a.reshape(3,4) 

print 'Original array is:' 
print a 
print '\n'  

print 'Modified array is:' 
for x in np.nditer(a, flags = ['external_loop'], order = 'F'):
    print x,
```

Le résultat est le suivant -

```python
Original array is:
[
    [ 0 5 10 15]
    [20 25 30 35]
    [40 45 50 55]
]

Modified array is:
[ 0 20 40] [ 5 25 45] [10 30 50] [15 35 55]
```

## Iteration de diffusion

Si deux tableaux sont **diffusables**, un objet **nditer** combiné est capable d'itérer sur eux simultanément. En supposant qu'un tableau a à une dimension de 3X4, et qu'il existe un autre tableau b de dimension 1X4, l'itérateur du type suivant est utilisé (le tableau b est diffusé à la taille de a).

### Exemple

```python
import numpy as np 
a = np.arange(0,60,5) 
a = a.reshape(3,4) 

print 'First array is:' 
print a 
print '\n'  

print 'Second array is:' 
b = np.array([1, 2, 3, 4], dtype = int) 
print b  
print '\n' 

print 'Modified array is:' 
for x,y in np.nditer([a,b]): 
    print "%d:%d
```

Sa sortie serait la suivante -

```python
First array is:
[
    [ 0 5 10 15]
    [20 25 30 35]
    [40 45 50 55]
]

Second array is:
[1 2 3 4]

Modified array is:
0:1 5:2 10:3 15:4 20:1 25:2 30:3 35:4 40:1 45:2 50:3 55:4
```