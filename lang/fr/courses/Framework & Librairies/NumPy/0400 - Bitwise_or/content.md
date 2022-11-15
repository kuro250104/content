## Introduction

L'opération OR bitwise sur les bits correspondants des représentations binaires des entiers dans les tableaux d'entrée est calculée par la fonction np.bitwise_or().

### Exemple

```python
import numpy as np 
a,b = 13,17 
print 'Binary equivalents of 13 and 17:' 
print bin(a), bin(b)  

print 'Bitwise OR of 13 and 17:' 
print np.bitwise_or(13, 17)
```

Sa sortie est la suivante -

```python
Binary equivalents of 13 and 17:
0b1101 0b10001

Bitwise OR of 13 and 17:
29
```

Vous pouvez vérifier cette sortie à l'aide de la table suivante. Considérons la table de vérité Bitwise_or suivante.

| **A** | **B** | **OR** |
| --- | --- | --- |
| 1 | 1 | 1 |
| 1 | 0 | 1 |
| 0 | 1 | 1 |
| 0 | 0 | 0 |