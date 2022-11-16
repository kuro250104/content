## Introduction

NumPy dispose de plusieurs fonctions statistiques utiles pour trouver le minimum, le maximum, l'écart-type du centile et la variance, etc. à partir des éléments donnés dans le tableau. Les fonctions sont expliquées comme suit -

## numpy.amin() and numpy.amax()

Ces fonctions renvoient le minimum et le maximum des éléments du tableau donné le long de l'axe spécifié.

### Exemple

```python
import numpy as np 
a = np.array([[3,7,5],[8,4,3],[2,4,9]]) 

print 'Our array is:' 
print a  
print '\n'  

print 'Applying amin() function:' 
print np.amin(a,1) 
print '\n'  

print 'Applying amin() function again:' 
print np.amin(a,0) 
print '\n'  

print 'Applying amax() function:' 
print np.amax(a) 
print '\n'  

print 'Applying amax() function again:' 
print np.amax(a, axis = 0)
```

Il produira le résultat suivant -

```python
Our array is:
[
    [3 7 5]
    [8 4 3]
    [2 4 9]
]

Applying amin() function:
[3 3 2]

Applying amin() function again:
[2 4 3]

Applying amax() function:
9

Applying amax() function again:
[8 7 9]
```

## numpy.ptp()

La fonction ```numpy.ptp()``` renvoie la plage (maximum-minimum) des valeurs le long d'un axe.

### Exemple

```python
import numpy as np 
a = np.array([[3,7,5],[8,4,3],[2,4,9]]) 

print 'Our array is:' 
print a 
print '\n'  

print 'Applying ptp() function:' 
print np.ptp(a) 
print '\n'  

print 'Applying ptp() function along axis 1:' 
print np.ptp(a, axis = 1) 
print '\n'   

print 'Applying ptp() function along axis 0:'
print np.ptp(a, axis = 0)
```

Il produira le résultat suivant -

```python
Our array is:
[
    [3 7 5]
    [8 4 3]
    [2 4 9]
]

Applying ptp() function:
7

Applying ptp() function along axis 1:
[4 5 7]

Applying ptp() function along axis 0:
[6 3 6]
```

## numpy.percentile()

Le percentile (ou un centile) est une mesure utilisée en statistiques indiquant la valeur en dessous de laquelle un pourcentage donné d'observations dans un groupe d'observations tombe. La fonction numpy.percentile() prend les arguments suivants.

```python
numpy.percentile(a, q, axis)
```

Où,

**Argument et description**

- **a** - Tableau d'entrée
- **q** - Le percentile à calculer doit être compris entre 0 et 100.
- **axis** - L'axe le long duquel le percentile doit être calculé.

### Exemple

```python
import numpy as np 
a = np.array([[30,40,70],[80,20,10],[50,90,60]]) 

print 'Our array is:' 
print a 
print '\n'  

print 'Applying percentile() function:' 
print np.percentile(a,50) 
print '\n'  

print 'Applying percentile() function along axis 1:' 
print np.percentile(a,50, axis = 1) 
print '\n'  

print 'Applying percentile() function along axis 0:' 
print np.percentile(a,50, axis = 0)
```

Il produira le résultat suivant -

```python
Our array is:
[
    [30 40 70]
    [80 20 10]
    [50 90 60]
]

Applying percentile() function:
50.0

Applying percentile() function along axis 1:
[ 40. 20. 60.]

Applying percentile() function along axis 0:
[ 50. 40. 60.]
```

## numpy.median()

La médiane est définie comme la valeur séparant la moitié supérieure d'un échantillon de données de la moitié inférieure. La fonction ```numpy.median()``` est utilisée comme indiqué dans le programme suivant.

### Exemple

```python
import numpy as np 
a = np.array([[30,65,70],[80,95,10],[50,90,60]]) 

print 'Our array is:' 
print a 
print '\n'  

print 'Applying median() function:' 
print np.median(a) 
print '\n'  

print 'Applying median() function along axis 0:' 
print np.median(a, axis = 0) 
print '\n'  

print 'Applying median() function along axis 1:' 
print np.median(a, axis = 1)
```

Il produira le résultat suivant -

```python
Our array is:
[
    [30 65 70]
    [80 95 10]
    [50 90 60]
]

Applying median() function:
65.0

Applying median() function along axis 0:
[ 50. 90. 60.]

Applying median() function along axis 1:
[ 65. 80. 60.]
```

## numpy.mean()

La moyenne arithmétique est la somme des éléments le long d'un axe divisée par le nombre d'éléments. La fonction ```numpy.mean()``` renvoie la moyenne arithmétique des éléments du tableau. Si l'axe est mentionné, elle est calculée le long de celui-ci.

### Exemple

```python
import numpy as np 
a = np.array([[1,2,3],[3,4,5],[4,5,6]]) 

print 'Our array is:' 
print a 
print '\n'  

print 'Applying mean() function:' 
print np.mean(a) 
print '\n'  

print 'Applying mean() function along axis 0:' 
print np.mean(a, axis = 0) 
print '\n'  

print 'Applying mean() function along axis 1:' 
print np.mean(a, axis = 1)
```

Il produira le résultat suivant -

```python
Our array is:
[
    [1 2 3]
    [3 4 5]
    [4 5 6]
]

Applying mean() function:
3.66666666667

Applying mean() function along axis 0:
[ 2.66666667 3.66666667 4.66666667]

Applying mean() function along axis 1:
[ 2. 4. 5.]
```

## numpy.average()

La moyenne pondérée est une moyenne résultant de la multiplication de chaque élément par un facteur reflétant son importance. La fonction numpy.average() calcule la moyenne pondérée des éléments d'un tableau en fonction de leur poids respectif donné dans un autre tableau. La fonction peut avoir un paramètre d'axe. Si l'axe n'est pas spécifié, le tableau est aplati.

En considérant un tableau [1,2,3,4] et les poids correspondants [4,3,2,1], la moyenne pondérée est calculée en ajoutant le produit des éléments correspondants et en divisant la somme par la somme des poids.

Moyenne pondérée = (1*4+2*3+3*2+4*1)/(4+3+2+1)

### Exemple

```python
import numpy as np 
a = np.array([1,2,3,4]) 

print 'Our array is:' 
print a 
print '\n'  

print 'Applying average() function:' 
print np.average(a) 
print '\n'  

# this is same as mean when weight is not specified 
wts = np.array([4,3,2,1]) 

print 'Applying average() function again:' 
print np.average(a,weights = wts) 
print '\n'  

# Returns the sum of weights, if the returned parameter is set to True. 
print 'Sum of weights' 
print np.average([1,2,3, 4],weights = [4,3,2,1], returned = True)
```

Il produira le résultat suivant -

```python
Our array is:
[1 2 3 4]

Applying average() function:
2.5

Applying average() function again:
2.0

Sum of weights
(2.0, 10.0)
```

Dans un tableau multidimensionnel, l'axe de calcul peut être spécifié.

### Exemple

```python
import numpy as np 
a = np.arange(6).reshape(3,2) 

print 'Our array is:' 
print a 
print '\n'  

print 'Modified array:' 
wt = np.array([3,5]) 
print np.average(a, axis = 1, weights = wt) 
print '\n'  

print 'Modified array:' 
print np.average(a, axis = 1, weights = wt, returned = True)
```

Il produira le résultat suivant -

```python
Our array is:
[
    [0 1]
    [2 3]
    [4 5]
]

Modified array:
[ 0.625 2.625 4.625]

Modified array:
(array([ 0.625, 2.625, 4.625]), array([ 8., 8., 8.]))
```

## Écart-type

L'écart-type est la racine carrée de la moyenne des écarts au carré par rapport à la moyenne. La formule de l'écart-type est la suivante : - 1.

```python
std = sqrt(mean(abs(x - x.mean())**2))
```

Si le tableau est [1, 2, 3, 4], alors sa moyenne est 2,5. Par conséquent, les écarts au carré sont [2,25, 0,25, 0,25, 2,25] et la racine carrée de sa moyenne divisée par 4, c'est-à-dire sqrt (5/4), est 1,1180339887498949.

### Exemple

```python
import numpy as np 
print np.std([1,2,3,4])
```

Il produira le résultat suivant -

```python
1.1180339887498949 
```

## Variance

La variance est la moyenne des écarts au carré, c'est-à-dire mean(abs(x - x.mean())**2). En d'autres termes, l'écart-type est la racine carrée de la variance.

### Exemple

```python
import numpy as np 
print np.var([1,2,3,4])
```

Il produira le résultat suivant -

```python
1.25
```