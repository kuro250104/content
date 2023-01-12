Il fournit un module pour les machines à état, qui sont mises en œuvre en utilisant des sous-classes, dérivées d'une classe de machine à état spécifiée. Les méthodes sont indépendantes de l'état et provoquent des transitions déclarées à l'aide de décorateurs.

## Comment mettre en œuvre le modèle d'état ?

L'implémentation de base du modèle d'état est présentée ci-dessous :

```python
class ComputerState(object):

    name = "state"
    allowed = []

    def switch(self, state):
        """ Switch to new state """
        if state.name in self.allowed:
            print('Current:', self, '=> switched to new state', state.name)
            self.__class__ = state
        else:
            print('Current:', self, '=> switching to' ,state.name, 'not possible')

    def __str__(self):
        return self.name

class Off(ComputerState):
    name = "off"
    allowed = ['on']

class On(ComputerState):
    """ State of being powered on and working """
    name = "on"
    allowed = ['off','suspend','hibernate']

class Suspend(ComputerState):
    """ State of being in suspended mode after switched on """
    name = "suspend"
    allowed = ['on']

class Hibernate(ComputerState):
    """ State of being in hibernation after powered on """
    name = "hibernate"
    allowed = ['on']

class Computer(object):
    """ A class representing a computer """

    def __init__(self, model='HP'):
        self.model = model
        # State of the computer - default is off.
        self.state = Off()

    def change(self, state):
        """ Change state """
        self.state.switch(state)

if __name__ == "__main__":
    comp = Computer()
    comp.change(On)
    comp.change(Off)
    comp.change(On)
    comp.change(Suspend)
    comp.change(Hibernate)
    comp.change(On)
    comp.change(Off)
```

### Résultat

Le programme ci-dessus génère le résultat suivant :


```bash
Current: off => switched to new sate on
Current: on => switched to new sate off
Current: off => switched to new sate on
Current: on => switched to new sate suspend
Current: suspend => switching to hibernate not possible
Current: suspend => switched to new sate on
Current: on => switched to new sate off
```
