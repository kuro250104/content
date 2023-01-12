Chaque clé est séparée de sa valeur par deux points ```:```, les éléments sont séparés par des virgules, et le tout est entouré d'accolades. Un dictionnaire vide, sans aucun élément, est écrit avec seulement deux accolades, comme ceci : ```{}```.

Les clés sont uniques dans un dictionnaire, alors que les valeurs peuvent ne pas l'être. Les valeurs d'un dictionnaire peuvent être de n'importe quel type, mais les clés doivent être d'un type de données immuable, comme les chaînes de caractères, les nombres ou les tuples.

## Accès aux valeurs d'un dictionnaire

Pour accéder aux éléments d'un dictionnaire, vous pouvez utiliser les crochets familiers avec la clé pour obtenir sa valeur. Voici un exemple simple :

```python
#!/usr/bin/python3

dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
print("dict['Name']:", dict['Name'])
print("dict['Age']:", dict['Age'])
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
dict['Name']: Zara
dict['Age']: 7
```

Si nous essayons d'accéder à un élément de données avec une clé qui ne fait pas partie du dictionnaire, nous obtenons une erreur comme suit :

```python
#!/usr/bin/python3

dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'};
print("dict['Alice']:", dict['Alice'])
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
dict['Zara']:
Traceback (most recent call last):
    File "test.py", line 4, in <module>
        print "dict['Alice']: ", dict['Alice'];
KeyError: 'Alice'
```

## Mise à jour d'un dictionnaire

Vous pouvez mettre à jour un dictionnaire en ajoutant une nouvelle entrée ou une paire clé-valeur, en modifiant une entrée existante ou en supprimant une entrée existante, comme le montre l'exemple simple ci-dessous.

```python
#!/usr/bin/python3

dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
dict['Age'] = 8 # update existing entry
dict['School'] = "DPS School" # Add new entry

print("dict['Age']:", dict['Age'])
print("dict['School']:", dict['School'])
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
dict['Age']: 8
dict['School']: DPS School
```

## Supprimer des éléments de dictionnaire

Vous pouvez soit supprimer des éléments de dictionnaire individuels, soit effacer l'intégralité du contenu d'un dictionnaire. Vous pouvez également supprimer un dictionnaire entier en une seule opération.

Pour supprimer explicitement un dictionnaire entier, il suffit d'utiliser l'instruction del. Voici un exemple simple :

```python
#!/usr/bin/python3

dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}

del dict['Name'] # remove entry with key 'Name'
dict.clear()     # remove all entries in dict
del dict         # delete entire dictionary

print("dict['Age']:", dict['Age'])
print("dict['School']:", dict['School'])
```

Cela produit le résultat suivant.

Une exception est levée car après ```del dict```, le dictionnaire n'existe plus.

```bash
dict['Age']:
Traceback (most recent call last):
    File "test.py", line 8, in <module>
        print "dict['Age']:", dict['Age'];
TypeError: 'type' object is unsubscriptable
```

__Remarque__ : La méthode ```del()``` est abordée dans la section suivante.

## Propriétés des clés de dictionnaire

Les valeurs de dictionnaire n'ont aucune restriction. Elles peuvent être n'importe quel objet Python arbitraire, qu'il s'agisse d'objets standard ou d'objets définis par l'utilisateur. Cependant, il n'en va pas de même pour les clés.

Il y a deux points importants à retenir au sujet des clés de dictionnaire :

**(a)** Il est interdit d'avoir plus d'une entrée par clé. Cela signifie qu'aucun doublon de clé n'est autorisé. Lorsque des clés en double sont rencontrées pendant l'affectation, la dernière affectation l'emporte. Par exemple :

```python
#!/usr/bin/python3

dict = {'Name': 'Zara', 'Age': 7, 'Name': 'Manni'}
print("dict['Name']:", dict['Name'])
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
dict['Name']: Manni
```

**(b)** Les clés doivent être immuables. Cela signifie que vous pouvez utiliser des chaînes de caractères, des nombres ou des tuples comme clés de dictionnaire, mais quelque chose comme ```['clé']``` n'est pas autorisé. Voici un exemple simple :

```python
#!/usr/bin/python3

dict = {['Name']: 'Zara', 'Age': 7}
print("dict['Name']:", dict['Name'])
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
Traceback (most recent call last):
    File "test.py", line 3, in <module>
        dict = {['Name']:'Zara', 'Age': 7}
TypeError: list objects are unhashable
```

## Fonctions et méthodes de dictionnaire intégrées

Python inclut les fonctions de dictionnaire suivantes :

- ```cmp(dict1, dict2)``` : n'est plus disponible en Python 3.
- ```len(dict)``` : Donne la longueur totale du dictionnaire. Ceci est égal au nombre d'éléments dans le dictionnaire.
- ```str(dict)``` : Produit une représentation sous forme de chaîne imprimable d'un dictionnaire.
- ```type(variable)``` : Retourne le type de la variable passée. Si la variable passée est un dictionnaire, alors elle renvoie un type de dictionnaire.

Python inclut les méthodes de dictionnaire suivantes :

- ```dict.clear()``` : Supprime tous les éléments du dictionnaire dict.
- ```dict.copy()``` : Retourne une copie superficielle du dictionnaire dict.
- ```dict.fromkeys()``` : crée un nouveau dictionnaire avec les clés de seq et les valeurs de value.
- ```dict.get(key, default=None)``` : Pour la clé key, retourne la valeur ou la valeur par défaut si la clé n'est pas dans le dictionnaire.
- ```dict.has_key(key)``` : Supprimé, utilisez l'opération in à la place.
- ```dict.items()``` : Retourne une liste de paires de tuplets (clé, valeur) du dict.
- ```dict.keys()``` : Retourne la liste des clés du dictionnaire dict.
- ```dict.setdefault(key, default = None)``` : Similaire à get(), mais définira dict[key] = default si la clé n'est pas déjà dans le dict.
- ```dict.update(dict2)``` : Ajoute les paires clé-valeur du dictionnaire dict2 à dict
- ```dict.values()``` : Retourne la liste des valeurs du dictionnaire dict.
