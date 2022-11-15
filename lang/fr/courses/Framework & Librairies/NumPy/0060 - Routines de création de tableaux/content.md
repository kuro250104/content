## Introduction

Un nouvel objet ndarray peut être construit par l'une des routines de création de tableau suivantes ou en utilisant un constructeur ndarray de bas niveau.

## numpy.empty

Elle crée un tableau non initialisé de forme et de type d spécifiés. Elle utilise le constructeur suivant -

```python
numpy.empty(shape, dtype = float, order = 'C')
```

Le constructeur prend les paramètres suivants.

**Paramètre et description**

- **Shape** - Forme d'un tableau vide en int ou séquence d'int
- **Dtype** - Type de données de sortie souhaité. Optionnel
- **Order** - C pour un tableau à dominante ligne de style C, F pour un tableau à dominante colonne de style FORTRAN.

### Exemple

Le code suivant montre un exemple de tableau vide.

```python
import numpy as np 
x = np.empty([3,2], dtype = int) 
print x
```

Le résultat est le suivant -

```python
[
    [22649312    1701344351] 
    [1818321759  1885959276] 
    [16779776    156368896]
]
```

__Remarque__ - Les éléments d'un tableau présentent des valeurs aléatoires car ils ne sont pas initialisés.

## numpy.zeros

Renvoie un nouveau tableau de taille spécifiée, rempli de zéros.

```python
numpy.zeros(shape, dtype = float, order = 'C')
```

Le constructeur prend les paramètres suivants.

**Paramètre et description**

- **Shape** - Forme d'un tableau vide en int ou séquence d'int
- **Dtype** - Type de données de sortie souhaité. Optionnel
- **Order** - C pour un tableau à dominante ligne de style C, F pour un tableau à dominante colonne de style FORTRAN.

### Exemple 1

```python
# array of five zeros. Default dtype is float 
import numpy as np 
x = np.zeros(5) 
print x
```

Le résultat est le suivant -

```python
[ 0.  0.  0.  0.  0.]
```

### Exemple 2

```python
import numpy as np 
x = np.zeros((5,), dtype = np.int) 
print x
```

Maintenant, la sortie serait la suivante -

```python
[0  0  0  0  0]
```

### Exemple 3

```python
# custom type 
import numpy as np 
x = np.zeros((2,2), dtype = [('x', 'i4'), ('y', 'i4')])  
print x
```

Il devrait produire le résultat suivant -

```python
[
    [(0,0)(0,0)]
    [(0,0)(0,0)]
]
```

## numpy.ones

Renvoie un nouveau tableau de taille et de type spécifiés, rempli de uns.

```python
numpy.ones(shape, dtype = None, order = 'C')
```

Le constructeur prend les paramètres suivants.

**Paramètre et description**

- **Shape** - Forme d'un tableau vide en int ou tuple d'int
- **Dtype** - Type de données de sortie souhaité. Optionnel
- **Order** - C pour un tableau à dominante ligne de style C, F pour un tableau à dominante colonne de style FORTRAN.

### Exemple 1

```python
# array of five ones. Default dtype is float 
import numpy as np 
x = np.ones(5) 
print x
```

Le résultat est le suivant -

```python
[ 1.  1.  1.  1.  1.]
```

### Exemple 2

```python
import numpy as np 
x = np.ones([2,2], dtype = int) 
print x
```

Maintenant, la sortie serait la suivante -

```python
[
    [1  1] 
    [1  1]
]
```