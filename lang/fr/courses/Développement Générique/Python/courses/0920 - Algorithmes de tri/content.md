Le tri consiste à organiser les données dans un format particulier. L'algorithme de tri spécifie la manière d'organiser les données dans un ordre particulier. Les ordres les plus courants sont l'ordre numérique ou lexicographique.

L'importance du tri réside dans le fait que la recherche de données peut être optimisée à un niveau très élevé, si les données sont stockées de manière triée. Le tri est également utilisé pour représenter les données dans des formats plus lisibles. Nous présentons ci-dessous cinq implémentations du tri en python.

- Tri à bulles
- Tri par fusion
- Tri par insertion
- Tri Shell
- Tri sélectif

## Tri à bulles

Il s'agit d'un algorithme basé sur la comparaison dans lequel chaque paire d'éléments adjacents est comparée et les éléments sont échangés s'ils ne sont pas dans l'ordre.

### Exemple

```python
def bubblesort(custom_list):
    # Swap the elements to arrange in order
    for iter_num in range(len(custom_list)-1,0,-1):
        for idx in range(iter_num):
            if custom_list[idx] > custom_list[idx+1]:
                temp = custom_list[idx]
                custom_list[idx] = custom_list[idx+1]
                custom_list[idx+1] = temp
custom_list = [19, 2, 31, 45, 6, 11, 121, 27]
bubblesort(custom_list)
print(custom_list)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[2, 6, 11, 19, 27, 31, 45, 121]
```

## Tri par fusion

Le tri par fusion divise d'abord le tableau en moitiés égales, puis les combine de manière triée.

### Exemple

```python
def merge_sort(unsorted_list):
    if len(unsorted_list) <= 1:
        return unsorted_list
    # Find the middle point and devide it
    middle = len(unsorted_list) // 2
    left_list = unsorted_list[:middle]
    right_list = unsorted_list[middle:]

    left_list = merge_sort(left_list)
    right_list = merge_sort(right_list)
    return list(merge(left_list, right_list))

# Merge the sorted halves
def merge(left_half,right_half):
    res = []
    while len(left_half) != 0 and len(right_half) != 0:
        if left_half[0] < right_half[0]:
            res.append(left_half[0])
            left_half.remove(left_half[0])
        else:
            res.append(right_half[0])
            right_half.remove(right_half[0])
    if len(left_half) == 0:
        res = res + right_half
    else:
        res = res + left_half
    return res
unsorted_list = [64, 34, 25, 12, 22, 11, 90]
print(merge_sort(unsorted_list))
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[11, 12, 22, 25, 34, 64, 90]
```

## Tri par insertion

Le tri par insertion consiste à trouver la bonne place pour un élément donné dans une liste triée. Donc, au début, nous comparons les deux premiers éléments et nous les trions en les comparant. Ensuite, nous choisissons le troisième élément et trouvons sa position correcte parmi les deux éléments triés précédents. De cette façon, nous ajoutons progressivement d'autres éléments à la liste déjà triée en les plaçant à la bonne place.

### Exemple

```python
def insertion_sort(InputList):
    for i in range(1, len(InputList)):
        j = i - 1
        nxt_element = InputList[i]
    # Compare the current element with next one
    while (InputList[j] > nxt_element) and (j >= 0):
        InputList[j+1] = InputList[j]
        j = j - 1
    InputList[j+1] = nxt_element
list = [19, 2, 31, 45, 30, 11, 121, 27]
insertion_sort(list)
print(list)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[2, 11, 19, 27, 30, 31, 45, 121]
```

## Tri Shell

Le tri Shell consiste à trier des éléments qui sont éloignés les uns des autres. Nous trions une grande sous-liste d'une liste donnée et continuons à réduire la taille de la liste jusqu'à ce que tous les éléments soient triés. Le programme ci-dessous trouve l'écart en l'assimilant à la moitié de la longueur de la liste, puis commence à trier tous les éléments qui s'y trouvent. Ensuite, nous continuons à réinitialiser l'écart jusqu'à ce que la liste entière soit triée.

### Exemple

```python
def shellSort(input_list):
    gap = len(input_list) // 2
    while gap > 0:
        for i in range(gap, len(input_list)):
            temp = input_list[i]
            j = i
    # Sort the sub list for this gap
    while j >= gap and input_list[j - gap] > temp:
        input_list[j] = input_list[j - gap]
        j = j - gap
        input_list[j] = temp
    # Reduce the gap for the next element
    gap = gap//2
list = [19, 2, 31, 45, 30, 11, 121, 27]
shellSort(list)
print(list)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[2, 11, 19, 27, 30, 31, 45, 121]
```

## Tri sélectif

Dans le tri sélectif, on commence par trouver la valeur minimale dans une liste donnée et on la déplace vers une liste triée. Ensuite, nous répétons le processus pour chacun des éléments restants dans la liste non triée. L'élément suivant qui entre dans la liste triée est comparé aux éléments existants et placé à sa position correcte, de sorte qu'à la fin, tous les éléments de la liste non triée sont triés.

### Exemple

```python
def selection_sort(input_list):
    for idx in range(len(input_list)):
        min_idx = idx
        for j in range( idx +1, len(input_list)):
            if input_list[min_idx] > input_list[j]:
            min_idx = j
    # Swap the minimum value with the compared value
    input_list[idx], input_list[min_idx] = input_list[min_idx], input_list[idx]
l = [19, 2, 31, 45, 30, 11, 121, 27]
selection_sort(l)
print(l)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[2, 11, 19, 27, 30, 31, 45, 121]
```
