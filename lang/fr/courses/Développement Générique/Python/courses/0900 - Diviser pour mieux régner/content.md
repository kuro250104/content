Dans l'approche "diviser pour régner", le problème à résoudre est divisé en sous-problèmes plus petits, puis chaque problème est résolu indépendamment. Si nous continuons à diviser les sous-problèmes en sous-problèmes encore plus petits, nous pouvons finalement atteindre un stade où plus aucune division n'est possible. Ces sous-problèmes "atomiques" les plus petits possibles (fractions) sont résolus. La solution de tous les sous-problèmes est finalement fusionnée afin d'obtenir la solution d'un problème original.

De manière générale, nous pouvons comprendre l'approche "diviser pour régner" par un processus en trois étapes.

## Diviser/Rompre

Cette étape consiste à décomposer le problème en sous-problèmes plus petits. Les sous-problèmes doivent représenter une partie du problème initial. Cette étape adopte généralement une approche récursive pour diviser le problème jusqu'à ce qu'aucun sous-problème ne soit plus divisible. À ce stade, les sous-problèmes deviennent atomiques par nature mais représentent toujours une partie du problème réel.

## Conquérir/Solvabiliser

Cette étape reçoit un grand nombre de sous-problèmes plus petits à résoudre. En général, à ce niveau, les problèmes sont considérés comme "résolus" par eux-mêmes.

## Fusionner/Combiner

Lorsque les sous-problèmes plus petits sont résolus, cette étape les combine récursivement jusqu'à ce qu'ils forment une solution du problème original. Cette approche algorithmique fonctionne de manière récursive et les étapes de conquête et de fusion sont si proches qu'elles apparaissent comme une seule et même solution.

### Exemples

Le programme suivant est un exemple d'approche de programmation de type "diviser pour régner" où la recherche binaire est mise en œuvre à l'aide de python.

## Mise en œuvre de la recherche binaire

Dans la recherche binaire, on prend une liste d'éléments triés et on commence à chercher un élément au milieu de la liste. Si la valeur recherchée correspond à la valeur du milieu de la liste, nous terminons la recherche. Sinon, nous éliminons la moitié de la liste d'éléments en choisissant de procéder avec la moitié droite ou gauche de la liste en fonction de la valeur de l'élément recherché.

Ceci est possible car la liste est triée et c'est beaucoup plus rapide que la recherche linéaire. Ici, nous divisons la liste donnée et conquérons en choisissant la bonne moitié de la liste. Nous répétons cette approche jusqu'à ce que nous trouvions l'élément ou que nous concluions à son absence dans la liste.

### Exemple

```python
def bsearch(list, val):
    list_size = len(list) - 1
    idx0 = 0
    idxn = list_size
    # Find the middle most value
    while idx0 <= idxn:
        midval = (idx0 + idxn)// 2
        if list[midval] == val:
            return midval
    # Compare the value the middle most value
    if val > list[midval]:
        idx0 = midval + 1
    else:
        idxn = midval - 1
    if idx0 > idxn:
        return None

# Initialize the sorted list
list = [2, 7, 19, 34, 53, 72]

# Print the search result
print(bsearch(list, 72))
print(bsearch(list, 11))
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
5
None
```
