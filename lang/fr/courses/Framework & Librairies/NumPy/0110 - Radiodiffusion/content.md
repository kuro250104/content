## Introduction

Le terme **diffusion** fait référence à la capacité de NumPy à traiter des tableaux de formes différentes lors des opérations arithmétiques. Les opérations arithmétiques sur les tableaux sont généralement effectuées sur les éléments correspondants. Si deux tableaux sont exactement de la même forme, alors ces opérations sont effectuées sans problème.

### Exemple 1

```python
import numpy as np 

a = np.array([1,2,3,4]) 
b = np.array([10,20,30,40]) 
c = a * b 
print c
```

Sa sortie est la suivante -

```python
[10   40   90   160]
```

Si les dimensions de deux tableaux sont dissemblables, les opérations d'élément à élément ne sont pas possibles. Cependant, les opérations sur des tableaux de formes non similaires sont toujours possibles dans NumPy, grâce à la capacité de diffusion. Le tableau le plus petit est **diffusé** à la taille du tableau le plus grand afin qu'ils aient des formes compatibles.

La diffusion est possible si les règles suivantes sont satisfaites -

- Le tableau ayant un **ndim** plus petit que l'autre est précédé de '1' dans sa forme.
- La taille dans chaque dimension de la forme de sortie est le maximum des tailles d'entrée dans cette dimension.
- Une entrée peut être utilisée dans un calcul, si sa taille dans une dimension particulière correspond à la taille de la sortie ou si sa valeur est exactement 1.
- Si une entrée a une dimension de 1, la première entrée de données dans cette dimension est utilisée pour tous les calculs le long de cette dimension.

On dit d'un ensemble de tableaux qu'il est **diffusable** si les règles ci-dessus produisent un résultat valide et si l'un des éléments suivants est vrai -

- Les tableaux ont exactement la même forme.
- Les tableaux ont le même nombre de dimensions et la longueur de chaque dimension est soit une longueur commune, soit 1.
- Un tableau ayant trop peu de dimensions peut voir sa forme précédée d'une dimension de longueur 1, de sorte que la propriété énoncée ci-dessus soit vraie.

Le programme suivant montre un exemple de diffusion.

### Exemple 2

```python
import numpy as np 
a = np.array([[0.0,0.0,0.0],[10.0,10.0,10.0],[20.0,20.0,20.0],[30.0,30.0,30.0]]) 
b = np.array([1.0,2.0,3.0])  

print 'First array:' 
print a 
print '\n'  

print 'Second array:' 
print b 
print '\n'  

print 'First Array + Second Array' 
print a + b
```

La sortie de ce programme serait la suivante -

```python
First array:
[
    [ 0. 0. 0.]
    [ 10. 10. 10.]
    [ 20. 20. 20.]
    [ 30. 30. 30.]
]

Second array:
[ 1. 2. 3.]

First Array + Second Array
[
    [ 1. 2. 3.]
    [ 11. 12. 13.]
    [ 21. 22. 23.]
    [ 31. 32. 33.]
]
```