## Introduction

La distribution standard de Python ne contient pas le module NumPy. Une alternative légère consiste à installer NumPy à l'aide du populaire installateur de paquets Python, pip.

```python
pip install numpy
```

La meilleure façon d'activer NumPy est d'utiliser un paquet binaire installable spécifique à votre système d'exploitation. Ces binaires contiennent la pile SciPy complète (y compris les paquets NumPy, SciPy, matplotlib, IPython, SymPy et nose ainsi que le noyau Python).

## Windows

**Anaconda** (de <a href="https://www.anaconda.com/" title="anaconda" target="_blank">https://www.anaconda.com/</a>) est une distribution gratuite de Python pour la pile SciPy. Elle est également disponible pour Linux et Mac. Pour ceux souhaitant faire du machine learning, de la data science, ou bien du scripting avec Python, c'est l'intallation la plus courante de nos jour et celle le plus utilisée en entreprise. Nous vous la recommendons donc.

**Canopy** est disponible en distribution gratuite et commerciale avec la pile SciPy complète pour Windows, Linux et Mac.

**Python (x,y)** : Il s'agit d'une distribution libre de Python avec la pile SciPy et l'IDE Spyder pour Windows OS.

## Linux

Les gestionnaires de paquets des distributions Linux respectives sont utilisés pour installer un ou plusieurs paquets dans la pile SciPy.

### Pour Ubuntu

```bash
sudo apt-get install python-numpy 
python-scipy python-matplotlibipythonipythonnotebook python-pandas 
python-sympy python-nose
```

### For Fedora

```bash
sudo yum install numpyscipy python-matplotlibipython 
python-pandas sympy python-nose atlas-devel
```

### Construire à partir de la source

Le noyau Python (2.6.x, 2.7.x et 3.2.x et suivants) doit être installé avec distutils et le module zlib doit être activé.

Le compilateur C GNU gcc (4.2 et plus) doit être disponible.

Pour installer NumPy, exécutez la commande suivante.

```bash
Python setup.py install
```

Pour vérifier si le module NumPy est correctement installé, essayez de l'importer à partir de l'invite Python.

```python
import numpy
```

S'il n'est pas installé, le message d'erreur suivant s'affiche.

```python
Traceback (most recent call last): 
    File "<pyshell#0>", line 1, in <module> 
        import numpy 
ImportError: No module named 'numpy'
```

Alternativement, le paquet NumPy est importé en utilisant la syntaxe suivante -

```python
import numpy as np
```