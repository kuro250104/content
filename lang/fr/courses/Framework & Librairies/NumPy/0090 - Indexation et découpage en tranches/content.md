## Introduction

Le contenu de l'objet ndarray peut être accédé et modifié par indexation ou découpage, tout comme les objets conteneurs intégrés de Python.

Comme mentionné précédemment, les éléments de l'objet ndarray suivent un index basé sur zéro. Trois types de méthodes d'indexation sont disponibles : l'accès aux champs, le découpage de base et l'indexation avancée.

Le découpage de base est une extension du concept de base de Python de découpage à n dimensions. Un objet Python slice est construit en donnant les paramètres start, stop, et step à la fonction slice intégrée. Cet objet slice est passé au tableau pour extraire une partie du tableau.

### Exemple 1

```python
import numpy as np 
a = np.arange(10) 
s = slice(2,7,2) 
print a[s]
```

Sa sortie est la suivante -

```python
[2  4  6]
```

Dans l'exemple ci-dessus, un objet ndarray est préparé par la fonction arange(). Ensuite, un objet slice est défini avec les valeurs start, stop, et step 2, 7, et 2 respectivement. Lorsque cet objet slice est transmis à l'objet ndarray, une partie de celui-ci, de l'indice 2 à l'indice 7, avec un pas de 2, est découpée en tranches.

Le même résultat peut également être obtenu en donnant les paramètres de découpage séparés par deux points : (start:stop:step) directement à l'objet ndarray.

### Exemple 2

```python
import numpy as np 
a = np.arange(10) 
b = a[2:7:2] 
print b
```

Ici, nous obtiendrons le même résultat -

```python
[2  4  6]
```

Si un seul paramètre est mis, un seul élément correspondant à l'index sera retourné. Si un : est inséré devant, tous les éléments à partir de cet index seront extraits. Si deux paramètres (avec un : entre eux) sont utilisés, les éléments situés entre les deux index (sans inclure l'index d'arrêt) avec le pas par défaut un sont découpés en tranches.

### Exemple 3

```python
# slice single item 
import numpy as np 

a = np.arange(10) 
b = a[5] 
print b
```

Sa sortie est la suivante -

```python
5
```

### Exemple 4

```python
# slice items starting from index 
import numpy as np 
a = np.arange(10) 
print a[2:]
```

Maintenant, la sortie serait -

```python
[2  3  4  5  6  7  8  9]
```

### Exemple 5

```python
# slice items between indexes 
import numpy as np 
a = np.arange(10) 
print a[2:5]
```

Ici, la sortie serait -

```python
[2  3  4] 
```

La description ci-dessus s'applique également aux ndarray multidimensionnels.

### Exemple 6

```python
import numpy as np 
a = np.array([[1,2,3],[3,4,5],[4,5,6]]) 
print a  

# slice items starting from index
print 'Now we will slice the array from the index a[1:]' 
print a[1:]
```

Le résultat est le suivant -

```python
[
    [1 2 3]
    [3 4 5]
    [4 5 6]
]
```

Now we will slice the array from the index a[1:]

```python
[
    [3 4 5]
    [4 5 6]
]
```

Le découpage peut également inclure des points de suspension (...) pour créer un tuple de sélection de la même longueur que la dimension d'un tableau. Si l'ellipse est utilisée à la position de la ligne, elle retournera un ndarray comprenant les éléments des lignes.

### Exemple 7

```python
# array to begin with 
import numpy as np 
a = np.array([[1,2,3],[3,4,5],[4,5,6]]) 

print 'Our array is:' 
print a 
print '\n'  

# this returns array of items in the second column 
print 'The items in the second column are:'  
print a[...,1] 
print '\n'  

# Now we will slice all items from the second row 
print 'The items in the second row are:' 
print a[1,...] 
print '\n'  

# Now we will slice all items from column 1 onwards 
print 'The items column 1 onwards are:' 
print a[...,1:]
```

La sortie de ce programme est la suivante -

```python
Our array is:
[
    [1 2 3]
    [3 4 5]
    [4 5 6]
] 

The items in the second column are: 
[2 4 5] 

The items in the second row are:
[3 4 5]

The items column 1 onwards are:
[
    [2 3]
    [4 5]
    [5 6]
]
```