## Introduction

Cette méthode renvoie une chaîne de caractères dans laquelle les caractères individuels sont joints par le caractère séparateur spécifié.

```python
import numpy as np 
print np.char.join(':','dmy') 
print np.char.join([':','-'],['dmy','ymd'])
```

Sa sortie est la suivante -

```python
d:m:y
['d:m:y' 'y-m-d']
```