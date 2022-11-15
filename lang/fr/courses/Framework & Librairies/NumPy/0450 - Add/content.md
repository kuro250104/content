## Introduction

Cette fonction effectue une concaténation de chaînes de caractères par éléments.

```python
import numpy as np 
print 'Concatenate two strings:' 
print np.char.add(['hello'],[' xyz']) 
print '\n'

print 'Concatenation example:' 
print np.char.add(['hello', 'hi'],[' abc', ' xyz'])
```

Sa sortie serait la suivante -

```python
Concatenate two strings:
['hello xyz']

Concatenation example:
['hello abc' 'hi xyz']
```