Le factory pattern fait partie de la catégorie de la liste des patterns de création. Il fournit l'une des meilleures façons de créer un objet. Dans le factory pattern, les objets sont créés sans exposer la logique au client et font référence à l'objet nouvellement créé en utilisant une interface commune.

Les factory patterns sont implémentés en Python en utilisant la méthode factory. Lorsqu'un utilisateur appelle une méthode telle que le passage d'une chaîne de caractères et la valeur de retour comme un nouvel objet est mise en œuvre par la méthode factory. Le type d'objet utilisé dans la méthode factory est déterminé par la chaîne de caractères qui est passée par la méthode.

Dans l'exemple ci-dessous, chaque méthode inclut un objet comme paramètre, qui est implémenté par la méthode factory.

## Comment mettre en œuvre un modèle factory ?

Voyons maintenant comment mettre en œuvre un modèle factory.

```python
class Button(object):
    html = ""
    def get_html(self):
        return self.html

class Image(Button):
    html = "<img></img>"

class Input(Button):
    html = "<input></input>"

class Flash(Button):
    html = "<obj></obj>"

class ButtonFactory():
    def create_button(self, typ):
        targetclass = typ.capitalize()
        return globals()[targetclass]()

button_obj = ButtonFactory()
button = ['image', 'input', 'flash']
for b in button:
    print(button_obj.create_button(b).get_html())
```

La classe button permet de créer les balises html et la page html associée. Le client n'aura pas accès à la logique du code et la sortie représente la création de la page html.

### Résultat

```bash
<img></img>
<input></input>
<obj></obj>
```

### Explication

Le code Python comprend la logique des balises html, qui spécifient une valeur. L'utilisateur final peut jeter un coup d'œil sur le fichier HTML créé par le code Python.
