Le modèle Adapter fonctionne comme un pont entre deux interfaces incompatibles. Ce type de modèle de conception fait partie des modèles structurels car il combine les capacités de deux interfaces indépendantes.

Ce modèle implique une classe unique, qui est responsable de l'union des fonctionnalités d'interfaces indépendantes ou incompatibles. Un exemple concret pourrait être le cas d'un lecteur de carte, qui agit comme un adaptateur entre la carte mémoire et un ordinateur portable. Vous branchez la carte mémoire dans le lecteur de cartes et le lecteur de cartes dans l'ordinateur portable afin que la carte mémoire puisse être lue par l'ordinateur portable.

Le design pattern Adapter permet de faire fonctionner des classes ensemble. Il convertit l'interface d'une classe en une autre interface en fonction des besoins. Le modèle comprend une spéciation, un polymorphisme qui désigne un nom et des formes multiples. Disons pour une classe de forme qui peut être utilisée selon les exigences recueillies.

Il existe deux types de modèles Adapter :

- **Modèle d’objet Adapter** : Ce modèle de conception repose sur l'implémentation d'objets. C'est pourquoi on l'appelle le modèle d’objet Adapter.
- **Modèle de classe Adapter** : Il s'agit d'une autre façon de mettre en œuvre le modèle de classe Adapter. Le modèle peut être mis en œuvre en utilisant des héritages multiples.

## Comment mettre en œuvre le modèle Adapter ?

Voyons maintenant comment mettre en œuvre le modèle Adapter.

```python
class EuropeanSocketInterface:
    def voltage(self): pass

    def live(self): pass
    def neutral(self): pass
    def earth(self): pass

# Adaptee
class Socket(EuropeanSocketInterface):
    def voltage(self):
        return 230

        def live(self):
        return 1

    def neutral(self):
        return -1

    def earth(self):
        return 0

# Target interface
class USASocketInterface:
    def voltage(self): pass
    def live(self): pass
    def neutral(self): pass

# The Adapter
class Adapter(USASocketInterface):
    __socket = None
    def __init__(self, socket):
        self.__socket = socket

    def voltage(self):
        return 110

    def live(self):
        return self.__socket.live()

    def neutral(self):
        return self.__socket.neutral()

# Client
class ElectricKettle:
    __power = None

    def __init__(self, power):
        self.__power = power

    def boil(self):
        if self.__power.voltage() > 110:
            print("Kettle on fire!")
        else:
            if self.__power.live() == 1 and \
                self.__power.neutral() == -1:
                print("Coffee time!")
            else:
                print("No power.")

def main():
    # Plug in
    socket = Socket()
    adapter = Adapter(socket)
    kettle = ElectricKettle(adapter)

    # Make coffee
    kettle.boil()

    return 0

if __name__ == "__main__":
    main()
```

### Résultat

Le programme ci-dessus génère le résultat suivant :

```bash
Coffee time!
```

### Explication

Le code comprend une interface adaptateur avec divers paramètres et attributs. Il inclut l'Adaptee avec l'interface Target qui implémente tous les attributs et affiche la sortie comme visible.
