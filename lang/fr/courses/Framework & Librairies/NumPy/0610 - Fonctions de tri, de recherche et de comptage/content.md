## Introduction

Une variété de fonctions liées au tri sont disponibles dans NumPy. Ces fonctions de tri mettent en œuvre différents algorithmes de tri, chacun d'entre eux étant caractérisé par la vitesse d'exécution, les performances dans le pire des cas, l'espace de travail requis et la stabilité des algorithmes. Le tableau suivant présente la comparaison de trois algorithmes de tri.

| **genre** | **vitesse** | **pire cas** | **espace de travail** | **stable** |
| --- | --- | --- | --- | --- |
| quicksort | 1 | O(n^2) | 0 | non |
| mergesort | 2 | O(n*log(n)) | ~n/2 | oui |
| heapsort | 3 | O(n*log(n)) | 0 | non |

## numpy.sort()

La fonction ```sort()``` renvoie une copie triée du tableau d'entrée. Elle possède les paramètres suivants

```python
numpy.sort(a, axis, kind, order)
```

Où,

**Paramètre et description**

- **a** - Tableau à trier
- **axis** - L'axe le long duquel le tableau doit être trié. S'il n'y en a pas, le tableau est aplati et trié sur le dernier axe.
- **kind** - La valeur par défaut est quicksort
- **order** - Si le tableau contient des champs, l'ordre des champs à trier.

### Exemple

```python
import numpy as np  
a = np.array([[3,7],[9,1]]) 

print 'Our array is:' 
print a 
print '\n'

print 'Applying sort() function:' 
print np.sort(a) 
print '\n' 

print 'Sort along axis 0:' 
print np.sort(a, axis = 0) 
print '\n'  

# Order parameter in sort function 
dt = np.dtype([('name', 'S10'),('age', int)]) 
a = np.array([("raju",21),("anil",25),("ravi", 17), ("amar",27)], dtype = dt) 

print 'Our array is:' 
print a 
print '\n'  

print 'Order by name:' 
print np.sort(a, order = 'name')
```

Il produira le résultat suivant -

```python
Our array is:
[
    [3 7]
    [9 1]
]

Applying sort() function:
[
    [3 7]
    [1 9]
]

Sort along axis 0:
[
    [3 1]
    [9 7]
]

Our array is:
[('raju', 21) ('anil', 25) ('ravi', 17) ('amar', 27)]

Order by name:
[('amar', 27) ('anil', 25) ('raju', 21) ('ravi', 17)]
```

## numpy.argsort()

La fonction ```numpy.argsort()``` effectue un tri indirect sur le tableau d'entrée, le long de l'axe donné et en utilisant un type de tri spécifié pour retourner le tableau des indices des données. Ce tableau d'indices est utilisé pour construire le tableau trié.

### Exemple

```python
import numpy as np 
x = np.array([3, 1, 2]) 

print 'Our array is:' 
print x 
print '\n'  

print 'Applying argsort() to x:' 
y = np.argsort(x) 
print y 
print '\n'  

print 'Reconstruct original array in sorted order:' 
print x[y] 
print '\n'  

print 'Reconstruct the original array using loop:' 
for i in y: 
    print x[i],
```

Il produira le résultat suivant -

```python
Our array is:
[3 1 2]

Applying argsort() to x:
[1 2 0]

Reconstruct original array in sorted order:
[1 2 3]

Reconstruct the original array using loop:
1 2 3
```

## numpy.lexsort()

effectue un tri indirect en utilisant une séquence de clés. Les clés peuvent être vues comme une colonne dans une feuille de calcul. La fonction renvoie un tableau d'indices, qui permet d'obtenir les données triées. Notez que la dernière clé est la clé primaire du tri.

### Exemple

```python
import numpy as np 

nm = ('raju','anil','ravi','amar') 
dv = ('f.y.', 's.y.', 's.y.', 'f.y.') 
ind = np.lexsort((dv,nm)) 

print 'Applying lexsort() function:' 
print ind 
print '\n'  

print 'Use this index to get sorted data:' 
print [nm[i] + ", " + dv[i] for i in ind]
```

Il produira le résultat suivant -

```python
Applying lexsort() function:
[3 1 0 2]

Use this index to get sorted data:
['amar, f.y.', 'anil, s.y.', 'raju, f.y.', 'ravi, s.y.']
```

Le module NumPy dispose d'un certain nombre de fonctions permettant de rechercher à l'intérieur d'un tableau. Des fonctions permettant de trouver le maximum, le minimum ainsi que les éléments satisfaisant une condition donnée sont disponibles.

## numpy.argmax() et numpy.argmin()

Ces deux fonctions renvoient les indices des éléments maximum et minimum respectivement le long de l'axe donné.

### Exemple

```python
import numpy as np 
a = np.array([[30,40,70],[80,20,10],[50,90,60]]) 

print 'Our array is:' 
print a 
print '\n' 

print 'Applying argmax() function:' 
print np.argmax(a) 
print '\n'  

print 'Index of maximum number in flattened array' 
print a.flatten() 
print '\n'  

print 'Array containing indices of maximum along axis 0:' 
maxindex = np.argmax(a, axis = 0) 
print maxindex 
print '\n'  

print 'Array containing indices of maximum along axis 1:' 
maxindex = np.argmax(a, axis = 1) 
print maxindex 
print '\n'  

print 'Applying argmin() function:' 
minindex = np.argmin(a) 
print minindex 
print '\n'  

print 'Flattened array:' 
print a.flatten()[minindex] 
print '\n'  

print 'Flattened array along axis 0:' 
minindex = np.argmin(a, axis = 0) 
print minindex
print '\n'

print 'Flattened array along axis 1:' 
minindex = np.argmin(a, axis = 1) 
print minindex
```

Il produira le résultat suivant -

```python
Our array is:
[
    [30 40 70]
    [80 20 10]
    [50 90 60]
]

Applying argmax() function:
7

Index of maximum number in flattened array
[30 40 70 80 20 10 50 90 60]

Array containing indices of maximum along axis 0:
[1 2 0]

Array containing indices of maximum along axis 1:
[2 0 1]

Applying argmin() function:
5

Flattened array:
10

Flattened array along axis 0:
[0 1 1]

Flattened array along axis 1:
[0 2 0]
```

## numpy.nonzero()

La fonction ```numpy.nonzero()``` retourne les indices des éléments non nuls dans le tableau d'entrée.

### Exemple

```python
import numpy as np 
a = np.array([[30,40,0],[0,20,10],[50,0,60]]) 

print 'Our array is:' 
print a 
print '\n'  

print 'Applying nonzero() function:' 
print np.nonzero (a)
```

Il produira le résultat suivant -

```python
Our array is:
[
    [30 40 0]
    [ 0 20 10]
    [50 0 60]
]

Applying nonzero() function:
(array([0, 0, 1, 1, 2, 2]), array([0, 1, 1, 2, 0, 2]))
```

## numpy.where()

La fonction ```where()``` renvoie les indices des éléments d'un tableau d'entrée pour lesquels la condition donnée est satisfaite.

### Exemple

```python
import numpy as np 
x = np.arange(9.).reshape(3, 3) 

print 'Our array is:' 
print x  

print 'Indices of elements > 3' 
y = np.where(x > 3) 
print y  

print 'Use these indices to get elements satisfying the condition' 
print x[y]
```

Il produira le résultat suivant -

```python
Our array is:
[
    [ 0. 1. 2.]
    [ 3. 4. 5.]
    [ 6. 7. 8.]
]

Indices of elements > 3
(array([1, 1, 2, 2, 2]), array([1, 2, 0, 1, 2]))

Use these indices to get elements satisfying the condition
[ 4. 5. 6. 7. 8.]
```

## numpy.extract()

La fonction ```extract()``` renvoie les éléments qui satisfont à une condition quelconque.

```python
import numpy as np 
x = np.arange(9.).reshape(3, 3) 

print 'Our array is:' 
print x  

# define a condition 
condition = np.mod(x,2) == 0 

print 'Element-wise value of condition' 
print condition  

print 'Extract elements using condition' 
print np.extract(condition, x)
```

Il produira le résultat suivant -

```python
Our array is:
[
    [ 0. 1. 2.]
    [ 3. 4. 5.]
    [ 6. 7. 8.]
]

Element-wise value of condition
[
    [ True False True]
    [False True False]
    [ True False True]
]

Extract elements using condition
[ 0. 2. 4. 6. 8.]
```