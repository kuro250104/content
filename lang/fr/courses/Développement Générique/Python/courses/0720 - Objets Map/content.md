Python Maps, également appelé ChainMap, est un type de structure de données permettant de gérer plusieurs dictionnaires ensemble comme une seule unité. Le dictionnaire combiné contient les paires de clés et de valeurs dans un ordre spécifique, éliminant tout doublon de clés. La meilleure utilisation de ChainMap est de rechercher dans plusieurs dictionnaires à la fois et d'obtenir le mappage approprié des paires clé-valeur. Nous constatons également que ces ChainMaps se comportent comme une structure de données en pile.

## Création d'un ChainMap

Nous créons deux dictionnaires et les combinons à l'aide de la méthode ChainMap de la bibliothèque ```collections```. Puis nous imprimons les clés et les valeurs du résultat de la combinaison des dictionnaires. S'il y a des clés en double, alors seule la valeur de la première clé est conservée.

```python
import collections

dict1 = {'day1': 'Mon', 'day2': 'Tue'}
dict2 = {'day3': 'Wed', 'day1': 'Thu'}

res = collections.ChainMap(dict1, dict2)

# Creating a single dictionary
print(res.maps,'\n')

print('Keys = {}'.format(list(res.keys())))
print('Values = {}'.format(list(res.values())))
print()

# Print all the elements from the result
print('elements:')
for key, val in res.items():
    print('{} = {}'.format(key, val))
print()

# Find a specific value in the result
print('day3 in res: {}'.format(('day1' in res)))
print('day4 in res: {}'.format(('day4' in res)))
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
[{'day1': 'Mon', 'day2': 'Tue'}, {'day1': 'Thu', 'day3': 'Wed'}] 

Keys = ['day1', 'day3', 'day2']
Values = ['Mon', 'Wed', 'Tue']

elements:
day1 = Mon
day3 = Wed
day2 = Tue

day3 in res: True
day4 in res: False
```

## Réorganisation d’un objet map

Si nous changeons l'ordre des dictionnaires en les regroupant dans l'exemple ci-dessus, nous voyons que la position des éléments est interchangée comme s'ils étaient dans une chaîne continue. Cela montre à nouveau le comportement de Map en tant que pile.

### Exemple

```python
import collections

dict1 = {'day1': 'Mon', 'day2': 'Tue'}
dict2 = {'day3': 'Wed', 'day4': 'Thu'}

res1 = collections.ChainMap(dict1, dict2)
print(res1.maps,'\n')

res2 = collections.ChainMap(dict2, dict1)
print(res2.maps,'\n')
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[{'day1': 'Mon', 'day2': 'Tue'}, {'day3': 'Wed', 'day4': 'Thu'}] 

[{'day3': 'Wed', 'day4': 'Thu'}, {'day1': 'Mon', 'day2': 'Tue'}] 
```

## Mettre à jour l’objet map

Lorsque l'élément du dictionnaire est mis à jour, le résultat est instantanément mis à jour dans le résultat du ChainMap. Dans l'exemple ci-dessous, nous voyons que la nouvelle valeur mise à jour se reflète dans le résultat sans avoir à réappliquer explicitement la méthode ```ChainMap```.

### Exemple

```python
import collections

dict1 = {'day1': 'Mon', 'day2': 'Tue'}
dict2 = {'day3': 'Wed', 'day4': 'Thu'}

res = collections.ChainMap(dict1, dict2)
print(res.maps,'\n')

dict2['day4'] = 'Fri'
print(res.maps,'\n')
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[{'day1': 'Mon', 'day2': 'Tue'}, {'day3': 'Wed', 'day4': 'Thu'}] 

[{'day1': 'Mon', 'day2': 'Tue'}, {'day3': 'Wed', 'day4': 'Fri'}] 
```