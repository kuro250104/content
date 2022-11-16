## Introduction

Les tableaux d'entrée pour l'exécution d'opérations arithmétiques telles que ```add()```, ```subtract()```, ```multiply()``` et ```divide()``` doivent être soit de la même forme, soit conformes aux règles de diffusion des tableaux.

### Exemple

```python
import numpy as np 
a = np.arange(9, dtype = np.float_).reshape(3,3) 

print 'First array:' 
print a 
print '\n'  

print 'Second array:' 
b = np.array([10,10,10]) 
print b 
print '\n'  

print 'Add the two arrays:' 
print np.add(a,b) 
print '\n'  

print 'Subtract the two arrays:' 
print np.subtract(a,b) 
print '\n'  

print 'Multiply the two arrays:' 
print np.multiply(a,b) 
print '\n'  

print 'Divide the two arrays:' 
print np.divide(a,b)
```

Il produira le résultat suivant -

```python
First array:
[
    [ 0. 1. 2.]
    [ 3. 4. 5.]
    [ 6. 7. 8.]
]

Second array:
[10 10 10]

Add the two arrays:
[
    [ 10. 11. 12.]
    [ 13. 14. 15.]
    [ 16. 17. 18.]
]

Subtract the two arrays:
[
    [-10. -9. -8.]
    [ -7. -6. -5.]
    [ -4. -3. -2.]
]

Multiply the two arrays:
[
    [ 0. 10. 20.]
    [ 30. 40. 50.]
    [ 60. 70. 80.]
]

Divide the two arrays:
[
    [ 0. 0.1 0.2]
    [ 0.3 0.4 0.5]
    [ 0.6 0.7 0.8]
]
```

Voyons maintenant quelques-unes des autres fonctions arithmétiques importantes disponibles dans NumPy.

## numpy.reciprocal()

Cette fonction renvoie la réciproque de l'argument, par élément. Pour les éléments dont la valeur absolue est supérieure à 1, le résultat est toujours 0 en raison de la façon dont Python gère la division des entiers. Pour le nombre entier 0, un avertissement de dépassement de capacité est émis.

### Exemple

```python
import numpy as np 
a = np.array([0.25, 1.33, 1, 0, 100]) 

print 'Our array is:' 
print a 
print '\n'  

print 'After applying reciprocal function:' 
print np.reciprocal(a) 
print '\n'  

b = np.array([100], dtype = int) 
print 'The second array is:' 
print b 
print '\n'  

print 'After applying reciprocal function:' 
print np.reciprocal(b)
```

Il produira le résultat suivant -

```python
Our array is:
[   0.25    1.33    1.      0.    100.  ]

After applying reciprocal function:

main.py:9: RuntimeWarning: divide by zero encountered in reciprocal
    print np.reciprocal(a)
[ 4.         0.7518797  1.               inf  0.01     ]

The second array is:
[100]

After applying reciprocal function:
[0]
```

## numpy.power()

Cette fonction traite les éléments du premier tableau d'entrée comme base et les renvoie élevés à la puissance de l'élément correspondant dans le deuxième tableau d'entrée.

### Exemple

```python
import numpy as np 
a = np.array([10,100,1000]) 

print 'Our array is:' 
print a 
print '\n'  

print 'Applying power function:' 
print np.power(a,2) 
print '\n'  

print 'Second array:' 
b = np.array([1,2,3]) 
print b 
print '\n'  

print 'Applying power function again:' 
print np.power(a,b)
```

Il produira le résultat suivant -

```python
Our array is:
[  10  100 1000]

Applying power function:
[    100   10000 1000000]

Second array:
[1 2 3]

Applying power function again:
[        10      10000 1000000000]
```

## numpy.mod()

Cette fonction renvoie le reste de la division des éléments correspondants dans le tableau d'entrée. La fonction numpy.remainder() produit également le même résultat.

```python
import numpy as np 
a = np.array([10,20,30]) 
b = np.array([3,5,7]) 

print 'First array:' 
print a 
print '\n'  

print 'Second array:' 
print b 
print '\n'  

print 'Applying mod() function:' 
print np.mod(a,b) 
print '\n'  

print 'Applying remainder() function:' 
print np.remainder(a,b)
```

Il produira le résultat suivant -

```python
First array:                                                                  
[10 20 30]

Second array:                                                                 
[3 5 7]

Applying mod() function:                                                      
[1 0 2]

Applying remainder() function:                                                
[1 0 2]
```

Les fonctions suivantes sont utilisées pour effectuer des opérations sur des tableaux avec des nombres complexes.

- ```numpy.real()``` − renvoie la partie réelle de l'argument de type de données complexes.
- ```numpy.imag()``` − renvoie la partie imaginaire de l'argument de type de données complexes.
- ```numpy.conj()``` − renvoie le conjugué complexe, qui est obtenu en changeant le signe de la partie imaginaire.
- ```numpy.angle()``` − renvoie l'angle de l'argument complexe. La fonction a un paramètre degré. Si vrai, l'angle en degré est retourné, sinon l'angle est en radians.

```python
import numpy as np 
a = np.array([-5.6j, 0.2j, 11. , 1+1j]) 

print 'Our array is:' 
print a 
print '\n'  

print 'Applying real() function:' 
print np.real(a) 
print '\n'  

print 'Applying imag() function:' 
print np.imag(a) 
print '\n'  

print 'Applying conj() function:' 
print np.conj(a) 
print '\n'  

print 'Applying angle() function:' 
print np.angle(a) 
print '\n'  

print 'Applying angle() function again (result in degrees)' 
print np.angle(a, deg = True)
```

Il produira le résultat suivant -

```python
Our array is:
[ 0.-5.6j 0.+0.2j 11.+0.j 1.+1.j ]

Applying real() function:
[ 0. 0. 11. 1.]

Applying imag() function:
[-5.6 0.2 0. 1. ]

Applying conj() function:
[ 0.+5.6j 0.-0.2j 11.-0.j 1.-1.j ]

Applying angle() function:
[-1.57079633 1.57079633 0. 0.78539816]

Applying angle() function again (result in degrees)
[-90. 90. 0. 45.]
```