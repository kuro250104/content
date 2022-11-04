Dans ce chapitre, nous allons nous concentrer sur les modèles utilisant les concepts orientés objet et leur mise en œuvre en Python. Lorsque nous concevons nos programmes autour de blocs d'instructions, qui manipulent les données autour de fonctions, on parle de programmation orientée procédure. Dans la programmation orientée objet, il existe deux instances principales appelées classes et objets.

## Comment mettre en œuvre les classes et les variables d'objet ?

L'implémentation des classes et des variables d'objet est la suivante :

```python
class Robot:
    population = 0
    
    def __init__(self, name):
        self.name = name
        print("(Initializing {})".format(self.name))
        Robot.population += 1
    
    def die(self):
        print("{} is being destroyed!".format(self.name))
        Robot.population -= 1
        if Robot.population == 0:
            print("{} was the last one.".format(self.name))
        else:
            print("There are still {:d} robots working.".format(
                Robot.population))
   
    def say_hi(self):
        print("Greetings, my masters call me {}.".format(self.name))
    
    @classmethod
    def how_many(cls):
        print("We have {:d} robots.".format(cls.population))
droid1 = Robot("R2-D2")
droid1.say_hi()
Robot.how_many()

droid2 = Robot("C-3PO")
droid2.say_hi()
Robot.how_many()

print("\nRobots can do some work here.\n")

print("Robots have finished their work. So let's destroy them.")
droid1.die()
droid2.die()

Robot.how_many()
```

### Réponse

Le programme ci-dessus génère la réponse suivante :

```bash
(Initializing R2-D2)
Greetings, my masters call me R2-D2.
We have 1 robots.
(Initializing C-3PO)
Greetings, my masters call me C-3PO.
We have 2 robots.

Robots can do some work here

Robots have finished their work. So let's destroy them.
R2-D2 is being destroyed!
There are still 1 robots working.
C-3PO is being destroyed!
C-3PO was the last one.
We have 0 robots.
```

### Explication

Cette illustration permet de démontrer la nature des variables de classe et d'objet.

- La variable "population" appartient à la classe "Robot". C'est pourquoi on la désigne comme une variable de classe ou un objet.
- Ici, nous faisons référence à la variable de classe population comme Robot.population et non comme self.population.