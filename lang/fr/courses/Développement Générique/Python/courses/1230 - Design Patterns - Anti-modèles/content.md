Les anti-modèles suivent une stratégie qui s'oppose aux modèles de conception prédéfinis. Cette stratégie comprend des approches communes à des problèmes communs, qui peuvent être formalisées et être généralement considérées comme une bonne pratique de développement. En général, les anti-modèles sont opposés et indésirables. Les anti-modèles sont certains modèles utilisés dans le développement de logiciels, qui sont considérés comme de mauvaises pratiques de programmation.

## Caractéristiques importantes des anti-modèles

Voyons maintenant quelques caractéristiques importantes des anti-modèles.

### Correctness

Ces modèles cassent littéralement votre code et vous font faire de mauvaises choses. Voici une illustration simple de ce phénomène :

```python
class Rectangle(object):
    def __init__(self, width, height):
        self._width = width
        self._height = height

r = Rectangle(5, 6)
# direct access of protected member
print("Width: {:d}".format(r._width))
```

### Maintenabilité

Un programme est dit maintenable s'il est facile à comprendre et à modifier en fonction des besoins. L'importation d'un module peut être considérée comme un exemple de maintenabilité.

```python
import math
x = math.ceil(y)
# or
import multiprocessing as mp
pool = mp.pool(8)
```

### Exemple d'anti-modèle

L'exemple suivant aide à la démonstration des anti-modèles.

```python
# Mauvais
def filter_for_foo(l):
    r = [e for e in l if e.find("foo") != -1]
    if not check_some_critical_condition(r):
        return None
    return r

res = filter_for_foo(["bar","foo","faz"])

if res is not None:
    #continue processing
    pass

# Bon
def filter_for_foo(l):
    r = [e for e in l if e.find("foo") != -1]
    if not check_some_critical_condition(r):
        raise SomeException("critical condition unmet!")
    return r

try:
    res = filter_for_foo(["bar","foo","faz"])
    #continue processing

except SomeException:
    i = 0
while i < 10:
    do_something()
    #we forget to increment i
```

### Explication

L'exemple comprend la démonstration des bonnes et mauvaises normes pour la création d'une fonction en Python.