## Introduction

Les objets ndarray peuvent être sauvegardés et chargés depuis les fichiers du disque. Les fonctions IO disponibles sont -

- ```load()``` and ```save()``` functions handle /numPy binary files (with npy extension)
- ```loadtxt()``` and ```savetxt()``` functions handle normal text files

NumPy introduit un format de fichier simple pour les objets ndarray. Ce fichier .npy stocke les données, la forme, le dtype et d'autres informations nécessaires pour reconstruire le ndarray dans un fichier disque de sorte que le tableau soit correctement récupéré même si le fichier se trouve sur une autre machine avec une architecture différente.

## numpy.save()

Le fichier ```numpy.save()``` stocke le tableau d'entrée dans un fichier disque avec une extension npy.

```python
import numpy as np 
a = np.array([1,2,3,4,5]) 
np.save('outfile',a)
```

Pour reconstruire le tableau à partir de outfile.npy, utilisez la fonction ```load()```.

```python
import numpy as np 
b = np.load('outfile.npy') 
print b
```

Il produira le résultat suivant -

```python
array([1, 2, 3, 4, 5])
```

Les fonctions ```save()``` et ```load()``` acceptent un paramètre booléen supplémentaire allow_pickles. En Python, un pickle est utilisé pour sérialiser et désérialiser des objets avant de les enregistrer ou de les lire dans un fichier disque.

## savetxt()

Le stockage et la récupération des données d'un tableau au format d'un simple fichier texte sont effectués à l'aide des fonctions savetxt() et loadtxt().

```python
import numpy as np 

a = np.array([1,2,3,4,5]) 
np.savetxt('out.txt',a) 
b = np.loadtxt('out.txt') 
print b
```

Il produira le résultat suivant -

```python
[ 1.  2.  3.  4.  5.] 
```

Les fonctions ```savetxt()``` et ```loadtxt()``` acceptent des paramètres facultatifs supplémentaires tels que l'en-tête, le pied de page et le délimiteur.