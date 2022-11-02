Python 3 est disponible pour Windows, Mac OS et la plupart des versions du système d'exploitation Linux. Bien que Python 2 soit disponible pour de nombreux autres systèmes d'exploitation, le support de Python 3 n'a pas été rendu disponible pour eux ou a été abandonné.

## Configuration de l'environnement local

Ouvrez une fenêtre de terminal et tapez ```python``` pour ouvrir une console python et obtenir la version utilisée. Pour en sortir, il faudra saisir ```exit()```. Ou, plus simplement, vous pouvez obtenir la version utilisée de python avec ```python -V```.

![Résultat de l'exécution de la commande python -V](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/Python/courses/0020%20-%20Configuration%20de%20l'environnement/images/image2.png)

Si la console indique qu’elle ne trouve pas Python, il vous faudra alors installer Python.

__remarque__ : En fonction de votre ordinateur, il est possible que le mot-clé ```python``` soit à remplacer soit par ```python3``` soit par ```py```. Le reste de la commande est inchangé. Attention, vous devrez réaliser ce changement pour l'ensemble des commandes à venir dans les cours.

### Obtenir Python

#### Windows

Les binaires de la dernière version de Python 3 sont disponibles sur cette page de téléchargement : <a href="https://www.python.org/downloads/windows/" target="_blank" title="Python pour Windows">https://www.python.org/downloads/windows/</a>.

![Screenshot des fichiers binaires disponibles pour python 3](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/Python/courses/0020%20-%20Configuration%20de%20l'environnement/images/image1.png)

Différents installateurs sont disponibles. Nous vous conseillons de prendre la version stable la plus récente de Python avec la version Windows installer correspondant à votre ordinateur. 

Lors de l’installation par un double clic sur l’icône de l'installateur, vérifiez que l’ajout de Python au path est bien sélectionné.

![Screenshot de l'installation de python 3](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/Python/courses/0020%20-%20Configuration%20de%20l'environnement/images/image3.png)

#### Linux

Les différentes versions de Linux utilisent différents gestionnaires de paquets pour l'installation de nouveaux paquets.

Sur Ubuntu Linux, Python 3 est installé en utilisant la commande suivante depuis le terminal.

```bash
sudo apt-get install python3-minimal
```

##### Installation à partir des sources

Téléchargez l'archive source compressée à partir de l'URL de téléchargement de Python - <a href="https://www.python.org/downloads/source/" target="_blank" title="Téléchargement de l'archive de python">https://www.python.org/downloads/source/</a>.

```bash
# Extraire le fichier tarball
tar xvfz Python-<version>.tgz
# Configurer et installer :
cd Python-<version>
./configure --prefix = /opt/python<version>
make  
sudo make install
```

#### Mac OS

Téléchargez les installateurs Mac OS à partir de cette URL - <a href="https://www.python.org/downloads/mac-osx/" target="_blank" title="Téléchargez les installateurs de Python pour Mac OS">https://www.python.org/downloads/mac-osx/</a> ```Installateur Mac OS X 64-bit/32-bit - python-<version>-macosx<version>.pkg```

Double-cliquez sur ce fichier de paquetage et suivez les instructions de l'assistant pour l'installation.

## Configuration du PATH

Les programmes et autres fichiers exécutables peuvent se trouver dans de nombreux répertoires. C'est pourquoi les systèmes d'exploitation fournissent un chemin de recherche qui répertorie les répertoires dans lesquels ils recherchent les exécutables.

Les caractéristiques importantes sont les suivantes .

- Le chemin d'accès est stocké dans une variable d'environnement, qui est une chaîne nommée maintenue par le système d'exploitation. Cette variable contient des informations disponibles pour le shell de commande et d'autres programmes.
- La variable de chemin d'accès est appelée PATH sous Unix ou Path sous Windows (Unix est sensible à la casse, Windows ne l'est pas).
- Sous Mac OS, le programme d'installation gère les détails du chemin. Pour invoquer l'interpréteur Python à partir d'un répertoire particulier, vous devez ajouter le répertoire Python à votre chemin.

### Définition du chemin sous Unix/Linux

Pour ajouter le répertoire Python au chemin d'accès d'une session donnée sous Unix

- **Dans l'interpréteur de commandes csh** - tapez ```setenv PATH "$PATH:/usr/local/bin/python3"``` et appuyez sur Entrée.
- **Dans l'interpréteur de commandes bash (Linux)** - tapez ```export PYTHONPATH=/usr/local/bin/python3.7``` et appuyez sur Entrée.
- **Dans l'interpréteur de commandes sh ou ksh** - tapez ```PATH = "$PATH:/usr/local/bin/python3"``` et appuyez sur Entrée.

__Remarque__ : ```/usr/local/bin/python3``` est généralement le chemin du répertoire Python.

### Définition du chemin sous Windows

Si vous avez bien suivi l’étape d’installation de Python, vous n’aurez pas à suivre cette étape.

Dans un premier temps, copiez le chemin d’accès au répertoire Python à utiliser par défaut:

![Screenshot du chemin d’accès au répertoire Python à utiliser par défaut](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/Python/courses/0020%20-%20Configuration%20de%20l'environnement/images/image4.png)

__Remarque__ : ```C:\Python3X``` est le chemin du répertoire vers Python en version 3.X.

Pour ajouter le répertoire Python au chemin d'accès d'une session particulière sous Windows, procédez comme suit :

- Rendez-vous sur l'invite de commande
- Saisissez: ```path %path%;C:\Python3X```
- Appuyez sur la touche Entrée.

## Variables d'environnement Python

Voici les variables d'environnement importantes, qui sont reconnues par Python :

- **PYTHONPATH** : Elle a un rôle similaire à celui de PATH. Cette variable indique à l'interpréteur Python où trouver les fichiers de modules importés dans un programme. Elle doit inclure le répertoire de la bibliothèque source Python et les répertoires contenant le code source Python. PYTHONPATH est parfois prédéfini par le programme d'installation de Python.
- **PYTHONSTARTUP** : Il contient le chemin d'un fichier d'initialisation contenant le code source de Python. Il est exécuté à chaque fois que vous démarrez l'interpréteur. Il est nommé .pythonrc.py sous Unix et contient des commandes qui chargent des utilitaires ou modifient PYTHONPATH.
- **PYTHONCASEOK** : Elle est utilisée dans Windows pour demander à Python de trouver la première correspondance insensible à la casse dans une instruction d'importation. Donnez à cette variable n'importe quelle valeur pour l'activer.
- **PYTHONHOME** : Il s'agit d'un chemin alternatif de recherche de modules. Il est généralement intégré dans les répertoires PYTHONSTARTUP ou PYTHONPATH pour faciliter le changement de bibliothèque de modules.

## Exécution de Python

Il y a trois façons différentes de lancer Python, à savoir :

### Interpréteur interactif

Vous pouvez lancer Python depuis Unix, DOS, ou tout autre système qui vous fournit un interpréteur de ligne de commande ou une fenêtre shell.

Entrez ‘python’ dans la ligne de commande.
Commencez à coder immédiatement dans l'interpréteur interactif.

```bash
$python # Unix/Linux
ou
python% # Unix/Linux
ou
C:>python # Windows/DOS
```

Pour en sortir, saisissez ```exit()```.

Voici la liste de toutes les options disponibles en ligne de commande :

| **-d** | fournit les informations de débogage |
| **-O** | génère un bytecode optimisé (résultant en des fichiers .pyo) |
| **-s** | ne pas exécuter le site d'importation pour rechercher les chemins Python au démarrage |
| **-v** | informations détaillées (trace détaillée sur les déclarations d'importation) |
| **-x** | désactive les exceptions intégrées basées sur les classes (utilisez simplement des chaînes de caractères) ; obsolète à partir de la version 1.6 |
| **-c cmd** | exécute le script Python envoyé en tant que chaîne cmd |
| **fichier.py** | exécute le script Python à partir du fichier donné |
| **-m fichier** | exécute le script Python à partir du fichier donné sans avoir à préciser l’extension |

__Remarque__ : Pour ouvrir un fichier Python, il faut soit ouvrir la console au niveau du fichier Python à exécuter, soit indiquer le chemin du fichier.

### Arguments de ligne de commande

De nombreux programmes peuvent être exécutés pour vous fournir des informations de base sur la façon dont ils doivent être exécutés. Python vous permet de le faire avec -h :

```bash
$ python -h
utilisation : python [option] ... [-c cmd | -m mod | file | -] [arg] ...
Options et arguments (et variables d'environnement correspondantes) :
-c cmd : programme passé en tant que chaîne de caractères (termine la liste des options)
-d : informations de débogage de l'analyseur (également PYTHONDEBUG=x)
-E : ignore les variables d'environnement (telles que PYTHONPATH)
-h : afficher ce message d'aide et quitter

[ etc. ]
```

__Remarque__ : Assurez-vous que le mode d'autorisation du fichier permet l'exécution.

### Environnement de développement intégré

Vous pouvez également exécuter Python à partir d'un environnement d'interface utilisateur graphique (GUI), si votre système comporte une application GUI prenant en charge Python:

- **Unix** - IDLE est le tout premier IDE Unix pour Python.
- **Windows** - PythonWin est la première interface Windows pour Python et est un IDE avec une interface graphique.
- **Macintosh** - La version Macintosh de Python ainsi que l'IDE IDLE sont disponibles sur le site principal, téléchargeables sous forme de fichiers MacBinary ou BinHex.

Mais ce n’est pas tout: il existe une multitude d’IDE (Integrated Development Environment : interfaces qui ont pour but d’aider les développeurs à coder) compatibles. En voici une liste non exhaustive:

- PyCharm Community (l’un des IDE Python plus connus et gratuit);
- PyCharm Pro (La version payante de PyCharm offre des outils de développement supplémentaire); 
- Visual Studio Code (un autre IDE très réputé).

N’hésitez pas à passer un peu de temps sur les tutoriels qui aident à comprendre la configuration de ces outils.