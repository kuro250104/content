## Introduction

L'opération ET bit à bit sur les bits correspondants des représentations binaires des entiers dans les tableaux d'entrée est calculée par la fonction np.bitwise_and().

### Exemple

```python
import numpy as np 
print 'Binary equivalents of 13 and 17:' 
a,b = 13,17 
print bin(a), bin(b) 
print '\n'  

print 'Bitwise AND of 13 and 17:' 
print np.bitwise_and(13, 17)
```

Sa sortie est la suivante -

```python
Binary equivalents of 13 and 17:
0b1101 0b10001

Bitwise AND of 13 and 17:
1
```

Vous pouvez vérifier la sortie comme suit. Considérons la table de vérité bitwise_and suivante.

| **A** | **B** | **AND** |
| --- | --- | --- |
| 1 | 1 | 1 |
| 1 | 0 | 0 |
| 0 | 1 | 0 |
| 0 | 0 | 0 |