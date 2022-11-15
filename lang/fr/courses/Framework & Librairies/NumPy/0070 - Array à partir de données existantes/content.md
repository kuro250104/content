## Introduction

Dans ce cours, nous allons voir comment créer un tableau à partir de données existantes.

## numpy.asarray

Cette fonction est similaire à numpy.array sauf qu'elle a moins de paramètres. Cette routine est utile pour convertir une séquence Python en ndarray.

```python
numpy.asarray(a, dtype = None, order = None)
```

Le constructeur prend les paramètres suivants.

**Paramètre et description**

- **a** - Données d'entrée sous n'importe quelle forme : liste, liste de tuples, tuples, tuple de tuples ou tuple de listes.
- **dtype** - Par défaut, le type de données d'entrée est appliqué au ndarray résultant.
- **order** - C (majeure de ligne) ou F (majeure de colonne). C est la valeur par défaut

Les exemples suivants montrent comment vous pouvez utiliser la fonction **asarray**.

### Exemple 1

```python
# convert list to ndarray 
import numpy as np 

x = [1,2,3] 
a = np.asarray(x) 
print a
```

Sa sortie serait la suivante -

```python
[1  2  3] 
```

### Exemple 2

```python
# dtype is set 
import numpy as np 

x = [1,2,3]
a = np.asarray(x, dtype = float) 
print a
```

Maintenant, la sortie serait la suivante -

```python
[ 1.  2.  3.] 
```

### Exemple 3

```python
# ndarray from tuple 
import numpy as np 

x = (1,2,3) 
a = np.asarray(x) 
print a
```

Sa sortie serait -

```python
[1  2  3]
```

### Exemple 4

```python
# ndarray from list of tuples 
import numpy as np 

x = [(1,2,3),(4,5)] 
a = np.asarray(x) 
print a
```

Ici, la sortie serait la suivante -

```python
[(1, 2, 3) (4, 5)]
```

## numpy.frombuffer

Cette fonction interprète un tampon comme un tableau unidimensionnel. N'importe quel objet qui expose l'interface de tampon est utilisé comme paramètre pour retourner un ndarray.

```python
numpy.frombuffer(buffer, dtype = float, count = -1, offset = 0)
```

Le constructeur prend les paramètres suivants.

**Paramètre et description**

- **buffer** - Tout objet qui expose l'interface du tampon
- **dtype** - Type de données du ndarray retourné. La valeur par défaut est float
- **count** - Le nombre d'éléments à lire, par défaut -1 signifie toutes les données.
- **offset** - La position de départ pour la lecture. La valeur par défaut est 0

### Exemple

Les exemples suivants démontrent l'utilisation de la fonction frombuffer.

```python
import numpy as np 
s = 'Hello World' 
a = np.frombuffer(s, dtype = 'S1') 
print a
```

Voici son résultat -

```python
['H'  'e'  'l'  'l'  'o'  ' '  'W'  'o'  'r'  'l'  'd']
```

## numpy.fromiter

Cette fonction construit un objet ndarray à partir de n'importe quel objet itérable. Un nouveau tableau unidimensionnel est retourné par cette fonction.

```python
numpy.fromiter(iterable, dtype, count = -1)
```

Ici, le constructeur prend les paramètres suivants.

**Paramètre et description**

- **iterable** - Tout objet itérable
- **dtype** - Type de données du tableau de la résultante
- **count** - Le nombre d'éléments à lire de l'itérateur. La valeur par défaut est -1, ce qui signifie que toutes les données doivent être lues.

Les exemples suivants montrent comment utiliser la fonction intégrée ```range()``` pour retourner un objet liste. Un itérateur de cette liste est utilisé pour former un objet **ndarray**.

### Exemple 1

```python
# create list object using range function 
import numpy as np 
list = range(5) 
print list
```

Sa sortie est la suivante -

```python
[0,  1,  2,  3,  4]
```

### Exemple 2

```python
# obtain iterator object from list 
import numpy as np 
list = range(5) 
it = iter(list)  

# use iterator to create ndarray 
x = np.fromiter(it, dtype = float) 
print x
```

Maintenant, la sortie serait la suivante -

```python
[0.   1.   2.   3.   4.]
```