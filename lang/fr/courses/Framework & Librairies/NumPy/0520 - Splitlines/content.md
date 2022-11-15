## Introduction

Cette fonction renvoie une liste d'éléments dans le tableau, avec une rupture aux limites de la ligne.

```python
import numpy as np 
print np.char.splitlines('hello\nhow are you?') 
print np.char.splitlines('hello\rhow are you?')
```

Sa sortie est la suivante -

```python
['hello', 'how are you?']
['hello', 'how are you?']
```

```\n```, ```\r```, ```\r\n``` peuvent être utilisés comme limites de lignes.