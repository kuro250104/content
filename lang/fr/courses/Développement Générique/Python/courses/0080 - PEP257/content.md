Le but de ce PEP est de standardiser la structure de haut niveau des docstrings : ce qu'ils doivent contenir et comment le dire (sans toucher à la syntaxe du balisage dans les docstrings). Le PEP contient des conventions, et non des lois ou une syntaxe.

> "Une convention universelle fournit tout ce qui est maintenabilité, clarté, cohérence, et une base pour de bonnes habitudes de programmation aussi. Ce qu'elle ne fait pas, c'est insister pour que vous la suiviez contre votre volonté. C'est Python !"
> 
> -- Tim Peters sur comp.lang.python, 2001-06-16

Si vous violez ces conventions, le pire que vous obtiendrez sera un mauvais regard. Mais certains logiciels (tels que le système de traitement des chaînes de caractères Docutils) connaissent les conventions, et les respecter vous permettra d'obtenir les meilleurs résultats.

## Que sont les docstrings ?

Une docstring est une chaîne de caractères littérale qui apparaît comme première déclaration dans un module, une fonction, une classe ou une définition de méthode. Une telle docstring devient l'attribut spécial ```__doc__``` de cet objet.

Tous les modules devraient normalement avoir des docstrings, et toutes les fonctions et classes exportées par un module devraient également avoir des docstrings. Les méthodes publiques (y compris le constructeur ```__init__```) doivent également avoir des docstrings. Un paquet peut être documenté dans la docstring du module du fichier ```__init__.py``` dans le répertoire du paquet.

Les chaînes de caractères qui apparaissent ailleurs dans le code Python peuvent également servir de documentation. Ils ne sont pas reconnus par le compilateur de bytecode Python et ne sont pas accessibles en tant qu'attributs d'objet d'exécution (c'est-à-dire qu'ils ne sont pas affectés à ```__doc__```), mais deux types de docstrings supplémentaires peuvent être extraits par des outils logiciels :

- Les littéraux de chaîne de caractères apparaissant immédiatement après une simple affectation au niveau supérieur d'un module, d'une classe ou de la méthode ```__init__``` sont appelés docstrings d'attributs.
- Les chaînes de caractères qui se trouvent immédiatement après une autre chaîne de caractères sont appelées chaînes de caractères supplémentaires.

Pour des raisons de cohérence, utilisez toujours """des guillemets doubles triples"" autour des chaînes de caractères. Utilisez les """triples guillemets bruts"" si vous utilisez des antislashs dans vos chaînes de caractères. Pour les docstrings Unicode, utilisez ```u """chaînes Unicode à triple guillemets"""```.

Il existe deux formes de docstrings : les docstrings d'une ligne et les docstrings multilignes.

### Les docstrings d’une ligne

Les phrases d'une ligne sont pour les cas vraiment évidentes. Elles doivent vraiment tenir sur une ligne. Par exemple :

```python
def kos_root() :
    """Retourne le chemin du répertoire racine de KOS."""
    global _kos_root
    if _kos_root : return _kos_root
    # ...
```

Des guillemets triples sont utilisés même si la chaîne tient sur une seule ligne. Cela permet de l'étendre facilement par la suite.

Les guillemets fermants sont sur la même ligne que les guillemets ouvrants. C'est mieux pour les phrases d'une ligne.

Il n'y a pas de ligne vierge avant ou après la chaîne de caractères.

La docstring est une phrase qui se termine par un point. Elle prescrit l'effet de la fonction ou de la méthode en tant que commande ("Fais ceci", "Renvoie cela"), et non en tant que description ; par exemple, n'écrivez pas "Renvoie le nom de chemin ...".

La docstring d'une ligne ne doit PAS être une "signature" répétant les paramètres de la fonction/méthode (qui peuvent être obtenus par introspection). Ne le faites pas :

```python
def function(a, b) :
    """function(a, b) -> liste"""
```

Ce type de docstring n'est approprié que pour les fonctions C (comme les built-ins), où l'introspection n'est pas possible. Cependant, la nature de la valeur de retour ne peut pas être déterminée par introspection, elle doit donc être mentionnée. La forme préférée pour une telle docstring serait quelque chose comme :

```python
def function(a, b) :
    """Faire X et retourner une liste."""
```

(Bien sûr, "Faire X" devrait être remplacé par une description utile !)

### Docstrings multiligne

Les docstrings multi-lignes se composent d'une ligne de résumé, comme une docstring d'une ligne, suivie d'une ligne vierge, puis d'une description plus élaborée. La ligne de résumé peut être utilisée par les outils d'indexation automatique ; il est important qu'elle tienne sur une ligne et qu'elle soit séparée du reste de la docstring par une ligne vide. La ligne de résumé peut être sur la même ligne que les guillemets d'ouverture ou sur la ligne suivante. La docstring entière est indentée de la même manière que les guillemets à sa première ligne (voir l'exemple ci-dessous).

Insérez une ligne vierge après toutes les docstrings (à une ou plusieurs lignes) qui documentent une classe - en général, les méthodes de la classe sont séparées les unes des autres par une seule ligne vierge, et la docstring doit être décalée de la première méthode par une ligne vierge.

La docstring d'un script (un programme autonome) devrait être utilisable comme message d'utilisation, imprimé lorsque le script est invoqué avec des arguments incorrects ou manquants (ou peut-être avec une option "-h", pour "help"). Une telle docstring devrait documenter la fonction du script et la syntaxe de la ligne de commande, les variables d'environnement et les fichiers. Les messages d'utilisation peuvent être assez élaborés (plusieurs écrans complets) et devraient être suffisants pour qu'un nouvel utilisateur puisse utiliser la commande correctement, ainsi qu'une référence rapide et complète à toutes les options et arguments pour l'utilisateur averti.

La docstring d'un module doit généralement lister les classes, exceptions et fonctions (et tout autre objet) qui sont exportées par le module, avec un résumé d'une ligne pour chacune. (Ces résumés donnent généralement moins de détails que la ligne de résumé dans la docstring de l'objet). La docstring d'un paquet (c'est-à-dire la docstring du module ```__init__.py``` du paquet) doit également énumérer les modules et sous-paquets exportés par le paquet.

La docstring d'une fonction ou d'une méthode doit résumer son comportement et documenter ses arguments, sa (ses) valeur(s) de retour, ses effets secondaires, les exceptions soulevées et les restrictions sur le moment où elle peut être appelée (le tout si applicable). Les arguments facultatifs doivent être indiqués. Il convient de documenter si les arguments des mots-clés font partie de l'interface.

La docstring d'une classe doit résumer son comportement et énumérer les méthodes publiques et les variables d'instance. Si la classe est destinée à être sous-classée et possède une interface supplémentaire pour les sous-classes, cette interface doit être indiquée séparément (dans la docstring). Le constructeur de la classe doit être documenté dans la docstring de sa méthode ```__init__```. Les méthodes individuelles doivent être documentées par leur propre docstring.

Si une classe sous-classe une autre classe et que son comportement est principalement hérité de cette dernière, sa docstring doit le mentionner et résumer les différences. Utilisez le verbe "override" pour indiquer qu'une méthode de sous-classe remplace une méthode de super-classe et n'appelle pas la méthode de super-classe ; utilisez le verbe "extend" pour indiquer qu'une méthode de sous-classe appelle la méthode de super-classe (en plus de son propre comportement).

N'utilisez pas la convention Emacs consistant à mentionner les arguments des fonctions ou des méthodes en majuscules dans le texte courant. Python est sensible à la casse et les noms des arguments peuvent être utilisés pour les arguments des mots-clés, la docstring doit donc documenter les noms corrects des arguments. Il est préférable de lister chaque argument sur une ligne séparée. Par exemple

```python
def complex(real=0.0, imag=0.0) :
    """Forme un nombre complexe.
    Arguments par mot-clé :
    real -- la partie réelle (par défaut 0.0)
    imag -- la partie imaginaire (par défaut 0.0)
    """
    if imag == 0.0 and real == 0.0 :
        return complex_zero
```

A moins que la docstring entière ne tienne sur une ligne, placez les guillemets fermants sur une ligne par eux-mêmes. De cette façon, la commande fill-paragraph d'Emacs peut être utilisée.

## Traitement de l’indentation de la docstring

Les outils de traitement de la docstring enlèveront une quantité uniforme d'indentation de la deuxième ligne et des lignes suivantes de la docstring, égale à l'indentation minimale de toutes les lignes non vides après la première ligne. Toute indentation dans la première ligne de la docstring (c'est-à-dire jusqu'à la première nouvelle ligne) est insignifiante et supprimée. L'indentation relative des lignes ultérieures de la docstring est conservée. Les lignes vides doivent être supprimées au début et à la fin de la docstring.

Le code étant beaucoup plus précis que les mots, voici une implémentation de l'algorithme :

```python
def trim(docstring) :

    if not docstring :
        return ''

    # Convertir les tabulations en espaces (selon les règles normales de Python)
    # et diviser en une liste de lignes :
    lines = docstring.expandtabs().splitlines()

    # Déterminer l'indentation minimale (la première ligne ne compte pas) :
    indent = sys.maxint

    for line in lines[1:]:
        dépouille = line.lstrip()

        if dépouille :
            indent = min(indent, len(line) - len(stripped))

    # Enlever l'indentation (la première ligne est spéciale) :
    trimmed = [lines[0].strip()]

    if indent < sys.maxint :
        for line in lines[1 :]:
            trimmed.append(line[indent :].rstrip())

    # Supprimez les lignes vides de queue et de tête :
    while trimmed and not trimmed[-1] :
        trimmed.pop()

    while trimmed et non trimmed[0] :
        trimmed.pop(0)

    # Retourne une seule chaîne de caractères :
    return '\n'.join(trimmed)
```

La docstring de cet exemple contient deux caractères de saut de ligne et est donc longue de 3 lignes. La première et la dernière ligne sont vides :

```python
def foo() :
    """
    Voici la deuxième ligne de la docstring.
    """
```

Pour illustrer :

```python
>>> print repr(foo.__doc__)
'\n C'est la deuxième ligne de la chaîne documentaire.\n '
>>> foo.__doc__.splitlines()
['', ' C'est la deuxième ligne de la chaîne documentaire.', ' ']
>>> trim(foo.__doc__)
Ceci est la deuxième ligne de la chaîne documentaire.
```

Une fois découpées, ces docstrings sont équivalentes :

```python
def foo() :
    """Une chaîne de caractères
    multi-lignes.
    """

def bar() :
    """
    Une chaîne de caractères
    multi-ligne.
    """
```