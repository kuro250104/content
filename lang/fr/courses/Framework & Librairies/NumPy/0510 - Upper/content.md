## Introduction

Cette fonction appelle la fonction str.upper sur chaque élément d'un tableau pour retourner les éléments en majuscules du tableau.

```python
import numpy as np 
print np.char.upper('hello') 
print np.char.upper(['hello','world'])
```

Voici son résultat -

```python
HELLO
['HELLO' 'WORLD']
```