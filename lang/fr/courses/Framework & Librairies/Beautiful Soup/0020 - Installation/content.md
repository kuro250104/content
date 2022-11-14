## Introduction

Comme BeautifulSoup n'est pas une bibliothèque python standard, nous devons d'abord l'installer. Nous allons installer la bibliothèque BeautifulSoup 4 (également connue sous le nom de BS4), qui est la plus récente.

Pour isoler notre environnement de travail afin de ne pas perturber la configuration existante, nous allons d'abord créer un environnement virtuel.

## Création d'un environnement virtuel (facultatif)

Un environnement virtuel nous permet de créer une copie de travail isolée de python pour un projet spécifique sans affecter la configuration extérieure.

La meilleure façon d'installer n'importe quel paquetage python est d'utiliser pip, cependant, si pip n'est pas déjà installé (vous pouvez le vérifier en utilisant - "pip -version" dans votre invite de commande ou shell), vous pouvez l'installer en donnant la commande ci-dessous -

### Linux environment

```bash
$sudo apt-get install python-pip
```

### Windows environment

Pour installer Pip sous Windows, procédez comme suit

Téléchargez le fichier get-pip.py depuis ```https://bootstrap.pypa.io/get-pip.py``` ou depuis github sur votre ordinateur.

Ouvrez l'invite de commande et naviguez dans le dossier contenant le fichier get-pip.py.

Exécutez la commande suivante -

```bash
>python get-pip.py
```

C'est tout, pip est maintenant installé sur votre machine Windows.

Vous pouvez vérifier que votre pip est installé en exécutant la commande ci-dessous -

```bash
>pip --version
pip 22.3.1 from c:\users\microlead\appdata\local\programs\python\python37\lib\site-packages\pip (python 3.7)
```

## Installation de l'environnement virtuel

Exécutez la commande ci-dessous dans votre invite de commande -

```bash
>pip install virtualenv
```

La commande ci-dessous créera un environnement virtuel ("myEnv") dans votre répertoire courant -

```bash
>virtualenv myEnv
```

Pour activer votre environnement virtuel, exécutez la commande suivante -

```bash
>myEnv\Scripts\activate
```

Pour sortir de l'environnement virtuel, exécutez deactivate.

```bash
(myEnv) C:\Users\yadur>deactivate
C:\Users\yadur>
```

Comme notre environnement virtuel est prêt, installons maintenant beautifulsoup.

## Installation de BeautifulSoup

Comme BeautifulSoup n'est pas une bibliothèque standard, nous devons l'installer. Nous allons utiliser le paquetage BeautifulSoup 4 (connu sous le nom de bs4).

### Machine Linux

Pour installer bs4 sur Debian ou Ubuntu linux à l'aide du gestionnaire de paquets du système, exécutez la commande suivante : -.

```bash
$sudo apt-get install python-bs4 (for python 2.x)
$sudo apt-get install python3-bs4 (for python 3.x)
```

Vous pouvez installer bs4 à l'aide de easy_install ou de pip (si vous rencontrez des problèmes lors de l'installation à l'aide du system packager).

```bash
$easy_install beautifulsoup4
$pip install beautifulsoup4
```

(Vous devrez peut-être utiliser easy_install3 ou pip3 respectivement si vous utilisez python3)

### Machine Windows

L'installation de beautifulsoup4 sous Windows est très simple, surtout si vous avez déjà installé pip.

```bash
>pip install beautifulsoup4
```

## Problèmes après l'installation

Sur une machine Windows, vous pouvez rencontrer l'erreur "mauvaise version installée", principalement par le biais de -.

- **error: ImportError "No module named HTMLParser"**, alors vous devez exécuter la version python 2 du code sous Python 3.
- **error: Erreur ImportError "No module named html.parser"**, alors vous devez exécuter la version Python 3 du code sous Python 2.

La meilleure façon de sortir de ces deux situations est de réinstaller BeautifulSoup à nouveau, en supprimant complètement l'installation existante.

Si vous obtenez le **SyntaxError "Invalid syntax"** sur la ligne ```ROOT_TAG_NAME = u'[document]'```, alors vous devez convertir le code python 2 en python 3, simplement en installant le paquet -

```bash
$ python3 setup.py install
```

ou en exécutant manuellement le script de conversion 2 vers 3 de python sur le répertoire bs4 -

```bash
$ 2to3-3.2 -w bs4
```

## Installation d'un analyseur

Par défaut, Beautiful Soup prend en charge l'analyseur HTML inclus dans la bibliothèque standard de Python, mais il prend également en charge de nombreux analyseurs python tiers externes comme l'analyseur lxml ou l'analyseur html5lib.

Pour installer le parseur lxml ou html5lib, utilisez la commande -

### Machine Linux

```bash
$apt-get install python-lxml
$apt-get insall python-html5lib
```

### Machine Windows

```bash
$pip install lxml
$pip install html5lib
```

En général, les utilisateurs utilisent lxml pour sa rapidité et il est recommandé d'utiliser l'analyseur lxml ou html5lib si vous utilisez une version plus ancienne de python 2 (avant la version 2.7.3) ou python 3 (avant la version 3.2.2) car l'analyseur HTML intégré à python n'est pas très performant pour gérer les anciennes versions.

## Lancer Beautiful Soup

Il est temps de tester notre paquet Beautiful Soup dans une page html et d'en extraire quelques informations.

Dans le code ci-dessous, nous essayons d'extraire le titre de la page d'accueil de microlead.

```python
from bs4 import BeautifulSoup
import requests
url = "https://www.microlead.fr"
req = requests.get(url)
soup = BeautifulSoup(req.text, "html.parser")
print(soup.title)
```

Une tâche courante consiste à extraire toutes les URL d'une page Web. Pour cela, il suffit d'ajouter la ligne de code ci-dessous -

```python
for link in soupe.find_all('a') :
    print(link.get('href'))
```