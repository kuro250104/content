## Introduction

La fonction ```numpy.left_shift()``` déplace les bits dans la représentation binaire d'un élément de tableau vers la gauche par des positions spécifiées. Un nombre égal de 0 est ajouté à partir de la droite.

Par exemple,

```python
import numpy as np 

print 'Left shift of 10 by two positions:' 
print np.left_shift(10,2) 
print '\n'  

print 'Binary representation of 10:' 
print np.binary_repr(10, width = 8) 
print '\n'  

print 'Binary representation of 40:' 
print np.binary_repr(40, width = 8)  
# Two bits in '00001010' are shifted to left and two 0s appended from right.
```

Sa sortie est la suivante -

```python
Left shift of 10 by two positions:
40

Binary representation of 10:
00001010

Binary representation of 40:
00101000
```