La gestion des exceptions est également un critère essentiel des modèles de conception. Une exception est une erreur qui se produit pendant l'exécution d'un programme. Lorsqu'une erreur particulière se produit, il est important de générer une exception. Cela permet de limiter les plantages du programme.

## Pourquoi utiliser des exceptions ?

Les exceptions sont des moyens pratiques de gérer les erreurs et les conditions spéciales dans un programme. Lorsqu'un utilisateur pense que le code spécifié peut produire une erreur, il est important d'utiliser la gestion des exceptions..

### Exemple - Division par zéro

```python
import sys

randomList = ['a', 0, 2]

for entry in randomList:
    try:
        print("The entry is", entry)
        r = 1/int(entry)
        break
    except:
        print("Oops!",sys.exc_info()[0],"occured.")
        print("Next entry.")
        print()
print("The reciprocal of", entry, "is",r)
```

### Réponse

Le programme ci-dessus génère la réponse suivante :

```bash
('The entry is', 'a')
('Oops!', <type 'exceptions.ZeroDivisionError'>, 'occured.')
Next entry.
()
('The entry is', 2)
('The reciprocal of', 2, 'is', 0)
```

### Levée d'exceptions

En programmation Python spécifiquement, les exceptions sont levées lorsque l'erreur correspondante du code se produit au moment de l'exécution. Ces exceptions peuvent être levées de manière forcée à l'aide du mot-clé ```raise```.

### Syntaxe

```bash
raise KeyboardInterrupt
Traceback (most recent call last):
...
KeyboardInterrupt
```
