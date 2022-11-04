Heap est une structure arborescente spéciale dans laquelle chaque nœud parent est inférieur ou égal à son nœud enfant. Il s'agit alors d'un tas minimal. Si chaque nœud parent est supérieur ou égal à son nœud enfant, il s'agit d'un tas maximum. Il est très utile pour mettre en œuvre des files d'attente prioritaires où l'élément de la file d'attente ayant un poids plus élevé est traité en priorité.

Une discussion détaillée sur les tas est disponible sur notre site web ici. Veuillez l'étudier en premier si vous êtes novice en matière de structure de données heap. Dans ce chapitre, nous allons voir l'implémentation de la structure de données heap en utilisant Python.

## Créer un tas

Un tas est créé en utilisant la bibliothèque intégrée de Python appelée heapq. Cette bibliothèque possède les fonctions nécessaires pour effectuer diverses opérations sur la structure de données du tas. Vous trouverez ci-dessous une liste de ces fonctions.

- ```heapify``` : Cette fonction convertit une liste régulière en un tas. Dans le tas résultant, le plus petit élément est poussé à la position d'index 0. Mais le reste des éléments de données ne sont pas nécessairement triés.
- ```heappush``` : Cette fonction ajoute un élément au tas sans modifier le tas actuel.
- ```heappop``` : Cette fonction retourne le plus petit élément de données du tas.
- ```heapreplace``` : Cette fonction remplace le plus petit élément de données par une nouvelle valeur fournie dans la fonction.

## Création d'un tas

Un tas est créé en utilisant simplement une liste d'éléments avec la fonction heapify. Dans l'exemple ci-dessous, nous fournissons une liste d'éléments et la fonction heapify réorganise les éléments en plaçant le plus petit élément en première position.

### Exemple

```python
import heapq

H = [21,1,45,78,3,5]
# Use heapify to rearrange the elements
heapq.heapify(H)
print(H)
Réponse
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[1, 3, 5, 78, 21, 45]
```

## Insertion dans le tas

L'insertion d'un élément de données dans un tas ajoute toujours l'élément au dernier index. Mais vous pouvez appliquer la fonction heapify à nouveau pour amener l'élément nouvellement ajouté au premier index seulement si sa valeur est la plus petite. Dans l'exemple ci-dessous, nous insérons le nombre 8.

### Exemple

```python
import heapq

H = [21,1,45,78,3,5]
# Covert to a heap
heapq.heapify(H)
print(H)

# Add element
heapq.heappush(H,8)
print(H)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[1, 3, 5, 78, 21, 45]
[1, 3, 5, 78, 21, 45, 8]
```

## Retirer du tas

Vous pouvez supprimer l'élément au premier index en utilisant cette fonction. Dans l'exemple ci-dessous, la fonction supprimera toujours l'élément à la position d'index 1.

### Exemple

```python
import heapq

H = [21,1,45,78,3,5]
# Create the heap

heapq.heapify(H)
print(H)

# Remove element from the heap
heapq.heappop(H)

print(H)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[1, 3, 5, 78, 21, 45]
[3, 21, 5, 78, 45]
```

## Remplacement dans un tas

La fonction de remplacement du tas supprime toujours le plus petit élément du tas et insère le nouvel élément entrant à un endroit non fixé par un ordre quelconque.

### Exemple

```python
import heapq

H = [21,1,45,78,3,5]
# Create the heap

heapq.heapify(H)
print(H)

# Replace an element
heapq.heapreplace(H,6)
print(H)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[1, 3, 5, 78, 21, 45]
[3, 6, 5, 78, 21, 45]
```