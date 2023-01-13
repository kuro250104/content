La récursion permet à une fonction de s'appeler elle-même. Des étapes fixes du code sont exécutées encore et encore pour de nouvelles valeurs. Nous devons également définir des critères pour décider de la fin de l'appel récursif. Dans l'exemple ci-dessous, nous voyons une approche récursive de la recherche binaire. Nous prenons une liste triée et donnons sa plage d'index comme entrée à la fonction récursive.

## Recherche binaire par récursion

Nous implémentons l'algorithme de recherche binaire en utilisant Python comme indiqué ci-dessous. Nous utilisons une liste ordonnée d'éléments et concevons une fonction récursive qui prend en entrée la liste ainsi que l'indice de début et de fin. Ensuite, la fonction de recherche binaire s'appelle elle-même jusqu'à ce qu'elle trouve l'élément recherché ou conclut à son absence dans la liste.

### Exemple

```python
def bsearch(list, idx0, idxn, val):
    if (idxn < idx0):
        return None
    else:
        midval = idx0 + ((idxn - idx0) // 2)
    # Compare the search item with middle most value
    if list[midval] > val:
        return bsearch(list, idx0, midval-1,val)
    else if list[midval] < val:
        return bsearch(list, midval+1, idxn, val)
    else:
        return midval

list = [8, 11, 24, 56, 88, 131]
print(bsearch(list, 0, 5, 24))
print(bsearch(list, 0, 5, 51))
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
2
None
```
