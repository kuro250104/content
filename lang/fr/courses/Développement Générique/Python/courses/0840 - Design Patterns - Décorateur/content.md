Le modèle Decorator permet à l'utilisateur d'ajouter une nouvelle fonctionnalité à un objet existant sans en modifier la structure. Ce type de modèle de conception fait partie des modèles structurels, car il agit comme une enveloppe pour une classe existante.

Ce patron crée une classe décoratrice, qui enveloppe la classe originale et fournit une fonctionnalité supplémentaire en conservant la signature des méthodes de la classe.

Le motif d'un patron de décorateur est d'attacher des responsabilités supplémentaires à un objet de manière dynamique.

## Comment implémenter le design pattern decorator ?

Le code mentionné ci-dessous est une démonstration simple de l'implémentation du design pattern decorator en Python. L'illustration implique la démonstration d'un café sous la forme d'une classe. La classe de café créée est une abstraite, ce qui signifie qu'elle ne peut pas être instanciée.

```python
import six
from abc import ABCMeta

@six.add_metaclass(ABCMeta)
class Abstract_Coffee(object):
    def get_cost(self):
        pass

    def get_ingredients(self):
        pass

    def get_tax(self):
        return 0.1 * self.get_cost()

class Concrete_Coffee(Abstract_Coffee):
    def get_cost(self):
        return 1.00

    def get_ingredients(self):
        return 'coffee'

@six.add_metaclass(ABCMeta)
class Abstract_Coffee_Decorator(Abstract_Coffee):
    def __init__(self,decorated_coffee):
        self.decorated_coffee = decorated_coffee

    def get_cost(self):
        return self.decorated_coffee.get_cost()

    def get_ingredients(self):
        return self.decorated_coffee.get_ingredients()

class Sugar(Abstract_Coffee_Decorator):
    def __init__(self,decorated_coffee):
        Abstract_Coffee_Decorator.__init__(self,decorated_coffee)

    def get_cost(self):
        return self.decorated_coffee.get_cost()

    def get_ingredients(self):
        return self.decorated_coffee.get_ingredients() + ', sugar'

class Milk(Abstract_Coffee_Decorator):
    def __init__(self,decorated_coffee):
        Abstract_Coffee_Decorator.__init__(self,decorated_coffee)

    def get_cost(self):
        return self.decorated_coffee.get_cost() + 0.25

    def get_ingredients(self):
        return self.decorated_coffee.get_ingredients() + ', milk'

class Vanilla(Abstract_Coffee_Decorator):
    def __init__(self,decorated_coffee):
        Abstract_Coffee_Decorator.__init__(self,decorated_coffee)

    def get_cost(self):
        return self.decorated_coffee.get_cost() + 0.75

    def get_ingredients(self):
        return self.decorated_coffee.get_ingredients() + ', vanilla'
```

L'implémentation de la classe abstraite du café est faite dans un fichier séparé comme mentionné ci-dessous :

```python
import coffeeshop

myCoffee = coffeeshop.Concrete_Coffee()
print('Ingredients: ' + myCoffee.get_ingredients()+
    '; Cost: ' + str(myCoffee.get_cost()) + '; sales tax = ' + str(myCoffee.get_tax()))

myCoffee = coffeeshop.Milk(myCoffee)
print('Ingredients: ' + myCoffee.get_ingredients()+
    '; Cost: '+str(myCoffee.get_cost()) + '; sales tax = ' + str(myCoffee.get_tax()))

myCoffee = coffeeshop.Vanilla(myCoffee)
print('Ingredients: ' + myCoffee.get_ingredients()+
    '; Cost: ' + str(myCoffee.get_cost()) + '; sales tax = ' + str(myCoffee.get_tax()))

myCoffee = coffeeshop.Sugar(myCoffee)
print('Ingredients: '+myCoffee.get_ingredients()+
    '; Cost: ' + str(myCoffee.get_cost()) + '; sales tax = ' + str(myCoffee.get_tax()))
```

### Résultat

Le programme ci-dessus génère le résultat suivant :

```bash
Ingredients: coffee; Cost; 1.0; sales tax = 0.1
Ingredients: coffee, milk; Cost; 1.25; sales tax = 0.125
Ingredients: coffee, milk, vanilla; Cost; 2.0; sales tax = 0.2
Ingredients: coffee, milk, vanilla, sugar; Cost; 2.0; sales tax = 0.2
```
