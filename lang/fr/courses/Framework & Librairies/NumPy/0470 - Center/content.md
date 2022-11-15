## Introduction

Cette fonction renvoie un tableau de la largeur requise pour que la chaîne d'entrée soit centrée et complétée à gauche et à droite par fillchar.

```python
import numpy as np 
# np.char.center(arr, width,fillchar) 
print np.char.center('hello', 20,fillchar = '*')
```

Voici son résultat -

```python
*******hello********
```