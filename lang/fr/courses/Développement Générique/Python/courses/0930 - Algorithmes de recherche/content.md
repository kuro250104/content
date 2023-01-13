La recherche est une nécessité fondamentale lorsque vous stockez des données dans différentes structures de données. L'approche la plus simple consiste à parcourir chaque élément de la structure de données et à le faire correspondre à la valeur recherchée, ce que l'on appelle la recherche linéaire. Elle est inefficace et rarement utilisée, mais la création d'un programme à cet effet donne une idée de la manière dont nous pouvons mettre en œuvre certains algorithmes de recherche avancés.

## Recherche linéaire

Dans ce type de recherche, une recherche séquentielle est effectuée sur tous les éléments un par un. Chaque élément est vérifié et si une correspondance est trouvée, cet élément particulier est renvoyé, sinon la recherche continue jusqu'à la fin de la structure de données.

### Exemple

```python
def linear_search(values, search_for):
    search_at = 0
    search_res = False
    # Match the value with each data element	
    while search_at < len(values) and search_res is False:
        if values[search_at] == search_for:
            search_res = True
        else:
            search_at = search_at + 1
    return search_res
l = [64, 34, 25, 12, 22, 11, 90]
print(linear_search(l, 12))
print(linear_search(l, 91))
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
True
False
```

## Recherche par interpolation

Cet algorithme de recherche fonctionne sur la position de sondage de la valeur requise. Pour que cet algorithme fonctionne correctement, la collection de données doit être triée et répartie de manière égale. Initialement, la position de sondage est la position de l'élément le plus central de la collection. Si une correspondance se produit, l'index de l'élément est renvoyé. Si l'élément central est supérieur à l'élément, la position de sondage est à nouveau calculée dans le sous-groupe à droite de l'élément central. Sinon, l'élément est recherché dans le sous-réseau à gauche de l'élément du milieu. Ce processus se poursuit également dans le sous-groupe jusqu'à ce que la taille du sous-groupe soit réduite à zéro.

### Exemple

Il existe une formule spécifique pour calculer la position médiane qui est indiquée dans le programme ci-dessous :

```python
def intpolsearch(values, x):
    idx0 = 0
    idxn = (len(values) - 1)
    while idx0 <= idxn and x >= values[idx0] and x <= values[idxn]:
    # Find the mid point
        mid = idx0 +\
        int(((float(idxn - idx0)/( values[idxn] - values[idx0]))
        * ( x - values[idx0])))
    # Compare the value at mid point with search value 
    if values[mid] == x:
        return "Found "+str(x)+" at index "+str(mid)
    if values[mid] < x:
        idx0 = mid + 1
    return "Searched element not in the list"

l = [2, 6, 11, 19, 27, 31, 45, 121]
print(intpolsearch(l, 2))
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Found 2 at index 0
```
