## Introduction

Cette fonction appelle numpy.char.decode() décode la chaîne donnée en utilisant le codec spécifié.

```python
import numpy as np 

a = np.char.encode('hello', 'cp500') 
print a 
print np.char.decode(a,'cp500')
```

Sa sortie est la suivante -

```python
'''''
hello
```