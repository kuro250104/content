Le modèle de fabrique abstraite est également appelé fabrique de fabricants. Ce modèle de conception fait partie de la catégorie des modèles de conception créative. Il fournit l'une des meilleures façons de créer un objet.

Il comprend une interface, qui est responsable de la création d'objets liés à Factory.

## Comment mettre en œuvre le modèle abstract factory ?

Le programme suivant permet d'implémenter le modèle abstract factory :

```python
class Window:
    __toolkit = ""
    __purpose = ""

    def __init__(self, toolkit, purpose):
        self.__toolkit = toolkit
        self.__purpose = purpose
    
    def getToolkit(self):
        return self.__toolkit
    
    def getType(self):
        return self.__purpose

class GtkToolboxWindow(Window):
    def __init__(self):
        Window.__init__(self, "Gtk", "ToolboxWindow")

class GtkLayersWindow(Window):
    def __init__(self):
        Window.__init__(self, "Gtk", "LayersWindow")

class GtkMainWindow(Window):
    def __init__(self):
        Window.__init__(self, "Gtk", "MainWindow")

class QtToolboxWindow(Window):
    def __init__(self):
        Window.__init__(self, "Qt", "ToolboxWindow")

class QtLayersWindow(Window):
    def __init__(self):
        Window.__init__(self, "Qt", "LayersWindow")

class QtMainWindow(Window):
    def __init__(self):
        Window.__init__(self, "Qt", "MainWindow")

# Abstract factory class
class UIFactory:
    def getToolboxWindow(self): pass
    def getLayersWindow(self): pass
    def getMainWindow(self): pass

class GtkUIFactory(UIFactory):
    def getToolboxWindow(self):
        return GtkToolboxWindow()
    def getLayersWindow(self):
        return GtkLayersWindow()
    def getMainWindow(self):
        return GtkMainWindow()

class QtUIFactory(UIFactory):
    def getToolboxWindow(self):
        return QtToolboxWindow()
    def getLayersWindow(self):
        return QtLayersWindow()
    def getMainWindow(self):
        return QtMainWindow()

if __name__ == "__main__":
    gnome = True
    kde = not gnome

    if gnome:
        ui = GtkUIFactory()
    elif kde:
        ui = QtUIFactory()

    toolbox = ui.getToolboxWindow()
    layers = ui.getLayersWindow()
    main = ui.getMainWindow()

    print("%s:%s" % (toolbox.getToolkit(), toolbox.getType()))
    print("%s:%s" % (layers.getToolkit(), layers.getType()))
    print("%s:%s" % (main.getToolkit(), main.getType()))
```

### Réponse

Le programme ci-dessus génère la réponse suivante :

```bash
Gtk:ToolboxWindow
Gtk:LayersWindow
Gtk:MainWindow
```

### Explication

Dans le programme ci-dessus, la fabrique abstraite crée des objets pour chaque fenêtre. Elle appelle pour chaque méthode, qui exécute la réponse comme prévu.
