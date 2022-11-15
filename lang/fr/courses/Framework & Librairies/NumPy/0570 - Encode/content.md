## Introduction

Cette fonction appelle la fonction str.encode pour chaque élément du tableau. L'encodage par défaut est utf_8, les codecs disponibles dans la bibliothèque Python standard peuvent être utilisés.

```python
import numpy as np 
a = np.char.encode('hello', 'cp500') 
print a
```

Sa sortie est la suivante -

```python
'''''
```