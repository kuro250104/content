Model View Controller est le modèle de conception le plus couramment utilisé. Les développeurs trouvent qu'il est facile de mettre en œuvre ce modèle de conception.

Voici l'architecture de base du Modèle Vue Contrôleur :

![architecture de base du Modèle Vue Contrôleur](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/Python/courses/0820%20-%20Patterns%20-%20Model%20View%20Controller/images/image1.jpg)

Voyons maintenant comment fonctionne cette structure.

## Modèle

Il consiste en une logique d'application pure, qui interagit avec la base de données. Il comprend toutes les informations permettant de représenter les données à l'utilisateur final.

## Vue

La vue représente les fichiers HTML, qui interagissent avec l'utilisateur final. Elle représente les données du modèle pour l'utilisateur.

## Contrôleur

Il agit comme un intermédiaire entre la vue et le modèle. Il écoute les événements déclenchés par la vue et interroge le modèle à ce sujet.

## Code Python

Considérons un objet de base appelé "Person" et créons un modèle de conception MVC.

### Model.py

```python
import json

class Person(object):
    def __init__(self, first_name = None, last_name = None):
        self.first_name = first_name
        self.last_name = last_name
    #returns Person name, ex: John Doe
    def name(self):
        return ("%s %s" % (self.first_name,self.last_name))
            
    @classmethod
    #returns all people inside db.txt as list of Person objects
    def getAll(self):
        database = open('db.txt', 'r')
        result = []
        json_list = json.loads(database.read())
        for item in json_list:
            item = json.loads(item)
            person = Person(item['first_name'], item['last_name'])
            result.append(person)
        return result
```

Il fait appel à une méthode qui récupère tous les enregistrements de la table Personne dans la base de données. Les enregistrements sont présentés au format JSON.

### Vue

Il affiche tous les enregistrements récupérés dans le modèle. La vue n'interagit jamais avec le modèle ; le contrôleur fait ce travail (communication avec le modèle et la vue).

```python
from model import Person
def showAllView(list):
    print('In our db we have %i users. Here they are:' % len(list))
    for item in list:
        print(item.name())
def startView():
    print('MVC - the simplest example')
    print('Do you want to see everyone in my db?[y/n]')
def endView():
    print('Goodbye!')
```

### Contrôleur

Le contrôleur interagit avec le modèle par le biais de la méthode ```getAll()``` qui récupère tous les enregistrements affichés à l'utilisateur final.

```python
from model import Person
import view

def showAll():
    #gets list of all Person objects
    people_in_db = Person.getAll()
    #calls view
    return view.showAllView(people_in_db)

def start():
    view.startView()
    input = raw_input()
    if input == 'y':
        return showAll()
    else:
        return view.endView()

if __name__ == "__main__":
    #running controller function
    start()
```
