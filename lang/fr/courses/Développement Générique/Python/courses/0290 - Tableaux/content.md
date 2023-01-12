Un tableau est un conteneur qui peut contenir un nombre fixe d'éléments et ces éléments doivent être du même type. La plupart des structures de données utilisent des tableaux pour mettre en œuvre leurs algorithmes. Les termes importants pour comprendre le concept de tableau sont les suivants :

- **Élément** : Chaque élément stocké dans un tableau est appelé un élément.
- **Index** : Chaque emplacement d'un élément dans un tableau a un index numérique, qui est utilisé pour identifier l'élément.

## Représentation des tableaux

Les tableaux peuvent être déclarés de diverses manières dans différents langages. En voici une illustration.

![Illustration des tableaux](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/Python/courses/0290%20-%20Tableaux/images/image1.jpg)

Selon l'illustration ci-dessus, les points importants à prendre en compte sont les suivants :

- L'index commence par 0.
- La longueur du tableau est de 10, ce qui signifie qu'il peut stocker 10 éléments.
- Chaque élément est accessible via son index. Par exemple, nous pouvons récupérer un élément à l'indice 6 comme 9.

## Opérations de base

Les opérations de base supportées par un tableau sont les suivantes :

- **Traverse** : imprime tous les éléments du tableau un par un.
- **Insertion** : Ajoute un élément à l'index donné.
- **Deletion** : Supprime un élément à l'index donné.
- **Search** : Recherche un élément à l'aide de l'index donné ou de la valeur.
- **Update** : Met à jour un élément à l'index donné.

Un tableau est créé en Python en important le module array dans le programme Python. Ensuite, le tableau est déclaré comme indiqué ci-dessous :

```python
from array import *

arrayName = array(typecode, [Initializers])
```

Les Typecodes sont les codes qui sont utilisés pour définir le type de valeur que le tableau va contenir. Certains codes de type courants sont utilisés comme suit :

| **Typecode** | **Valeur** |
| --- | --- |
| b | Représente un entier signé de taille 1 octet. |
| B | Représente un nombre entier non signé de taille 1 octet. |
| c | Représente un caractère de taille 1 octet. |
| i | Représente un entier signé de taille 2 octets. |
| l | Représente un nombre entier non signé de 2 octets. |
| f | Représente un point flottant de taille 4 octets. |
| d | Représente un point flottant de taille 8 octets. |

Avant d'examiner les différentes opérations sur les tableaux, créons et imprimons un tableau en utilisant Python.

### Exemple

Le code ci-dessous crée un tableau nommé array1.

```python
from array import *

array1 = array('i', [10,20,30,40,50])

for x in array1:
   print(x)
```

### Réponse

Lorsque nous compilons et exécutons le programme ci-dessus, il produit le résultat suivant :

```bash
10
20
30
40
50
```

## Accès aux éléments d'un tableau

Nous pouvons accéder à chaque élément d'un tableau en utilisant l'index de l'élément. Le code ci-dessous montre comment accéder à un élément d'un tableau.

### Exemple

```python
from array import *

array1 = array('i', [10,20,30,40,50])

print(array1[0])

print(array1[2])
```

### Réponse

Lorsque nous compilons et exécutons le programme ci-dessus, il produit le résultat suivant, qui montre que l'élément est inséré à la position d'index 1.

```bash
10
30
```

## Opération d'insertion

L'opération d'insertion consiste à insérer un ou plusieurs éléments de données dans un tableau. En fonction des besoins, un nouvel élément peut être ajouté au début, à la fin ou à n'importe quel index du tableau.

### Exemple

Ici, nous ajoutons un élément de données au milieu du tableau en utilisant la méthode ```insert()``` intégrée à Python.

```python
from array import *

array1 = array('i', [10,20,30,40,50])

array1.insert(1,60)

for x in array1:
    print(x)
```

Lorsque nous compilons et exécutons le programme ci-dessus, il produit le résultat suivant qui montre que l'élément est inséré à la position d'index 1.

### Réponse

```bash
10
60
20
30
40
50
```

## Opération de suppression

La suppression consiste à retirer un élément existant du tableau et à réorganiser tous les éléments d'un tableau.

### Exemple

Ici, nous supprimons un élément de données au milieu du tableau en utilisant la méthode ```remove()``` intégrée à Python.

```python
from array import *

array1 = array('i', [10,20,30,40,50])

array1.remove(40)

for x in array1:
    print(x)
```

### Réponse

Lorsque nous compilons et exécutons le programme ci-dessus, il produit le résultat suivant qui montre que l'élément est retiré du tableau.

```bash
10
20
30
50
```

## Opération de recherche

Vous pouvez effectuer une recherche sur un élément de tableau en fonction de sa valeur ou de son index.

### Exemple

Ici, nous recherchons un élément de données en utilisant la méthode index() intégrée à Python.

```python
from array import *

array1 = array('i', [10,20,30,40,50])

print(array1.index(40))
```

### Réponse

Lorsque nous compilons et exécutons le programme ci-dessus, il produit le résultat suivant qui indique l'indice de l'élément. Si la valeur n'est pas présente dans le tableau, le programme renvoie une erreur.

```bash
3
```

## Opération de mise à jour

L'opération de mise à jour consiste à mettre à jour un élément existant du tableau à un index donné.

### Exemple

Ici, nous affectons simplement une nouvelle valeur à l'index que nous voulons mettre à jour.

```python
from array import *

array1 = array('i', [10,20,30,40,50])

array1[2] = 80

for x in array1:
    print(x)
```

### Réponse

Lorsque nous compilons et exécutons le programme ci-dessus, il produit le résultat suivant qui montre la nouvelle valeur à la position d'index 2.

```bash
10
20
80
40
50
```
