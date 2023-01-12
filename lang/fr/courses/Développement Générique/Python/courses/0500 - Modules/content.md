Un module vous permet d'organiser logiquement votre code Python. Le regroupement de code apparenté dans un module rend le code plus facile à comprendre et à utiliser. Un module est un objet Python avec des attributs nommés arbitrairement que vous pouvez lier et référencer.

Plus simplement, un module est un fichier constitué de code Python. Un module peut définir des fonctions, des classes et des variables. Un module peut également inclure du code exécutable.

Exemple

Le code Python d'un module nommé ```aname``` se trouve normalement dans un fichier nommé ```aname```.py. Voici un exemple d'un module simple, ```support.py``` :

```python
def print_func(par):
    print("Hello :", par)
    return
```

## L'instruction import

Vous pouvez utiliser n'importe quel fichier source Python comme module en exécutant une instruction import dans un autre fichier source Python. L'import a la syntaxe suivante :

```python
import module1[, module2[,... moduleN]
```

Lorsque l'interpréteur rencontre une instruction ```import```, il importe le module si celui-ci est présent dans le chemin de recherche. Un chemin de recherche est une liste de répertoires que l'interpréteur recherche avant d'importer un module. Par exemple, pour importer le module hello.py, vous devez placer la commande suivante en haut du script :

```python
#!/usr/bin/python3

# Import module support
import support

# Now you can call defined function that module as follows
support.print_func("Zara")
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Hello : Zara
```

Un module est chargé une seule fois, quel que soit le nombre de fois où il est importé. Cela permet d'éviter que l'exécution du module ne se répète, en cas d'importations multiples.

## L'instruction from ... import

L'instruction from de Python vous permet d'importer des attributs spécifiques d'un module dans l'espace de noms actuel. L'instruction ```from...import``` à la syntaxe suivante :

```python
from modname import name1[, name2[, ... nameN]]
```

Par exemple, pour importer la fonction Fibonacci du module fib, utilisez l'instruction suivante :

```python
#!/usr/bin/python3

# Fibonacci numbers module

def fib(n): # return Fibonacci series up to n
    result = []
    a, b = 0, 1
    while b < n:
        result.append(b)
        a, b = b, a + b
    return result
>>> from fib import fib
>>> fib(100)
[1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
```

Cette instruction n'importe pas l'intégralité du module fib dans l'espace de noms actuel ; elle introduit simplement l'élément ```fibonacci``` du module fib dans la table de symboles globale du module d'importation.

## L'instruction from ... import *

Il est également possible d'importer tous les noms d'un module dans l'espace de noms courant en utilisant l'instruction import suivante :

```python
from modname import *
```

Cela fournit un moyen facile d'importer tous les éléments d'un module dans l'espace de noms actuel ; cependant, cette instruction doit être utilisée avec parcimonie.

## Exécution de modules en tant que scripts

Dans un module, le nom du module (sous forme de chaîne de caractères) est disponible comme valeur de la variable globale ```__name__```. Le code du module sera exécuté, comme si vous l'aviez importé, mais avec la variable ```__name__``` définie sur ```__main__```.

Ajoutez ce code à la fin de votre module :

```python
#!/usr/bin/python3

# Fibonacci numbers module

def fib(n): # return Fibonacci series up to n
    result = []
    a, b = 0, 1
    while b < n:
        result.append(b)
        a, b = b, a + b
    return result
if __name__ == "__main__":
    f = fib(100)
    print(f)
```

Lorsque vous exécutez le code ci-dessus, la sortie suivante s'affiche.

```bash
[1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
```

## Localisation des modules

Lorsque vous importez un module, l'interpréteur Python recherche le module dans les séquences suivantes :

- Le répertoire actuel.
- Si le module n'est pas trouvé, Python recherche alors chaque répertoire dans la variable shell ```PYTHONPATH```.
- Si tout le reste échoue, Python vérifie le chemin par défaut. Sous UNIX, ce chemin par défaut est normalement ```/usr/local/lib/python3/```.

Le chemin de recherche du module est stocké dans le module système sys sous la forme de la variable ```sys.path```. La variable ```sys.path``` contient le répertoire courant, ```PYTHONPATH```, et le chemin par défaut dépendant de l'installation.

## La variable PYTHONPATH

La variable ```PYTHONPATH``` est une variable d'environnement, constituée d'une liste de répertoires. La syntaxe de ```PYTHONPATH``` est la même que celle de la variable shell ```PATH```.

Voici un ```PYTHONPATH``` typique d'un système Windows :

```bash
set PYTHONPATH = c:\python34\lib
```

Voici un ```PYTHONPATH``` typique d'un système UNIX :

```bash
set PYTHONPATH = /usr/local/lib/python
```

## Namespaces et portée des noms

Les variables sont des noms (identificateurs) qui correspondent à des objets. Un espace de noms est un dictionnaire de noms de variables (clés) et de leurs objets correspondants (valeurs).

- Une instruction Python peut accéder à des variables dans un espace de noms local et dans l'espace de noms global. Si une variable locale et une variable globale ont le même nom, la variable locale éclipse la variable globale.
- Chaque fonction possède son propre espace de noms local. Les méthodes de classe suivent la même règle de scoping que les fonctions ordinaires.
- Python fait des suppositions sur le caractère local ou global des variables. Il part du principe que toute variable à laquelle une valeur est attribuée dans une fonction est locale.
- Par conséquent, pour attribuer une valeur à une variable globale dans une fonction, vous devez d'abord utiliser l'instruction ```global```.
- L'instruction globale VarName indique à Python que VarName est une variable globale. Python cesse de rechercher la variable dans l'espace de nom local.

Par exemple, nous définissons une variable Money dans l'espace de noms global. Dans la fonction Money, nous attribuons une valeur à Money, donc Python considère Money comme une variable locale.

Cependant, nous avons accédé à la valeur de la variable locale Money avant de la définir, ce qui entraîne un UnboundLocalError. Décommenter l'instruction globale résout le problème.

```python
#!/usr/bin/python3

Money = 2000
def AddMoney():
    # Uncomment the following line to fix the code:
    # global Money
    Money = Money + 1

print (Money)
AddMoney()
print(Money)
```

## La fonction dir()

La fonction intégrée ```dir()``` renvoie une liste triée de chaînes de caractères contenant les noms définis par un module.

La liste contient les noms de tous les modules, variables et fonctions qui sont définis dans un module. Voici un exemple simple :

```python
#!/usr/bin/python3

# Import built-in module math
import math

content = dir(math)
print(content)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
['__doc__', '__file__', '__name__', 'acos', 'asin', 'atan', 
'atan2', 'ceil', 'cos', 'cosh', 'degrees', 'e', 'exp', 
'fabs', 'floor', 'fmod', 'frexp', 'hypot', 'ldexp', 'log',
'log10', 'modf', 'pi', 'pow', 'radians', 'sin', 'sinh', 
'sqrt', 'tan', 'tanh']
```

Ici, la variable spéciale ```__name__``` est le nom du module, et ```__file__``` est le nom du fichier à partir duquel le module a été chargé.

## Les fonctions globals() et locals()

Les fonctions ```globals()``` et ```locals()``` peuvent être utilisées pour renvoyer les noms des espaces de noms globaux et locaux en fonction de l'endroit d'où elles sont appelées.

- Si la fonction ```locals()``` est appelée à l'intérieur d'une fonction, elle renvoie tous les noms auxquels on peut accéder localement à partir de cette fonction.
- Si ```globals()``` est appelé à l'intérieur d'une fonction, il renverra tous les noms auxquels on peut accéder globalement à partir de cette fonction.

Le type de retour de ces deux fonctions est un dictionnaire. Par conséquent, les noms peuvent être extraits à l'aide de la fonction ```keys()```.

## La fonction reload()

Lorsqu'un module est importé dans un script, le code de la partie de haut niveau d'un module n'est exécuté qu'une seule fois.

Par conséquent, si vous souhaitez réexécuter le code de haut niveau d'un module, vous pouvez utiliser la fonction ```reload()```. La fonction ```reload()``` importe à nouveau un module précédemment importé. La syntaxe de la fonction ```reload()``` est la suivante :

```python
reload(module_name)
```

Ici, ```module_name``` est le nom du module que vous voulez recharger et non la chaîne contenant le nom du module. Par exemple, pour recharger le module hello, procédez comme suit :

```python
reload(hello)
```

## Paquets en Python

Un paquetage est une structure hiérarchique de répertoires de fichiers qui définit un environnement d'application Python unique, composé de modules, de sous-paquets, de sous-sous-paquets, et ainsi de suite.

Considérons un fichier ```Pots.py``` disponible dans le répertoire Phone. Ce fichier comporte la ligne de code source suivante :

```python
#!/usr/bin/python3

def Pots():
print("I'm Pots Phone") 
```

De même, nous avons deux autres fichiers ayant des fonctions différentes avec le même nom que ci-dessus. Il s'agit de :

- Fichier ```Phone/Isdn.py``` ayant la fonction ```Isdn()```
- Fichier ```Phone/G3.py``` ayant la fonction ```G3()```

Maintenant, créez un autre fichier ```__init__.py``` dans le répertoire Phone :

- ```Phone/__init__.py```

Pour rendre toutes vos fonctions disponibles lorsque vous avez importé Phone, vous devez mettre des déclarations d'importation explicites dans ```__init__.py``` comme suit :

```python
from Pots import Pots
from Isdn import Isdn
from G3 import G3
```

Après avoir ajouté ces lignes à ```__init__.py```, vous disposez de toutes ces classes lorsque vous importez le paquet Phone.

```python
#!/usr/bin/python3

# Now import your Phone Package.
import Phone

Phone.Pots()
Phone.Isdn()
Phone.G3()
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
I'm Pots Phone
I'm 3G Phone
I'm ISDN Phone
```

Dans l'exemple ci-dessus, nous avons pris l'exemple d'une seule fonction dans chaque fichier, mais vous pouvez conserver plusieurs fonctions dans vos fichiers. Vous pouvez également définir différentes classes Python dans ces fichiers, puis créer vos packages à partir de ces classes.
