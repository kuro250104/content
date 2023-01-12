Ce chapitre couvre toutes les fonctions d'E/S de base disponibles dans Python 3. Pour plus de fonctions, veuillez vous référer à la documentation standard de Python.

## Impression à l'écran

La façon la plus simple de produire une sortie est d'utiliser l'instruction print à laquelle vous pouvez passer zéro ou plusieurs expressions séparées par des virgules. Cette fonction convertit les expressions que vous passez en une chaîne de caractères et écrit le résultat sur la sortie standard comme suit :

```python
#!/usr/bin/python3
print("Python is really a great language,","isn't it?")
```

Cela donne le résultat suivant sur votre écran standard :

```bash
Python is really a great language, isn't it?
```

## Lecture de l'entrée du clavier

Python 2 dispose de deux fonctions intégrées pour lire les données de l'entrée standard, qui par défaut provient du clavier. Ces fonctions sont ```input()``` et ```raw_input()```.

Dans Python 3, la fonction ```raw_input()``` est dépréciée. De plus, les fonctions ```input()``` lisent les données du clavier sous forme de chaîne de caractères, qu'elle soit entourée de guillemets (' ' ou " ") ou non.

## La fonction input

La fonction ```input([prompt])``` est équivalente à ```raw_input```, sauf qu'elle suppose que l'entrée est une expression Python valide et vous renvoie le résultat évalué.

```python
#!/usr/bin/python3

>>> x = input("something:")
something:10

>>> x
'10'

>>> x = input("something:")
something:'10' #entered data treated as string with or without ''

>>> x
"'10'"
```

## Ouverture et fermeture de fichiers

Jusqu'à présent, vous avez lu et écrit sur l'entrée et la sortie standard. Nous allons maintenant voir comment utiliser des fichiers de données réels.

Python fournit par défaut les fonctions et méthodes de base nécessaires à la manipulation des fichiers. Vous pouvez effectuer la plupart des manipulations de fichiers à l'aide d'un objet fichier.

## La fonction open

Avant de pouvoir lire ou écrire un fichier, vous devez l'ouvrir à l'aide de la fonction intégrée ```open()``` de Python. Cette fonction crée un objet fichier, qui sera utilisé pour appeler d'autres méthodes de support qui lui sont associées.

### Syntaxe

```python
file object = open(file_name [,access_mode][,buffering])
```

Voici les détails des paramètres :

- ```file_name``` : L'argument file_name est une valeur de type chaîne de caractères qui contient le nom du fichier auquel on veut accéder.
- ```access_mode``` : L'argument access_mode détermine le mode dans lequel le fichier doit être ouvert, c'est-à-dire lecture, écriture, ajout, etc. Une liste complète des valeurs possibles est donnée ci-dessous dans le tableau. Il s'agit d'un paramètre facultatif et le mode d'accès au fichier par défaut est la lecture (r).
- ```buffering``` : Si la valeur de la mise en mémoire tampon est fixée à 0, aucune mise en mémoire tampon n'a lieu. Si la valeur de mise en mémoire tampon est 1, une mise en mémoire tampon de ligne est effectuée lors de l'accès à un fichier. Si vous spécifiez la valeur de mise en mémoire tampon sous la forme d'un nombre entier supérieur à 1, la mise en mémoire tampon est effectuée avec la taille de tampon indiquée. Si elle est négative, la taille de la mémoire tampon est celle du système par défaut (comportement par défaut).

Voici une liste des différents modes d'ouverture d'un fichier :

- ```r``` : Ouvre un fichier en lecture seule. Le pointeur de fichier est placé au début du fichier. C'est le mode par défaut.
- ```rb``` : Ouvre un fichier en lecture seule au format binaire. Le pointeur de fichier est placé au début du fichier. C'est le mode par défaut.
- ```r+``` : Ouvre un fichier pour la lecture et l'écriture. Le pointeur de fichier est placé au début du fichier.
- ```rb+``` : Ouvre un fichier en lecture et en écriture au format binaire. Le pointeur de fichier est placé au début du fichier.
- ```w``` : Ouvre un fichier pour l'écriture uniquement. Écrase le fichier si celui-ci existe. Si le fichier n'existe pas, crée un nouveau fichier pour l'écriture.
- ```wb``` : Ouvre un fichier en écriture uniquement au format binaire. Écrase le fichier s'il existe. Si le fichier n'existe pas, crée un nouveau fichier à écrire.
- ```w+``` : Ouvre un fichier en écriture et en lecture. Écrase le fichier existant si le fichier existe. Si le fichier n'existe pas, crée un nouveau fichier pour la lecture et l'écriture.
- ```wb+``` : Ouvre un fichier en écriture et en lecture au format binaire. Écrase le fichier existant s'il existe. Si le fichier n'existe pas, crée un nouveau fichier pour la lecture et l'écriture.
- ```a``` : Ouvre un fichier pour y ajouter des données. Le pointeur de fichier est à la fin du fichier si le fichier existe. C'est-à-dire que le fichier est en mode ajout. Si le fichier n'existe pas, il crée un nouveau fichier pour l'écriture.
- ```ab``` : Ouvre un fichier à annexer au format binaire. Le pointeur de fichier est à la fin du fichier si le fichier existe. C'est-à-dire que le fichier est en mode ajout. Si le fichier n'existe pas, il crée un nouveau fichier à écrire.
- ```a+``` : Ouvre un fichier à la fois pour l'ajout et la lecture. Le pointeur de fichier est à la fin du fichier si le fichier existe. Le fichier s'ouvre en mode ajout. Si le fichier n'existe pas, il crée un nouveau fichier pour la lecture et l'écriture.
- ```ab+``` : Ouvre un fichier pour l'ajout et la lecture au format binaire. Le pointeur de fichier se trouve à la fin du fichier si celui-ci existe. Le fichier s'ouvre en mode ajout. Si le fichier n'existe pas, il crée un nouveau fichier pour la lecture et l'écriture.

## Les attributs de l'objet fichier

Une fois qu'un fichier est ouvert et que vous avez un objet fichier, vous pouvez obtenir diverses informations relatives à ce fichier.

Voici une liste de tous les attributs liés à un objet fichier :

- ```file.closed``` : Retourne true si le fichier est fermé, false sinon.
- ```file.mode``` : Retourne le mode d'accès avec lequel le fichier a été ouvert.
- ```file.name``` : Retourne le nom du fichier.

__Remarque__ : L'attribut softspace n'est pas pris en charge dans Python 3.x.

### Exemple

```python
#!/usr/bin/python3

# Open a file
fo = open("foo.txt", "wb")
print("Name of the file :", fo.name)
print("Closed or not :", fo.closed)
print("Opening mode :", fo.mode)
fo.close()
```

On obtient ainsi le résultat suivant :

```bash
Name of the file : foo.txt
Closed or not : False
Opening mode : wb
```

## La méthode close()

La méthode ```close()``` d'un objet fichier vide les informations non écrites et ferme l'objet fichier, après quoi aucune écriture ne peut plus être effectuée.

Python ferme automatiquement un fichier lorsque l'objet de référence d'un fichier est affecté à un autre fichier. Il est recommandé d'utiliser la méthode ```close()``` pour fermer un fichier.

### Syntaxe

```python
fileObject.close();
```

### Exemple

```python
#!/usr/bin/python3

# Open a file
fo = open("foo.txt", "wb")
print("Name of the file :", fo.name)

# Close opened file
fo.close()
```

On obtient ainsi le résultat suivant :

```bash
Name of the file : foo.txt
```

## Lecture et écriture de fichiers

L'objet fichier fournit un ensemble de méthodes d'accès pour nous faciliter la vie. Nous allons voir comment utiliser les méthodes ```read()``` et ```write()``` pour lire et écrire des fichiers.

## La méthode write()


La méthode ```write()``` écrit n'importe quelle chaîne de caractères dans un fichier ouvert. Il est important de noter que les chaînes Python peuvent contenir des données binaires et pas seulement du texte.

La méthode ```write()``` n'ajoute pas de caractère de nouvelle ligne (```\n```) à la fin de la chaîne :

### Syntaxe

```python
fileObject.write(string);
```

Ici, le paramètre passé est le contenu à écrire dans le fichier ouvert.

### Exemple

```python
#!/usr/bin/python3

# Open a file
fo = open("foo.txt", "w")
fo.write("Python is a great language.\nYeah its great!!\n")

# Close opend file
fo.close()
```

La méthode ci-dessus crée le fichier foo.txt et y écrit le contenu donné, puis ferme le fichier. Si vous ouvrez ce fichier, il aura le contenu suivant :

```bash
Python is a great language.
Yeah its great!!
```

## La méthode read()

La méthode ```read()``` lit une chaîne de caractères à partir d'un fichier ouvert. Il est important de noter que les chaînes Python peuvent contenir des données binaires, en plus des données texte.

### Syntax

```python
fileObject.read([count]);
```

Ici, le paramètre passé est le nombre d'octets à lire depuis le fichier ouvert. Cette méthode commence à lire depuis le début du fichier et si le nombre d'octets est manquant, elle essaie de lire autant que possible, peut-être jusqu'à la fin du fichier.

### Exemple

Prenons un fichier ```foo.txt```, que nous avons créé ci-dessus.

```python
#!/usr/bin/python3

# Open a file
fo = open("foo.txt","r+")
str = fo.read(10)
print ("Read String is :", str)

# Close opened file
fo.close()
```

On obtient ainsi le résultat suivant :

```bash
Read String is : Python is
```

## Positions des fichiers

La méthode ```tell()``` vous indique la position actuelle dans le fichier ; en d'autres termes, la prochaine lecture ou écriture aura lieu à ce nombre d'octets du début du fichier.

La méthode ```seek(offset[, from])``` modifie la position actuelle du fichier. L'argument offset indique le nombre d'octets à déplacer. L'argument from spécifie la position de référence à partir de laquelle les octets doivent être déplacés.

Si ```from``` a la valeur 0, le début du fichier est utilisé comme position de référence. S'il a la valeur 1, la position actuelle est utilisée comme position de référence. S'il est défini à 2, la fin du fichier sera prise comme position de référence.

### Exemple

Prenons un fichier ```foo.txt```, que nous avons créé ci-dessus :

```python
#!/usr/bin/python3

# Open a file
fo = open("foo.txt", "r+")
str = fo.read(10)
print("Read String is :", str)

# Check current position
position = fo.tell()
print("Current file position :", position)

# Reposition pointer at the beginning once again
position = fo.seek(0, 0)
str = fo.read(10)
print("Again read String is :", str)

# Close opened file
fo.close()
```

On obtient ainsi le résultat suivant :

```bash
Read String is : Python is
Current file position : 10
Again read String is : Python is
```

## Renommer et supprimer des fichiers

Le module Python ```os``` fournit des méthodes qui vous aident à effectuer des opérations de traitement de fichiers, comme le renommage et la suppression de fichiers.

Pour utiliser ce module, vous devez d'abord l'importer, puis vous pouvez appeler toutes les fonctions associées.

## La méthode rename()

La méthode ```rename()``` prend deux arguments, le nom de fichier actuel et le nouveau nom de fichier.

### Syntaxe

```python
os.rename(current_file_name, new_file_name)
```

### Exemple

L'exemple suivant permet de renommer un fichier existant test1.txt :

```python
#!/usr/bin/python3
import os

# Rename a file from test1.txt to test2.txt
os.rename("test1.txt", "test2.txt")
```

## La méthode remove()

Vous pouvez utiliser la méthode ```remove()``` pour supprimer des fichiers en fournissant le nom du fichier à supprimer comme argument.

### Syntaxe

```python
os.remove(file_name)
```

### Exemple

L'exemple suivant permet de supprimer un fichier existant ```test2.txt``` :

```python
#!/usr/bin/python3
import os

# Delete file test2.txt
os.remove("text2.txt")
```

## Répertoires en Python

Tous les fichiers sont contenus dans différents répertoires, et Python n'a aucun problème à les gérer également. Le module ```os``` possède plusieurs méthodes qui vous aident à créer, supprimer et modifier des répertoires.

## La méthode mkdir()

Vous pouvez utiliser la méthode ```mkdir()``` du module os pour créer des répertoires dans le répertoire courant. Vous devez fournir un argument à cette méthode, qui contient le nom du répertoire à créer.

### Syntaxe

```python
os.mkdir("newdir")
```

### Exemple

L'exemple suivant permet de créer un répertoire test dans le répertoire courant :

```python
#!/usr/bin/python3
import os

# Create a directory "test"
os.mkdir("test")
```

## La méthode chdir()

Vous pouvez utiliser la méthode ```chdir()``` pour changer le répertoire courant. La méthode ```chdir()``` prend un argument, qui est le nom du répertoire que vous voulez faire devenir le répertoire courant.

### Syntaxe

```python
os.chdir("newdir")
```

### Exemple

Voici un exemple pour aller dans le répertoire ```/home/newdir``` :

```python
#!/usr/bin/python3
import os

# Changing a directory to "/home/newdir"
os.chdir("/home/newdir")
```

### La méthode getcwd()

La méthode ```getcwd()``` affiche le répertoire de travail actuel.

### Syntaxe

```python
os.getcwd()
```

### Exemple

Voici un exemple pour donner le répertoire courant :

```python
#!/usr/bin/python3
import os

# This would give location of the current directory
os.getcwd()
```

## La méthode rmdir()

La méthode ```rmdir()``` supprime le répertoire, qui est passé en argument dans la méthode.
Avant de supprimer un répertoire, il convient de supprimer tout le contenu qu'il contient.

### Syntaxe

```python
os.rmdir('dirname')
```

### Exemple

Voici un exemple pour supprimer le répertoire ```/tmp/test```. Il est nécessaire de donner le nom complet du répertoire, sinon il cherchera ce répertoire dans le répertoire courant.

```python
#!/usr/bin/python3
import os

# This would  remove "/tmp/test" directory.
os.rmdir("/tmp/test")
```

## Méthodes relatives aux fichiers et répertoires

Il existe trois sources importantes, qui fournissent un large éventail de méthodes utilitaires pour manipuler les fichiers et les répertoires sur les systèmes d'exploitation Windows et Unix. Elles sont les suivantes :

- ```File Object Methods``` : L'objet file fournit des fonctions pour manipuler les fichiers.
- ```OS Object Methods``` : Cet objet fournit des méthodes pour traiter les fichiers ainsi que les répertoires.
