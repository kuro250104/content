## Introduction

Lors de l'exécution des fonctions, certaines d'entre elles renvoient une copie du tableau d'entrée, tandis que d'autres renvoient la vue. Lorsque le contenu est physiquement stocké à un autre endroit, on parle de **copie**. Si, par contre, une vue différente du même contenu de la mémoire est fournie, on l'appelle **View**.

## No Copy

Les affectations simples ne font pas de copie de l'objet tableau. Au lieu de cela, elles utilisent le même **id()** du tableau original pour y accéder. L'**id()** renvoie un identifiant universel de l'objet Python, similaire au pointeur en C.

En outre, tout changement dans l'un se reflète dans l'autre. Par exemple, le changement de forme de l'un modifiera également la forme de l'autre.

### Exemple

```python
import numpy as np 
a = np.arange(6) 

print 'Our array is:' 
print a  

print 'Applying id() function:' 
print id(a)  

print 'a is assigned to b:' 
b = a 
print b  

print 'b has same id():' 
print id(b)  

print 'Change shape of b:' 
b.shape = 3,2 
print b  

print 'Shape of a also gets changed:' 
print a
```

Il produira le résultat suivant -

```python
Our array is:
[0 1 2 3 4 5]

Applying id() function:
139747815479536

a is assigned to b:
[0 1 2 3 4 5]
b has same id():
139747815479536

Change shape of b:
[
    [0 1]
    [2 3]
    [4 5]
]

Shape of a also gets changed:
[
    [0 1]
    [2 3]
    [4 5]
]
```

## View ou Shallow Copy

NumPy dispose de la méthode ```ndarray.view()``` qui permet d'obtenir un nouvel objet tableau qui regarde les mêmes données que le tableau original. Contrairement au cas précédent, le changement de dimensions du nouveau tableau ne change pas les dimensions de l'original.

### Exemple

```python
import numpy as np 
# To begin with, a is 3X2 array 
a = np.arange(6).reshape(3,2) 

print 'Array a:' 
print a  

print 'Create view of a:' 
b = a.view() 
print b  

print 'id() for both the arrays are different:' 
print 'id() of a:'
print id(a)  
print 'id() of b:' 
print id(b)  

# Change the shape of b. It does not change the shape of a 
b.shape = 2,3 

print 'Shape of b:' 
print b  

print 'Shape of a:' 
print a
```

Il produira le résultat suivant -

```python
Array a:
[
    [0 1]
    [2 3]
    [4 5]
]

Create view of a:
[
    [0 1]
    [2 3]
    [4 5]
]

id() for both the arrays are different:
id() of a:
140424307227264
id() of b:
140424151696288

Shape of b:
[
    [0 1 2]
    [3 4 5]
]

Shape of a:
[
    [0 1]
    [2 3]
    [4 5]
]
```

La tranche d'un tableau crée une vue.

### Exemple

```python
import numpy as np 
a = np.array([[10,10], [2,3], [4,5]]) 

print 'Our array is:' 
print a  

print 'Create a slice:' 
s = a[:, :2] 
print s
```

Il produira le résultat suivant -

```python
Our array is:
[
    [10 10]
    [ 2 3]
    [ 4 5]
]

Create a slice:
[
    [10 10]
    [ 2 3]
    [ 4 5]
]
```

## Deep Copy

La fonction ```ndarray.copy()``` crée une copie profonde. Il s'agit d'une copie complète du tableau et de ses données, qui n'est pas partagée avec le tableau original.

### Exemple

```python
import numpy as np 
a = np.array([[10,10], [2,3], [4,5]]) 

print 'Array a is:' 
print a  

print 'Create a deep copy of a:' 
b = a.copy() 
print 'Array b is:' 
print b 

#b does not share any memory of a 
print 'Can we write b is a' 
print b is a  

print 'Change the contents of b:' 
b[0,0] = 100 

print 'Modified array b:' 
print b  

print 'a remains unchanged:' 
print a
```

Il produira le résultat suivant -

```python

Array a is:
[
    [10 10]
    [ 2 3]
    [ 4 5]
]

Create a deep copy of a:
Array b is:
[
    [10 10]
    [ 2 3]
    [ 4 5]
]
Can we write b is a
False

Change the contents of b:
Modified array b:
[
    [100 10]
    [ 2 3]
    [ 4 5]
]

a remains unchanged:
[
    [10 10]
    [ 2 3]
    [ 4 5]
]
```