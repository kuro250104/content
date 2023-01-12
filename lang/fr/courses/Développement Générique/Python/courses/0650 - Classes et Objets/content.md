Python est un langage orienté objet depuis qu'il existe. De ce fait, la création et l'utilisation de classes et d'objets sont très faciles. Ce chapitre vous aidera à devenir un expert dans l'utilisation du support de programmation orienté objet de Python.

Si vous n'avez pas d'expérience préalable de la programmation orientée objet (POO), vous pouvez consulter un cours d'introduction à ce sujet ou au moins un tutoriel quelconque afin de maîtriser les concepts de base.

Cependant, voici une petite introduction à la programmation orientée objet (POO) pour vous aider :

## Aperçu de la terminologie de la POO

- **Classe** : Prototype défini par l'utilisateur pour un objet qui définit un ensemble d'attributs qui caractérisent tout objet de la classe. Les attributs sont des membres de données (variables de classe et variables d'instance) et des méthodes, accessibles via la notation par points.
- **Variable de classe** : Une variable qui est partagée par toutes les instances d'une classe. Les variables de classe sont définies à l'intérieur d'une classe mais en dehors de toute méthode de la classe. Les variables de classe ne sont pas utilisées aussi fréquemment que les variables d'instance.
- **Membre de données** : Variable de classe ou d'instance qui contient des données associées à une classe et à ses objets.
- **Surcharge de fonctions** : L'attribution de plus d'un comportement à une fonction particulière. L'opération effectuée varie en fonction des types d'objets ou d'arguments impliqués.
- **Variable d'instance** : Variable définie à l'intérieur d'une méthode et appartenant uniquement à l'instance actuelle d'une classe.
- **Héritage** : Le transfert des caractéristiques d'une classe à d'autres classes qui en sont dérivées.
- **Instance** : Un objet individuel d'une certaine classe. Un objet ```obj``` qui appartient à la classe Circle, par exemple, est une instance de la classe Circle.
- **Instanciation** : La création d'une instance d'une classe.
- **Méthode** : Un type particulier de fonction qui est défini dans la définition d'une classe.
- **Objet** : Une instance unique d'une structure de données définie par sa classe. Un objet comprend à la fois des membres de données (variables de classe et variables d'instance) et des méthodes.
- **Surcharge d'opérateurs** : L'affectation de plus d'une fonction à un opérateur particulier.

## Création de classes

L'instruction ```class``` crée une nouvelle définition de classe. Le nom de la classe suit immédiatement le mot-clé ```class``` suivi d'un deux-points comme suit :

```python
class ClassName:
    'Optional class documentation string'
    # class_suite
```

- La classe possède une chaîne de documentation, à laquelle on peut accéder via ```ClassName.__doc__```.
- La ```class_suite``` est constituée de toutes les déclarations de composants définissant les membres de la classe, les attributs de données et les fonctions.

### Exemple

Voici un exemple d'une classe Python simple :

```python
class Employee:
    'Common base class for all employees'
    empCount = 0

    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
        Employee.empCount += 1
    
    def displayCount(self):
        print("Total Employee %d" % Employee.empCount)

    def displayEmployee(self):
        print("Name :", self.name,  ", Salary:", self.salary)
```

- La variable ```empCount``` est une variable de classe dont la valeur est partagée entre toutes les instances de a dans cette classe. On peut y accéder sous la forme ```Employee.empCount``` depuis l'intérieur ou l'extérieur de la classe.
- La première méthode ```__init__()``` est une méthode spéciale, appelée constructeur de classe ou méthode d'initialisation, que Python appelle lorsque vous créez une nouvelle instance de cette classe.
- Vous déclarez les autres méthodes de la classe comme des fonctions normales, à l'exception du fait que le premier argument de chaque méthode est ```self```. Python ajoute l'argument self à la liste pour vous ; vous n'avez pas besoin de l'inclure lorsque vous appelez les méthodes.

## Création d'objets d'instance

Pour créer des instances d'une classe, vous appelez la classe à l'aide de son nom et vous lui passez les arguments que sa méthode ```__init__``` accepte.

Cela créerait le premier objet de la classe Employee :

```python
emp1 = Employee("Zara", 2000)
```

Cela créerait un deuxième objet de la classe Employee :

```python
emp2 = Employee("Manni", 5000)
```

## Accès aux attributs

Vous accédez aux attributs de l'objet en utilisant l'opérateur point avec l'objet. On accède à une variable de classe en utilisant le nom de la classe comme suit :

```python
emp1.displayEmployee()
emp2.displayEmployee()
print("Total Employee %d" % Employee.empCount)
```

Maintenant, en mettant tous les concepts ensemble :

```python
#!/usr/bin/python3

class Employee:
    'Common base class for all employees'
    empCount = 0

    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
        Employee.empCount += 1
    
    def displayCount(self):
        print ("Total Employee %d" % Employee.empCount)

    def displayEmployee(self):
        print ("Name :", self.name,  ", Salary:", self.salary)


#This would create first object of Employee class"
emp1 = Employee("Zara", 2000)
#This would create second object of Employee class"
emp2 = Employee("Manni", 5000)
emp1.displayEmployee()
emp2.displayEmployee()
print ("Total Employee %d" % Employee.empCount)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Name : Zara ,Salary: 2000
Name : Manni ,Salary: 5000
Total Employee 2
```

Vous pouvez ajouter, supprimer ou modifier les attributs des classes et des objets à tout moment :

```python
emp1.salary = 7000  # Add an 'salary' attribute.
emp1.name = 'xyz'  # Modify 'age' attribute.
del emp1.salary  # Delete 'age' attribute.
```

Au lieu d'utiliser les instructions normales pour accéder aux attributs, vous pouvez utiliser les fonctions suivantes :

- ```Le getattr(obj, name[, default])``` - pour accéder à l'attribut de l'objet.
- ```La fonction hasattr(obj,name)``` - pour vérifier si un attribut existe ou non.
- ```La fonction setattr(obj,name,value)``` - permet de définir un attribut. Si l'attribut n'existe pas, il sera créé.
- ```La commande delattr(obj, name)``` - permet de supprimer un attribut.

```python
hasattr(emp1, 'salary')    # Returns true if 'salary' attribute exists
getattr(emp1, 'salary')    # Returns value of 'salary' attribute
setattr(emp1, 'salary', 7000) # Set attribute 'salary' at 7000
delattr(emp1, 'salary')    # Delete attribute 'salary'
```

## Attributs de classe intégrés

Chaque classe Python possède les attributs intégrés suivants, auxquels on peut accéder à l'aide de l'opérateur point, comme n'importe quel autre attribut :

- ```__dict__``` - Dictionnaire contenant l'espace de noms de la classe.
- ```__doc__``` - Chaîne de documentation de la classe ou aucune, si elle n'est pas définie.
- ```__name__``` - Nom de la classe.
- ```__module__``` - Nom du module dans lequel la classe est définie. Cet attribut est ```__main__``` en mode interactif.
- ```__bases__``` - Un tuple éventuellement vide contenant les classes de base, dans l'ordre de leur apparition dans la liste des classes de base.

Pour la classe ci-dessus, essayons d'accéder à tous ces attributs :

```python
#!/usr/bin/python3

class Employee:
    'Common base class for all employees'
    empCount = 0

    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
        Employee.empCount += 1
    
    def displayCount(self):
        print ("Total Employee %d" % Employee.empCount)

    def displayEmployee(self):
        print ("Name :", self.name,  ", Salary:", self.salary)

emp1 = Employee("Zara", 2000)
emp2 = Employee("Manni", 5000)
print("Employee.__doc__:", Employee.__doc__)
print("Employee.__name__:", Employee.__name__)
print("Employee.__module__:", Employee.__module__)
print("Employee.__bases__:", Employee.__bases__)
print("Employee.__dict__:", Employee.__dict__ )
```

Voici le résultat de l'exécution du code ci-dessus :

```bash
Employee.__doc__: Common base class for all employees
Employee.__name__: Employee
Employee.__module__: __main__
Employee.__bases__: (<class 'object'>,)
Employee.__dict__: {
    'displayCount': <function Employee.displayCount at 0x0160D2B8>, 
    '__module__': '__main__', '__doc__': 'Common base class for all employees', 
    'empCount': 2, '__init__': 
    <function Employee.__init__ at 0x0124F810>, 'displayEmployee': 
    <function Employee.displayEmployee at 0x0160D300>,
    '__weakref__': 
    <attribute '__weakref__' of 'Employee' objects>, '__dict__': 
    <attribute '__dict__' of 'Employee' objects>
}
```

## Destruction d'objets (Garbage Collection)

Python supprime automatiquement les objets inutiles (types intégrés ou instances de classe) afin de libérer l'espace mémoire. Le processus par lequel Python récupère périodiquement les blocs de mémoire qui ne sont plus utilisés est appelé Garbage Collection.

Le ramasseur d'ordures de Python fonctionne pendant l'exécution du programme et est déclenché lorsque le nombre de références d'un objet atteint zéro. Le nombre de références d'un objet varie en fonction du nombre d'alias qui pointent vers lui.

Le nombre de références d'un objet augmente lorsqu'un nouveau nom lui est attribué ou lorsqu'il est placé dans un conteneur (liste, tuple ou dictionnaire). Le nombre de références d'un objet diminue lorsqu'il est supprimé avec ```del```, que sa référence est réaffectée ou que sa référence sort de la portée. Lorsque le nombre de références d'un objet atteint zéro, Python le récupère automatiquement.

```python
a = 40      # Create object <40>
b = a       # Increase ref. count  of <40> 
c = [b]     # Increase ref. count  of <40> 

del a       # Decrease ref. count  of <40>
b = 100     # Decrease ref. count  of <40> 
c[0] = -1   # Decrease ref. count  of <40>
```

Normalement, vous ne remarquerez pas quand le ramasseur d'ordures détruit une instance orpheline et récupère son espace. Cependant, une classe peut implémenter la méthode spéciale ```__del__()```, appelée destructeur, qui est invoquée lorsque l'instance est sur le point d'être détruite. Cette méthode peut être utilisée pour nettoyer toutes les ressources non-mémoire utilisées par une instance.

### Exemple

Ce destructeur ```__del__()``` imprime le nom de la classe d'une instance qui est sur le point d'être détruite :

```python
#!/usr/bin/python3

class Point:
    def __init__( self, x=0, y=0):
        self.x = x
        self.y = y
    def __del__(self):
        class_name = self.__class__.__name__
        print(class_name, "destroyed")

pt1 = Point()
pt2 = pt1
pt3 = pt1
print (id(pt1), id(pt2), id(pt3))   # prints the ids of the obejcts
del pt1
del pt2
del pt3
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
140338326963984 140338326963984 140338326963984
Point destroyed
```

__Remarque__ : Idéalement, vous devriez définir vos classes dans un fichier séparé, puis les importer dans votre fichier de programme principal à l'aide de l'instruction import.

Dans l'exemple ci-dessus, la définition supposée d'une classe Point est contenue dans point.py et il n'y a pas d'autre code exécutable dans celui-ci.

```python
#!/usr/bin/python3
import point

p1 = point.Point()
```

## Héritage des classes

Au lieu de partir de zéro, vous pouvez créer une classe en la dérivant d'une classe préexistante en indiquant la classe parent entre parenthèses après le nom de la nouvelle classe.

La classe enfant hérite des attributs de sa classe parent, et vous pouvez utiliser ces attributs comme s'ils étaient définis dans la classe enfant. Une classe enfant peut également remplacer les membres de données et les méthodes de la classe parent.

### Syntaxe

Les classes dérivées sont déclarées de la même manière que leur classe mère ; toutefois, une liste des classes de base dont elles héritent est donnée après le nom de la classe :

```python
class SubClassName (ParentClass1[, ParentClass2, ...]):
    'Optional class documentation string'
    # class_suite
```

### Exemple

```python
#!/usr/bin/python3

class Parent:        # define parent class
    parentAttr = 100
    def __init__(self):
        print("Calling parent constructor")

    def parentMethod(self):
        print('Calling parent method')

    def setAttr(self, attr):
        Parent.parentAttr = attr

    def getAttr(self):
        print("Parent attribute :", Parent.parentAttr)

class Child(Parent): # define child class
    def __init__(self):
        print("Calling child constructor")

    def childMethod(self):
        print('Calling child method')

c = Child()          # instance of child
c.childMethod()      # child calls its method
c.parentMethod()     # calls parent's method
c.setAttr(200)       # again call parent's method
c.getAttr()          # again call parent's method
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Calling child constructor
Calling child method
Calling parent method
Parent attribute : 200
```

De la même manière, vous pouvez piloter une classe à partir de plusieurs classes parentes comme suit :

```python
class A:        # define your class A
    # .....

class B:         # define your calss B
    # .....

class C(A, B):   # subclass of A and B
    # .....
```

Vous pouvez utiliser les fonctions ```issubclass()``` ou ```isinstance()``` pour vérifier les relations entre deux classes et instances.

- La fonction booléenne ```issubclass(sub, sup)``` retourne ```True```, si la sous-classe donnée sub est bien une sous-classe de la superclasse sup.
- La fonction booléenne ```isinstance(obj, Class)``` renvoie ```True```, si obj est une instance de la classe Class ou est une instance d'une sous-classe de ```Class```.

## Remplacement des méthodes

Vous pouvez toujours remplacer les méthodes de votre classe parent. L'une des raisons pour lesquelles vous devez remplacer les méthodes de votre parent est que vous pouvez vouloir une fonctionnalité spéciale ou différente dans votre sous-classe.

### Example

```python
#!/usr/bin/python3

class Parent:        # define parent class
    def myMethod(self):
        print ('Calling parent method')

class Child(Parent): # define child class
    def myMethod(self):
        print ('Calling child method')

c = Child()          # instance of child
c.myMethod()         # child calls overridden method
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Calling child method
```


## Méthodes de surcharge de la base

Le tableau suivant répertorie certaines fonctionnalités génériques que vous pouvez surcharger dans vos propres classes :

- ```__init__ ( self [,args...] )``` : Constructeur (avec tous les arguments optionnels)
    - Exemple d'appel : ```obj = className(args)```
- ```__del__( self )``` : Destructeur, supprime un objet
    - Exemple d'appel : ```del obj```
- ```__repr__( self )``` : Représentation sous forme de chaîne évaluable
    - Exemple d'appel : ```repr(obj)```
- ```__str__( self )``` : Représentation de chaîne de caractères imprimable
    - Exemple d'appel : ```str(obj)```
- ```__cmp__ ( self, x )``` : Comparaison d'objets
    - Exemple d'appel : ```cmp(obj, x)```

## Surcharge des opérateurs

Supposons que vous ayez créé une classe Vector pour représenter des vecteurs à deux dimensions. Que se passe-t-il lorsque vous utilisez l'opérateur plus pour les additionner ? Il est fort probable que Python vous engueule.

Vous pourriez toutefois définir la méthode ```__add__``` dans votre classe pour effectuer l'addition de vecteurs et l'opérateur plus se comporterait alors comme prévu :

### Exemple

```python
#!/usr/bin/python3

class Vector:
    def __init__(self, a, b):
        self.a = a
        self.b = b

    def __str__(self):
        return 'Vector (%d, %d)' % (self.a, self.b)
    
    def __add__(self,other):
        return Vector(self.a + other.a, self.b + other.b)

v1 = Vector(2,10)
v2 = Vector(5,-2)
print(v1 + v2)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Vector(7,8)
```

## Masquage de données

Les attributs d'un objet peuvent ou non être visibles en dehors de la définition de la classe. Vous devez nommer les attributs avec un préfixe à double soulignement, et ces attributs ne seront alors pas directement visibles par les personnes extérieures.

### Exemple

```python
#!/usr/bin/python3

class JustCounter:
    __secretCount = 0
    
    def count(self):
        self.__secretCount += 1
        print (self.__secretCount)

counter = JustCounter()
counter.count()
counter.count()
print(counter.__secretCount)
```

Voici le résultat de l'exécution du code ci-dessus :

```bash
1
2
Traceback (most recent call last):
    File "test.py", line 12, in <module>
        print counter.__secretCount
AttributeError: JustCounter instance has no attribute '__secretCount'
```

Python protège ces membres en modifiant en interne le nom pour inclure le nom de la classe. Vous pouvez accéder à ces attributs par ```object._className__attrName```. Si vous remplacez votre dernière ligne par la suivante, cela fonctionne pour vous :

```python
# .........................
print(counter._JustCounter__secretCount)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
1
2
2
```
