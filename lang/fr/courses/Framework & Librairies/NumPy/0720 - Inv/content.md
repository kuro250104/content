## Introduction

Nous utilisons la fonction ```numpy.linalg.inv()``` pour calculer l'inverse d'une matrice. L'inverse d'une matrice est tel que si elle est multipliée par la matrice originale, il en résulte une matrice d'identité.

### Exemple

```python
import numpy as np 

x = np.array([[1,2],[3,4]]) 
y = np.linalg.inv(x) 
print x 
print y 
print np.dot(x,y)
```

Il devrait produire le résultat suivant -

```python
[
    [1 2]
    [3 4]
]
[
    [-2.   1. ]
    [ 1.5 -0.5]
]
[
    [  1.00000000e+00   1.11022302e-16]
    [  0.00000000e+00   1.00000000e+00]
]
```

### Exemple

Créons maintenant l'inverse de la matrice A de notre exemple.

```python
import numpy as np 
a = np.array([[1,1,1],[0,2,5],[2,5,-1]]) 

print 'Array a:" 
print a 
ainv = np.linalg.inv(a) 

print 'Inverse of a:' 
print ainv  

print 'Matrix B is:' 
b = np.array([[6],[-4],[27]]) 
print b 

print 'Compute A-1B:' 
x = np.linalg.solve(a,b) 
print x  
# this is the solution to linear equations x = 5, y = 3, z = -2
```

Il produira le résultat suivant -

```python
Array a:
[
    [ 1 1 1]
    [ 0 2 5]
    [ 2 5 -1]
]

Inverse of a:
[
    [ 1.28571429 -0.28571429 -0.14285714]
    [-0.47619048 0.14285714 0.23809524]
    [ 0.19047619 0.14285714 -0.0952381 ]
]

Matrix B is:
[
    [ 6]
    [-4]
    [27]
]

Compute A-1B:
[
    [ 5.]
    [ 3.]
    [-2.]
]
```

Le même résultat peut être obtenu en utilisant la fonction -

```python
x = np.dot(ainv,b)
```