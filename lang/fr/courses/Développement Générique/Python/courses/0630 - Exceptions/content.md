Python fournit deux fonctionnalités très importantes pour gérer toute erreur inattendue dans vos programmes Python et pour ajouter des capacités de débogage dans ceux-ci.

- **Gestion des exceptions** - Ce sujet sera traité dans ce cours. Voici une liste des exceptions standard disponibles en Python - Standard Exceptions.
- **Assertions**.

## Exceptions standards

Voici une liste des exceptions standard disponibles en Python :

- ```Exception``` : Classe de base pour toutes les exceptions.
- ```StopIteration``` : Levée lorsque la méthode ```next()``` d'un itérateur ne pointe vers aucun objet.
- ```SystemExit``` : Levée par la fonction ```sys.exit()```.
- ```StandardError``` : Classe de base pour toutes les exceptions intégrées sauf StopIteration et SystemExit.
- ```ArithmeticError``` : Classe de base pour toutes les erreurs qui se produisent lors de calculs numériques.
- ```OverflowError``` : S'affiche lorsqu'un calcul dépasse la limite maximale pour un type numérique.
- ```FloatingPointError``` : Levée lorsqu'un calcul en virgule flottante échoue.
- ```ZeroDivisonError``` : Levée lorsque la division ou le modulo par zéro a lieu pour tous les types numériques.
- ```AssertionError``` : Levée en cas d'échec de l'instruction Assert.
- ```AttributeError``` : Levée en cas d'échec de la référence ou de l'affectation d'un attribut.
- ```EOFError``` : Évoquée lorsqu'il n'y a aucune entrée provenant de la fonction ```raw_input()``` ou ```input()``` et que la fin du fichier est atteinte.
- ```ImportError``` : S'affiche lorsqu'une déclaration d'importation échoue.
- ```KeyboardInterrupt``` : Levée lorsque l'utilisateur interrompt l'exécution du programme, généralement en appuyant sur Ctrl+c.
- ```LookupError``` : Classe de base pour toutes les erreurs de consultation.
- ```IndexError``` : Levée lorsqu'un index n'est pas trouvé dans une séquence.
- ```KeyError``` : Levée lorsque la clé spécifiée n'est pas trouvée dans le dictionnaire.
- ```NameError``` : Levée lorsqu'un identifiant n'est pas trouvé dans l'espace de noms local ou global.
- ```UnboundLocalError``` : Lancée lorsqu'on essaie d'accéder à une variable locale dans une fonction ou une méthode mais qu'aucune valeur ne lui a été attribuée.
- ```EnvironmentError``` : Classe de base pour toutes les exceptions qui se produisent en dehors de l'environnement Python.
- ```IOError``` : Levée lorsqu'une opération d'entrée/sortie échoue, comme l'instruction print ou la fonction ```open()``` lorsqu'on essaie d'ouvrir un fichier qui n'existe pas.
- ```OSError``` : Levée pour les erreurs liées au système d'exploitation.
- ```SyntaxError``` : S'affiche lorsqu'il y a une erreur dans la syntaxe Python.
- ```IndentationError``` : S'affiche lorsque l'indentation n'est pas spécifiée correctement.
- ```SystemError``` : Levée lorsque l'interpréteur trouve un problème interne, mais lorsque cette erreur est rencontrée, l'interpréteur Python ne sort pas.
- ```SystemExit``` : soulevé lorsque l'interpréteur Python est quitté en utilisant la fonction sys.exit(). Si elle n'est pas gérée dans le code, elle provoque la sortie de l'interpréteur.
- ```TypeError``` : Levée lorsqu'une opération ou une fonction est tentée alors qu'elle n'est pas valide pour le type de données spécifié.
- ```ValueError``` : Lancé lorsque la fonction intégrée pour un type de données a le type d'arguments valide, mais les arguments ont des valeurs invalides spécifiées.
- ```RuntimeError``` : Levée lorsqu'une erreur générée n'entre dans aucune catégorie.
- ```NotImplementedError``` : Lancée lorsqu'une méthode abstraite qui doit être implémentée dans une classe héritée n'est pas réellement implémentée.

## Assertions en Python

Une assertion est un contrôle d'intégrité que vous pouvez activer ou désactiver lorsque vous avez terminé de tester le programme.

- La façon la plus simple de penser à une assertion est de la comparer à une instruction ```raise-if``` (ou, pour être plus précis, une instruction ```raise-if-not```). Une expression est testée, et si le résultat est faux, une exception est levée.
- Les assertions sont exécutées par l'instruction ```assert```, le mot-clé le plus récent de Python, introduit dans la version 1.5.
- Les programmeurs placent souvent les assertions au début d'une fonction pour vérifier la validité des entrées, et après un appel de fonction pour vérifier la validité des sorties.

## L'instruction assert

Lorsqu'il rencontre une instruction ```assert```, Python évalue l'expression qui l'accompagne, en espérant qu'elle soit vraie. Si l'expression est fausse, Python lève une exception AssertionError.
La syntaxe de l'instruction ```assert``` est :

```python
assert Expression[, Arguments]
```

Si l'assertion échoue, Python utilise ```ArgumentExpression``` comme argument pour l'```AssertionError```. Les exceptions ```AssertionError``` peuvent être attrapées et traitées comme toute autre exception, à l'aide de l'instruction ```try-except```. Si elles ne sont pas traitées, elles mettent fin au programme et produisent un retour de trace.

### Exemple

Voici une fonction qui convertit une température donnée des degrés Kelvin en degrés Fahrenheit. Étant donné que 0° K est la température la plus basse possible, la fonction s'arrête si elle voit une température négative :

```python
def KelvinToFahrenheit(Temperature):
    assert (Temperature >= 0), "Colder than absolute zero!"
    return ((Temperature-273)*1.8)+32

print(KelvinToFahrenheit(273))
print(int(KelvinToFahrenheit(505.78)))
print(KelvinToFahrenheit(-5))
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
32.0
451
Traceback (most recent call last):
File "test.py", line 9, in <module>
print(KelvinToFahrenheit(-5))
File "test.py", line 4, in KelvinToFahrenheit
assert (Temperature >= 0), "Colder than absolute zero!"
AssertionError: Colder than absolute zero!
```

## Qu'est-ce qu'une exception ?

Une exception est un événement qui se produit pendant l'exécution d'un programme et qui perturbe le déroulement normal des instructions du programme. En général, lorsqu'un script Python rencontre une situation à laquelle il ne peut faire face, il lève une exception. Une exception est un objet Python qui représente une erreur.

Lorsqu'un script Python lève une exception, il doit la traiter immédiatement, sinon il se termine et quitte le programme.

## Gérer une exception

Si vous avez du code suspect susceptible de lever une exception, vous pouvez défendre votre programme en plaçant le code suspect dans un bloc ```try:```. Après le bloc ```try:```, incluez une instruction ```except:```, suivie d'un bloc de code qui traite le problème de la manière la plus élégante possible.

### Syntaxe

Voici la syntaxe simple des blocs ```try....except...else``` :

```python
try:
    # You do your operations here
    # ......................
except ExceptionI:
    # If there is ExceptionI, then execute this block.
except ExceptionII:
    # If there is ExceptionII, then execute this block.
    # ......................
else:
    # If there is no exception then execute this block.
```

Voici quelques points importants concernant la syntaxe mentionnée ci-dessus :

- Une seule instruction ```try``` peut avoir plusieurs instructions ```except```. Cela s'avère utile lorsque le bloc ```try``` contient des instructions qui peuvent lancer différents types d'exceptions.
- Vous pouvez également fournir une clause ```except``` générique, qui gère toutes les exceptions.
- Après la ou les clauses ```except```, vous pouvez inclure une clause ```else```. Le code du bloc ```else``` s'exécute si le code du bloc ```try``` ne lève pas d'exception.
- Le bloc ```else``` est un bon endroit pour le code qui n'a pas besoin de la protection du bloc ```try:```.

### Exemple

Cet exemple ouvre un fichier, écrit son contenu dans le fichier et s'en sort avec élégance car il n'y a aucun problème :

```python
try:
    fh = open("testfile", "w")
    fh.write("This is my test file for exception handling!!")
except IOError:
    print("Error: can\'t find file or read data")
else:
    print("Written content in the file successfully")
    fh.close()
```

On obtient ainsi le résultat suivant :

```python
Written content in the file successfully
```

### Exemple

Cet exemple tente d'ouvrir un fichier pour lequel vous n'avez pas les droits d'écriture, ce qui entraîne une exception.

```python
try:
    fh = open("testfile", "r")
    fh.write("This is my test file for exception handling!!")
except IOError:
    print("Error: can\'t find file or read data")
else:
    print("Written content in the file successfully")
```

On obtient ainsi le résultat suivant :

```bash
Error: can't find file or read data
```

## La clause except sans exception

Vous pouvez également utiliser l'instruction ```except``` sans exception définie comme suit

```python
try:
    # You do your operations here
    # ......................
except:
    # If there is any exception, then execute this block.
    # ......................
else:
    # If there is no exception then execute this block.
```

Ce type d'instruction ```try-except``` capture toutes les exceptions qui se produisent. L'utilisation de ce type d'instruction ```try-except``` n'est cependant pas considérée comme une bonne pratique de programmation, car elle permet d'attraper toutes les exceptions mais ne permet pas au programmeur d'identifier la cause première du problème qui peut survenir.

## La clause except avec plusieurs exceptions

Vous pouvez également utiliser la même instruction ```except``` pour traiter plusieurs exceptions, comme suit :

```python
try:
    # Réalisation de vos opérations ici
    # ......................
except(Exception1[, Exception2[,...ExceptionN]]]):
    # S'il y a une exception qui est levée depuis la liste, 
    # alors ce bloc s'exécute
    # ......................
else:
    # S'il n'y a pas d'exception one xécute ce bloc
```

## La clause try-finally

Vous pouvez utiliser un bloc ```finally:``` avec un bloc ```try:```. Le bloc ```finally:``` est un endroit où placer tout code qui doit être exécuté, que le bloc ```try``` ait soulevé une exception ou non. La syntaxe de l'instruction ```try-finally``` est la suivante :

```python
try:
    # Réalisation de vos opérations ici
    # ......................
    # Une seule exception fait tout sauter
finally:
    # Bloc étant toujours exécuté, quoi qu'il arrive
    # ......................
```

__Remarque__ : Vous pouvez fournir une ou plusieurs clauses ```except```, ou une clause finally, mais pas les deux. Vous ne pouvez pas utiliser la clause ```else``` en même temps que la clause ```finally```.

### Exemple

```python
try:
    fh = open("testfile", "w")
    fh.write("This is my test file for exception handling!!")
finally:
    print("Error: can\'t find file or read data")
    fh.close()
```

Si vous n'avez pas les droits pour ouvrir le fichier en mode écriture, cela produira le résultat suivant :

```bash
Error: can't find file or read data
```

Le même exemple peut être écrit plus proprement comme suit :

```python
try:
    fh = open("testfile", "w")
    try:
        fh.write("This is my test file for exception handling!!")
    finally:
        print ("Going to close the file")
        fh.close()
except IOError:
    print ("Error: can\'t find file or read data")
```

On obtient ainsi le résultat suivant :

```bash
Going to close the file
```

Lorsqu'une exception est levée dans le bloc ```try```, l'exécution passe immédiatement au bloc ```finally```. Après l'exécution de toutes les instructions du bloc ```finally```, l'exception est à nouveau levée et traitée dans les instructions ```except```, si elles sont présentes dans la couche supérieure suivante de l'instruction ```try-except```.

## Argument d'une exception

Une exception peut avoir un argument, qui est une valeur donnant des informations supplémentaires sur le problème. Le contenu de l'argument varie selon l'exception. Vous capturez l'argument d'une exception en fournissant une variable dans la clause ```except``` comme suit :

```python
try:
    # Réalisation de vos opérations ici
    # ......................
except ExceptionType as Argument:
    # Vous pouvez afficher la valeur de Argument ici
```

Si vous écrivez le code pour traiter une seule exception, vous pouvez faire suivre le nom de l'exception par une variable dans l'instruction ```except```. Si vous traitez plusieurs exceptions, vous pouvez faire suivre le tuple de l'exception par une variable.

Cette variable reçoit la valeur de l'exception contenant principalement la cause de l'exception. La variable peut recevoir une valeur unique ou plusieurs valeurs sous la forme d'un tuple. Ce tuple contient généralement la chaîne d'erreur, le numéro d'erreur et l'emplacement de l'erreur.

### Exemple

Voici un exemple pour une seule exception :

```python
# Define a function here.
def temp_convert(var):
    try:
        return int(var)
    except ValueError as Argument:
        print("The argument does not contain numbers\n", Argument)

# Call above function here.
temp_convert("xyz")
This produces the following result −
The argument does not contain numbers
invalid literal for int() with base 10: 'xyz'
```

## Levée d'une exception

Vous pouvez lever des exceptions de plusieurs façons en utilisant l'instruction ```raise```. La syntaxe générale de l'instruction ```raise``` est la suivante :

### Syntaxe

```python
raise [Exception [, args [, traceback]]]
```

Ici, Exception est le type d'exception (par exemple, NameError) et argument est une valeur pour l'argument d'exception. L'argument est facultatif ; s'il n'est pas fourni, l'argument exception est None.

Le dernier argument, ```traceback```, est également facultatif (et rarement utilisé en pratique), et s'il est présent, il s'agit de l'objet ```traceback``` utilisé pour l'exception.

### Exemple

Une exception peut être une chaîne de caractères, une classe ou un objet. La plupart des exceptions que le noyau Python lève sont des classes, avec un argument qui est une instance de la classe. Définir de nouvelles exceptions est assez facile et peut être fait comme suit :

```python
def functionName( level ):
    if level <1:
        raise Exception(level)
        # The code below to this would not be executed
        # if we raise the exception
    return level
```

__Remarque__ : Pour capturer une exception, la clause ```except``` doit faire référence à la même exception lancée, soit sous forme d'objet de classe, soit sous forme de simple chaîne de caractères. Par exemple, pour capturer l'exception ci-dessus, nous devons écrire la clause ```except``` comme suit :

```python
try:
    # Logique métier ici...
except Exception as e:
    # Gestion des exception ici en utilisant e.args...
else:
    # Le reste du code ici...
```

L'exemple suivant illustre l'utilisation de la levée d'une exception :

```python
def functionName( level ):
    if level <1:
        raise Exception(level)
        # The code below to this would not be executed
        # if we raise the exception
    return level

try:
    l = functionName(-10)
    print("level = ", l)
except Exception as e:
    print("error in level argument", e.args[0])
```

Cela donnera le résultat suivant :

```bash
error in level argument -10
```

## Exceptions définies par l'utilisateur

Python vous permet également de créer vos propres exceptions en dérivant des classes à partir des exceptions standards intégrées.

Voici un exemple lié à ```RuntimeError```. Ici, une classe est créée qui est sous-classée de ```RuntimeError```. Cette classe est utile lorsque vous devez afficher des informations plus spécifiques lorsqu'une exception est détectée.

Dans le bloc ```try```, l'exception définie par l'utilisateur est levée et attrapée dans le bloc ```except```. La variable e est utilisée pour créer une instance de la classe ```Networkerror```.

```python
class Networkerror(RuntimeError):
    def __init__(self, arg):
        self.args = arg
# So once you have defined the above class, you can raise the exception as follows −
try:
    raise Networkerror("Bad hostname")
except Networkerror,e:
    print(e.args)
```
