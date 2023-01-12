Un modèle définit un algorithme de base dans une classe de base à l'aide d'une opération abstraite dont les sous-classes surchargent le comportement concret. Le modèle de gabarit conserve les grandes lignes de l'algorithme dans une méthode distincte. Cette méthode est appelée méthode modèle.

Voici les différentes caractéristiques du modèle de template :

- Elle définit le squelette de l'algorithme dans une opération.
- Elle comprend des sous-classes, qui redéfinissent certaines étapes d'un algorithme.

```python

class MakeMeal:

    def prepare(self): pass
    def cook(self): pass
    def eat(self): pass

    def go(self):
        self.prepare()
        self.cook()
        self.eat()

class MakePizza(MakeMeal):
    def prepare(self):
        print("Prepare Pizza")

    def cook(self):
        print("Cook Pizza")

    def eat(self):
        print("Eat Pizza")

class MakeTea(MakeMeal):
    def prepare(self):
        print("Prepare Tea")

    def cook(self):
        print("Cook Tea")

    def eat(self):
        print("Eat Tea")

makePizza = MakePizza()
makePizza.go()

print(25 * "+")

makeTea = MakeTea()
makeTea.go()
```

## Réponse

Le programme ci-dessus génère la réponse suivante :

```bash
Prepare Pizza
Cook Pizza
Eat Pizza
+++++++++++++++++++++++++
Prepare Tea
Cook Tea
Eat Tea
```

### Explication

Ce code crée un modèle pour préparer un repas. Ici, chaque paramètre représente l'attribut pour créer une partie du repas comme le thé, la pizza, etc.

La sortie représente la visualisation des attributs.
