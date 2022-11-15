## Introduction

Dans ce cours, nous allons voir comment créer un tableau à partir de plages numériques.

## numpy.arange

Cette fonction renvoie un objet ndarray contenant des valeurs uniformément espacées dans une plage donnée. Le format de la fonction est le suivant -

```python
numpy.arange(start, stop, step, dtype)
```

Le constructeur prend les paramètres suivants.

**Paramètre et description**

- **start** - Le début d'un intervalle. Si omis, la valeur par défaut est 0
- **stop** - La fin d'un intervalle (n'incluant pas ce nombre)
- **step** - Espacement entre les valeurs, par défaut 1
- **dtype** - Type de données du ndarray résultant. S'il n'est pas donné, le type de données de l'entrée est utilisé.

Les exemples suivants montrent comment vous pouvez utiliser cette fonction.

### Exemple 1

```python
import numpy as np 
x = np.arange(5) 
print x
```

Its output would be as follows −

```python
[0  1  2  3  4]
```

### Exemple 2

```python
import numpy as np 
# dtype set 
x = np.arange(5, dtype = float)
print x
```

Here, the output would be −

```python
[0.  1.  2.  3.  4.] 
```

### Exemple 3

```python
# start and stop parameters set 
import numpy as np 
x = np.arange(10,20,2) 
print x
```

Sa sortie est la suivante -

```python
[10  12  14  16  18] 
```

## numpy.linspace

Cette fonction est similaire à la fonction ```arange()```. Dans cette fonction, au lieu de la taille du pas, on spécifie le nombre de valeurs régulièrement espacées entre les intervalles. L'utilisation de cette fonction est la suivante -

```python
numpy.linspace(start, stop, num, endpoint, retstep, dtype)
```

Le constructeur prend les paramètres suivants.

**Paramètre et description**

- **start** - La valeur de départ de la séquence
- **stop** - La valeur finale de la séquence, incluse dans la séquence si le point final est défini comme vrai.
- **num** - Le nombre d'échantillons uniformément espacés à générer. La valeur par défaut est 50
- **endpoint** - Vrai par défaut, donc la valeur d'arrêt est incluse dans la séquence. Si false, elle n'est pas incluse
- **retstep** - Si vrai, renvoie les échantillons et le pas entre les numéros consécutifs.
- **dtype** - Type de données de la sortie ndarray

Les exemples suivants démontrent l'utilisation de la fonction linspace.

### Exemple 1

```python
00import numpy as np 
x = np.linspace(10,20,5) 
print x
```

Sa sortie serait -

```python
[10.   12.5   15.   17.5  20.]
```

Exemple 2

```python
# endpoint set to false 
import numpy as np 
x = np.linspace(10,20, 5, endpoint = False) 
print x
```

La sortie serait -

```python
[10.   12.   14.   16.   18.]
```

### Exemple 3

```python
# find retstep value 
import numpy as np 

x = np.linspace(1,2,5, retstep = True) 
print x 
# retstep here is 0.25
```

Maintenant, la sortie serait -

```python
(array([ 1.  ,  1.25,  1.5 ,  1.75,  2.  ]), 0.25)
```

## numpy.logspace

Cette fonction renvoie un objet ndarray qui contient les nombres qui sont uniformément espacés sur une échelle logarithmique. Les points de départ et d'arrivée de l'échelle sont des indices de la base, généralement 10.

```python
numpy.logspace(start, stop, num, endpoint, base, dtype)
```

Les paramètres suivants déterminent la sortie de la fonction **logspace**.

**Paramètre et description**

- **start** - Le point de départ de la séquence est basestart
- **stop** - La valeur finale de la séquence est basestop
- **num** - Le nombre de valeurs comprises dans l'intervalle. La valeur par défaut est 50
- **endpoint** - Si c'est vrai, stop est la dernière valeur de la plage.
- **base** - Base d'espace pour le journal, par défaut 10
- **dtype** - Type de données du tableau de sortie. S'il n'est pas donné, il dépend des autres arguments d'entrée.

Les exemples suivants vous aideront à comprendre la fonction **logspace**.

### Exemple 1

```python
import numpy as np 
# default base is 10 
a = np.logspace(1.0, 2.0, num = 10) 
print a
```

Sa sortie serait la suivante -

```python
[ 10.           12.91549665     16.68100537      21.5443469  27.82559402      
  35.93813664   46.41588834     59.94842503      77.42636827    100.    ]
```

### Exemple 2

```python
# set base of log space to 2 
import numpy as np 
a = np.logspace(1,10,num = 10, base = 2) 
print a
```

Maintenant, la sortie serait -

```python
[ 2.     4.     8.    16.    32.    64.   128.   256.    512.   1024.]
```