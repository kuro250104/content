## Introduction

Cette fonction diffuse un tableau vers une nouvelle forme. Elle retourne une vue en lecture seule sur le tableau original. Il n'est généralement pas contigu. La fonction peut lancer ValueError si la nouvelle forme ne respecte pas les règles de diffusion de NumPy. 

__Remarque__ − Cette fonction est disponible à partir de la version 1.10.0.

La fonction prend les paramètres suivants.

```python
numpy.broadcast_to(array, shape, subok)
```

### Exemple

```python
import numpy as np 
a = np.arange(4).reshape(1,4) 

print 'The original array:' 
print a 
print '\n'  

print 'After applying the broadcast_to function:' 
print np.broadcast_to(a,(4,4))
```

Il devrait produire le résultat suivant -

```python
[
    [0  1  2  3] 
    [0  1  2  3] 
    [0  1  2  3] 
    [0  1  2  3]
]
```