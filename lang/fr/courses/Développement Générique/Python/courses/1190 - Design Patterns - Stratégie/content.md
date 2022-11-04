Le modèle de stratégie est un type de modèle comportemental. L'objectif principal du modèle de stratégie est de permettre au client de choisir parmi différents algorithmes ou procédures pour accomplir la tâche spécifiée. Il est possible d'intervertir différents algorithmes sans aucune complication pour la tâche mentionnée.

Ce modèle peut être utilisé pour améliorer la flexibilité lors de l'accès à des ressources externes.

## Comment mettre en œuvre le modèle de stratégie ?

Le programme ci-dessous permet de mettre en œuvre le modèle de stratégie.

```python
import types

class StrategyExample:
    def __init__(self, func = None):
        self.name = 'Strategy Example 0'
        if func is not None:
            self.execute = types.MethodType(func, self)

    def execute(self):
        print(self.name)

def execute_replacement1(self): 
    print(self.name + 'from execute 1')

def execute_replacement2(self):
    print(self.name + 'from execute 2')

if __name__ == '__main__':
    strat0 = StrategyExample()
    strat1 = StrategyExample(execute_replacement1)
    strat1.name = 'Strategy Example 1'
    strat2 = StrategyExample(execute_replacement2)
    strat2.name = 'Strategy Example 2'
    strat0.execute()
    strat1.execute()
    strat2.execute()
```

### Résultat

Le programme ci-dessus génère la réponse suivante :

```bash
Strategy Example 0
Strategy Example 1from execute 1
Strategy Example 2from execute 2
```

### Explication

Il fournit une liste de stratégies à partir des fonctions, qui exécutent la sortie. L'objectif principal de ce modèle de comportement est le comportement.
