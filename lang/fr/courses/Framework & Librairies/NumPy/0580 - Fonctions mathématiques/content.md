## Introduction

De manière assez compréhensible, NumPy contient un grand nombre d'opérations mathématiques diverses. NumPy fournit des fonctions trigonométriques standard, des fonctions pour les opérations arithmétiques, la manipulation de nombres complexes, etc.

## Fonctions trigonométriques

NumPy possède des fonctions trigonométriques standard qui renvoient des rapports trigonométriques pour un angle donné en radians.

### Exemple

```python
import numpy as np 
a = np.array([0,30,45,60,90]) 

print 'Sine of different angles:' 
# Convert to radians by multiplying with pi/180 
print np.sin(a*np.pi/180) 
print '\n'  

print 'Cosine values for angles in array:' 
print np.cos(a*np.pi/180) 
print '\n'  

print 'Tangent values for given angles:' 
print np.tan(a*np.pi/180)
```

Voici son résultat -

```python
Sine of different angles:
[ 0.          0.5         0.70710678  0.8660254   1.        ]

Cosine values for angles in array:
[  1.00000000e+00   8.66025404e-01   7.07106781e-01   5.00000000e-01
   6.12323400e-17]                                                            

Tangent values for given angles:
[  0.00000000e+00   5.77350269e-01   1.00000000e+00   1.73205081e+00
   1.63312394e+16]
```

Les fonctions **arcsin**, **arcos**, et **arctan** retournent l'inverse trigonométrique de sin, cos, et tan de l'angle donné. Le résultat de ces fonctions peut être vérifié par la fonction ```numpy.degrees()``` en convertissant les radians en degrés.

### Exemple

```python
import numpy as np 
a = np.array([0,30,45,60,90]) 

print 'Array containing sine values:' 
sin = np.sin(a*np.pi/180) 
print sin 
print '\n'  

print 'Compute sine inverse of angles. Returned values are in radians.' 
inv = np.arcsin(sin) 
print inv 
print '\n'  

print 'Check result by converting to degrees:' 
print np.degrees(inv) 
print '\n'  

print 'arccos and arctan functions behave similarly:' 
cos = np.cos(a*np.pi/180) 
print cos 
print '\n'  

print 'Inverse of cos:' 
inv = np.arccos(cos) 
print inv 
print '\n'  

print 'In degrees:' 
print np.degrees(inv) 
print '\n'  

print 'Tan function:' 
tan = np.tan(a*np.pi/180) 
print tan
print '\n'  

print 'Inverse of tan:' 
inv = np.arctan(tan) 
print inv 
print '\n'  

print 'In degrees:' 
print np.degrees(inv)
```

Il produit le résultat suivant -

```python
Array containing sine values:
[ 0.          0.5         0.70710678  0.8660254   1.        ]

Compute sine inverse of angles. Returned values are in radians.
[ 0.          0.52359878  0.78539816  1.04719755  1.57079633] 

Check result by converting to degrees:
[  0.  30.  45.  60.  90.]

arccos and arctan functions behave similarly:
[  1.00000000e+00   8.66025404e-01   7.07106781e-01   5.00000000e-01          
   6.12323400e-17] 

Inverse of cos:
[ 0.          0.52359878  0.78539816  1.04719755  1.57079633] 

In degrees:
[  0.  30.  45.  60.  90.] 

Tan function:
[  0.00000000e+00   5.77350269e-01   1.00000000e+00   1.73205081e+00          
   1.63312394e+16]

Inverse of tan:
[ 0.          0.52359878  0.78539816  1.04719755  1.57079633]

In degrees:
[  0.  30.  45.  60.  90.]
```

## Fonctions d'arrondi

### numpy.around()

Il s'agit d'une fonction qui renvoie la valeur arrondie à la précision souhaitée. La fonction prend les paramètres suivants.

```python
numpy.around(a,decimals)
```

Où,

**Paramètre et description**

- **a** - Données d'entrée
- **decimals** - Le nombre de décimales à arrondir. La valeur par défaut est 0. Si elle est négative, le nombre entier est arrondi à la position située à gauche du point décimal.

#### Exemple

```python
import numpy as np 
a = np.array([1.0,5.55, 123, 0.567, 25.532]) 

print 'Original array:' 
print a 
print '\n'  

print 'After rounding:' 
print np.around(a) 
print np.around(a, decimals = 1) 
print np.around(a, decimals = -1)
```

Il produit le résultat suivant -

```python
Original array:                                                               
[   1.       5.55   123.       0.567   25.532] 

After rounding:                                                               
[   1.    6.   123.    1.   26. ]                                               
[   1.    5.6  123.    0.6  25.5]                                          
[   0.    10.  120.    0.   30. ]
```

### numpy.floor()

Cette fonction renvoie le plus grand entier non supérieur au paramètre d'entrée. Le plancher du scalaire x est le plus grand entier i, tel que i <= x. Notez qu'en Python, le plancher est toujours arrondi à l'écart de 0.

#### Example

```python
import numpy as np 
a = np.array([-1.7, 1.5, -0.2, 0.6, 10]) 

print 'The given array:' 
print a 
print '\n'  

print 'The modified array:' 
print np.floor(a)
```

Il produit le résultat suivant -

```python
The given array:                                                              
[ -1.7   1.5  -0.2   0.6  10. ]

The modified array:                                                           
[ -2.   1.  -1.   0.  10.]
```

### numpy.ceil()

La fonction ```ceil()``` renvoie le plafond d'une valeur d'entrée, c'est-à-dire que le plafond du scalaire x est le plus petit entier i, tel que i >= x.

#### Exemple

```python
import numpy as np 
a = np.array([-1.7, 1.5, -0.2, 0.6, 10]) 

print 'The given array:' 
print a 
print '\n'  

print 'The modified array:' 
print np.ceil(a)
```

Il produira le résultat suivant -

```python
The given array:                                                              
[ -1.7   1.5  -0.2   0.6  10. ]

The modified array:                                                           
[ -1.   2.  -0.   1.  10.]
```