Les tables de hachage sont un type de structure de données dans laquelle l'adresse ou la valeur d'index de l'élément de données est générée à partir d'une fonction de hachage. Cela permet d'accéder plus rapidement aux données car la valeur d'index se comporte comme une clé pour la valeur des données. En d'autres termes, la table de hachage stocke des paires clé-valeur, mais la clé est générée par une fonction de hachage.

Ainsi, la fonction de recherche et d'insertion d'un élément de données devient beaucoup plus rapide car les valeurs de la clé deviennent elles-mêmes l'index du tableau qui stocke les données.

En Python, les types de données Dictionary représentent l'implémentation des tables de hachage. Les clés du dictionnaire répondent aux exigences suivantes.

- Les clés du dictionnaire sont hachables, c'est-à-dire qu'elles sont générées par une fonction de hachage qui génère un résultat unique pour chaque valeur unique fournie à la fonction de hachage.
- L'ordre des éléments de données dans un dictionnaire n'est pas fixe.

Nous voyons donc l'implémentation de la table de hachage en utilisant les types de données du dictionnaire comme ci-dessous.

## Accès aux valeurs du dictionnaire

Pour accéder aux éléments du dictionnaire, vous pouvez utiliser les crochets familiers avec la clé pour obtenir sa valeur.

### Exemple

```python
# Declare a dictionary 
dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}

# Accessing the dictionary with its key
print("dict['Name']:", dict['Name'])
print("dict['Age']:", dict['Age'])
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
dict['Name']: Zara
dict['Age']: 7
```

## Mise à jour du dictionnaire

Vous pouvez mettre à jour un dictionnaire en ajoutant une nouvelle entrée ou une paire clé-valeur, en modifiant une entrée existante ou en supprimant une entrée existante comme le montre l'exemple simple ci-dessous :

### Exemple

```python
# Declare a dictionary
dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
dict['Age'] = 8 # update existing entry
dict['School'] = "DPS School" # Add new entry
print("dict['Age']:", dict['Age'])
print("dict['School']:", dict['School'])
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
dict['Age']: 8
dict['School']: DPS School
```

## Supprimer les éléments du dictionnaire

Vous pouvez soit supprimer des éléments individuels du dictionnaire, soit effacer tout le contenu d'un dictionnaire. Vous pouvez également supprimer un dictionnaire entier en une seule opération. Pour supprimer explicitement un dictionnaire entier, il suffit d'utiliser l'instruction del.

### Exemple

```python
dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
del dict['Name'] # remove entry with key 'Name'
dict.clear()     # remove all entries in dict
del dict        # delete entire dictionary

print("dict['Age']:", dict['Age'])
print("dict['School']:", dict['School'])
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
dict['Age']:
Traceback (most recent call last):
    File "test.py", line 8, in <module>
        print("dict['Age']:", dict['Age'])
TypeError: 'type' object is unsubscriptable
```

__Remarque__ : Une exception est levée car après ```del dict```, le dictionnaire n'existe plus.
