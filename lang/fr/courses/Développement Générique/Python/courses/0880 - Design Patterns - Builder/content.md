Le modèle Builder est un modèle de conception unique qui aide à construire des objets complexes à l'aide d'objets simples et utilise une approche algorithmique. Ce modèle de conception entre dans la catégorie des modèles de création. Dans ce modèle de conception, une classe de constructeur construit l'objet final en suivant une procédure étape par étape. Ce constructeur est indépendant des autres objets.

## Avantages du modèle Builder

- Il fournit une séparation claire et une couche unique entre la construction et la représentation d'un objet spécifique créé par la classe.
- Il permet un meilleur contrôle du processus de construction du modèle créé.
- Il donne le scénario parfait pour changer la représentation interne des objets.

## Comment mettre en œuvre le modèle builder ?

Dans cette section, nous allons apprendre à mettre en œuvre le modèle builder.

```python
class Director:
    __builder = None

    def setBuilder(self, builder):
        self.__builder = builder

    def getCar(self):
        car = Car()

        # First goes the body
        body = self.__builder.getBody()
        car.setBody(body)

        # Then engine
        engine = self.__builder.getEngine()
        car.setEngine(engine)

        # And four wheels
        i = 0
        while i < 4:
            wheel = self.__builder.getWheel()
                car.attachWheel(wheel)
            i += 1
        return car

# The whole product
class Car:
    def __init__(self):
        self.__wheels = list()
        self.__engine = None
        self.__body = None

    def setBody(self, body):
        self.__body = body

    def attachWheel(self, wheel):
        self.__wheels.append(wheel)

    def setEngine(self, engine):
        self.__engine = engine

    def specification(self):
        print("body: %s" % self.__body.shape)
        print("engine horsepower: %d" % self.__engine.horsepower)
        print("tire size: %d\'" % self.__wheels[0].size)

class Builder:
    def getWheel(self): pass
    def getEngine(self): pass
    def getBody(self): pass

class JeepBuilder(Builder):

    def getWheel(self):
        wheel = Wheel()
        wheel.size = 22
        return wheel

    def getEngine(self):
        engine = Engine()
        engine.horsepower = 400
        return engine

    def getBody(self):
        body = Body()
        body.shape = "SUV"
        return body

# Car parts
class Wheel:
    size = None

class Engine:
    horsepower = None

class Body:
    shape = None

def main():
    jeepBuilder = JeepBuilder() # initializing the class
    
    director = Director()
    
    # Build Jeep
    print "Jeep"
    director.setBuilder(jeepBuilder)
    jeep = director.getCar()
    jeep.specification()
    print("")

if __name__ == "__main__":
    main()
```

### Résultat

Le programme ci-dessus génère le résultat suivant :

```bash
Jeepbody: SUV
engine horsepower: 400
tire size: 22'
```
