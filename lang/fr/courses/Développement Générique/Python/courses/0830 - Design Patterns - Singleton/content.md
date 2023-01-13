Ce pattern limite l'instanciation d'une classe à un seul objet. Il s'agit d'un type de pattern de création et implique une seule classe pour créer des méthodes et des objets spécifiés.

Il fournit un point d'accès global à l'instance créée.

## Comment implémenter une classe singleton ?

Le programme suivant démontre l'implémentation de la classe singleton où il imprime les instances créées plusieurs fois.

```python
class Singleton:
    __instance = None
    @staticmethod 
    def getInstance():
        """Static access method."""
        if Singleton.__instance == None:
            Singleton()
        return Singleton.__instance
    def __init__(self):
        """Virtually private constructor."""
        if Singleton.__instance != None:
            raise Exception("This class is a singleton!")
        else:
            Singleton.__instance = self
s = Singleton()
print(s)

s = Singleton.getInstance()
print(s)

s = Singleton.getInstance()
print(s)
```

### Résultat

Le programme ci-dessus génère le résultat suivant :

```bash
<__main__.Singleton instance at 0x018356c0>
<__main__.Singleton instance at 0x018356c0>
<__main__.Singleton instance at 0x018356c0>
```

Le nombre d'instances créées est le même et il n'y a pas de différence dans les objets listés en sortie.
