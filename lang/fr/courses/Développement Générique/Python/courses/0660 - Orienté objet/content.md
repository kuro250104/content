Le modèle orienté objet est le modèle le plus couramment utilisé. Ce modèle se retrouve dans presque tous les langages de programmation.

## Comment mettre en œuvre le modèle orienté objet ?

Voyons maintenant comment mettre en œuvre le modèle orienté objet.

```python
class Parrot:
    # class attribute
    species = "bird"
        
    # instance attribute
    def __init__(self, name, age):
        self.name = name
        self.age = age

# instantiate the Parrot class
blu = Parrot("Blu", 10)
woo = Parrot("Woo", 15)

# access the class attributes
print("Blu is a {}".format(blu.__class__.species))
print("Woo is also a {}".format(woo.__class__.species))

# access the instance attributes
print("{} is {} years old".format(blu.name, blu.age))
print("{} is {} years old".format(woo.name, woo.age))
```

### Réponse

Le programme ci-dessus génère la réponse suivante :

```bash
Blu is a bird
Woo is also a bird
Blu is 10 years old
Woo is 15 years old
```

### Explication

Le code comprend des attributs de classe et d'instance, qui sont imprimés en fonction des besoins de la réponse. Plusieurs caractéristiques font partie du modèle orienté objet. Ces caractéristiques sont expliquées dans le chapitre suivant.
