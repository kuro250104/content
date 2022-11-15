## Introduction

Cette fonction renvoie une copie du tableau dont les éléments sont dépouillés des caractères spécifiés en tête et/ou en queue de tableau.

```python
import numpy as np 
print np.char.strip('ashok arora','a') 
print np.char.strip(['arora','admin','java'],'a')
```

Voici son résultat -

```python
shok aror
['ror' 'dmin' 'jav']
```