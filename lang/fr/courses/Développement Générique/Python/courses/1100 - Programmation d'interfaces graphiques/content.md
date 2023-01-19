Python offre diverses options pour le développement d'interfaces utilisateur graphiques (IUG). Les fonctionnalités les plus importantes sont énumérées ci-dessous.

- **Tkinter** - Tkinter est l'interface Python de la boîte à outils Tk GUI livrée avec Python. Nous étudierons cette option dans ce chapitre.
- **wxPython** - C'est une interface Python open-source pour la boîte à outils GUI wxWidgets.
- **PyQt** - Il s'agit également d'une interface Python pour la populaire bibliothèque d'interfaces graphiques Qt multiplateforme.
- **JPython** - JPython est un portage Python pour Java, qui donne aux scripts Python un accès transparent aux bibliothèques de classes Java sur la machine locale.

Il existe de nombreuses autres interfaces, que vous pouvez trouver sur le net.

## Programmation Tkinter

Tkinter est la bibliothèque standard d'interface graphique pour Python. Combiné à Tkinter, Python offre un moyen rapide et facile de créer des applications graphiques. Tkinter fournit une interface orientée objet puissante à la boîte à outils Tk GUI.

Créer une application GUI en utilisant Tkinter est une tâche facile. Tout ce que vous avez à faire est d'effectuer les étapes suivantes :

- Importez le module Tkinter.
- Créer la fenêtre principale de l'application GUI.
- Ajoutez un ou plusieurs des widgets mentionnés ci-dessus à l'application GUI.
- Entrez dans la boucle d'événement principale pour prendre des mesures contre chaque événement déclenché par l'utilisateur.

### Exemple

```python
#!/usr/bin/python3

import tkinter # note that module name has changed from Tkinter in Python 2 to tkinter in Python 3
top = tkinter.Tk()
# Code to add widgets will go here...
top.mainloop()
```

## Widgets Tkinter

Tkinter fournit divers contrôles, tels que des boutons, des étiquettes et des boîtes de texte utilisés dans une application GUI. Ces contrôles sont communément appelés widgets.

Il y a actuellement 19 types de widgets dans Tkinter. Nous présentons ces widgets ainsi qu'une brève description dans le tableau suivant :

- ```Button``` : Le widget Button est utilisé pour afficher les boutons dans votre application.
- ```Canvas``` : Le widget Canvas est utilisé pour dessiner des formes, telles que des lignes, des ovales, des polygones et des rectangles, dans votre application.
- ```Checkbutton``` : Le widget Checkbutton est utilisé pour afficher un certain nombre d'options sous forme de cases à cocher. L'utilisateur peut sélectionner plusieurs options à la fois.
- ```Entry``` : Le widget Entry est utilisé pour afficher un champ de texte d'une ligne pour accepter les valeurs d'un utilisateur.
- ```Frame``` : Le widget Frame est utilisé comme un widget conteneur pour organiser d'autres widgets.
- ```Label``` : Le widget Label est utilisé pour fournir une légende d'une ligne à d'autres widgets. Il peut également contenir des images.
- ```Listbox``` : Le widget Listbox est utilisé pour fournir une liste d'options à un utilisateur.
- ```Menubutton``` : Le widget Menubutton est utilisé pour afficher des menus dans votre application.
- ```Menu``` : Le widget Menu est utilisé pour fournir diverses commandes à un utilisateur. Ces commandes sont contenues dans le Menubutton.
- ```Message``` : Le widget Message est utilisé pour afficher des champs de texte multilignes pour accepter des valeurs d'un utilisateur.
- ```Radiobutton``` : Le widget Radiobutton est utilisé pour afficher un certain nombre d'options sous forme de boutons radio. L'utilisateur ne peut sélectionner qu'une seule option à la fois.
- ```Scale``` : Le widget Scale est utilisé pour fournir un widget de curseur.
- ```Scrollbar``` : Le widget Scrollbar est utilisé pour ajouter une capacité de défilement à divers widgets, tels que les boîtes de liste.
- ```Text``` : Le widget Text est utilisé pour afficher du texte sur plusieurs lignes.
- ```Toplevel``` : Le widget Toplevel est utilisé pour fournir un conteneur de fenêtre séparé.
- ```Spinbox``` : Le widget Spinbox est une variante du widget Entry standard de Tkinter, qui peut être utilisé pour choisir parmi un nombre fixe de valeurs.
- ```PanedWindow``` : Un PanedWindow est un widget conteneur qui peut contenir un nombre quelconque de panneaux, disposés horizontalement ou verticalement.
- ```LabelFrame``` : Un LabelFrame est un simple widget conteneur. Son objectif principal est d'agir comme un espaceur ou un conteneur pour des dispositions de fenêtres complexes.
- ```tkMessageBox``` : Ce module est utilisé pour afficher des boîtes de messages dans vos applications.

## Gestion de la géométrie

Tous les widgets de Tkinter ont accès aux méthodes spécifiques de gestion de la géométrie, qui ont pour but d'organiser les widgets dans la zone du widget parent. Tkinter expose les classes de gestion de la géométrie suivantes : pack, grid, et place.

- ```pack()``` : Ce gestionnaire de géométrie organise les widgets en blocs avant de les placer dans le widget parent.
- ```grid()``` : Ce gestionnaire de géométrie organise les widgets dans une structure de type tableau dans le widget parent.
- ```place()``` : Ce gestionnaire de géométrie organise les widgets en les plaçant dans une position spécifique dans le widget parent.
