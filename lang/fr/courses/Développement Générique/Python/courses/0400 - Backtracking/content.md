Le retour en arrière est une forme de récursion. Mais elle implique de choisir une seule option parmi toutes les possibilités. Nous commençons par choisir une option et revenons en arrière si nous arrivons à un état où nous concluons que cette option spécifique ne donne pas la solution requise. Nous répétons ces étapes en passant par chaque option disponible jusqu'à ce que nous obtenions la solution souhaitée.

Voici un exemple de recherche de tous les ordres d'arrangement possibles d'un ensemble de lettres donné. Lorsque nous choisissons une paire, nous appliquons le retour en arrière pour vérifier si cette paire exacte a déjà été créée ou non. Si elle n'a pas déjà été créée, la paire est ajoutée à la liste des réponses, sinon elle est ignorée.

## Example

```python
def permute(list, s):
    if list == 1:
        return s
    else:
        return [ 
            y + x
            for y in permute(1, s)
            for x in permute(list - 1, s)
        ]
print(permute(1, ["a","b","c"]))
print(permute(2, ["a","b","c"]))
```

## Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
['a', 'b', 'c']
['aa', 'ab', 'ac', 'ba', 'bb', 'bc', 'ca', 'cb', 'cc']
```