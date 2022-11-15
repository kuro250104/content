## Introduction

Cette fonction renvoie un tableau unidimensionnel aplati. Une copie n'est faite que si nécessaire. Le tableau retourné aura le même type que celui du tableau d'entrée. La fonction prend un paramètre.

```python
numpy.ravel(a, order)
```

Le constructeur prend les paramètres suivants.

**Paramètre et description**

- **order** - C' : ordre principal des lignes (par défaut) F' : colonne principale 'A' : aplatir dans l'ordre de la colonne principale, si a est contigu dans la mémoire Fortran, dans l'ordre de la ligne principale sinon 'K' : aplatir a dans l'ordre des éléments dans la mémoire

### Exemple

```python
import numpy as np 
a = np.arange(8).reshape(2,4) 

print 'The original array is:' 
print a 
print '\n'  

print 'After applying ravel function:' 
print a.ravel()  
print '\n' 

print 'Applying ravel function in F-style ordering:' 
print a.ravel(order = 'F')
```

Sa sortie serait la suivante -

```python
The original array is:
[
    [0 1 2 3]
    [4 5 6 7]
]

After applying ravel function:
[0 1 2 3 4 5 6 7]

Applying ravel function in F-style ordering:
[0 4 1 5 2 6 3 7]
```