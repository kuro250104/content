Le XML est un langage portable et libre qui permet aux programmeurs de développer des applications pouvant être lues par d'autres applications, indépendamment du système d'exploitation et/ou de la langue de développement.

## Qu'est-ce que le XML ?

Le langage de balisage extensible (XML) est un langage de balisage semblable au HTML ou au SGML. Il est recommandé par le World Wide Web Consortium et disponible en tant que norme ouverte.

Le XML est extrêmement utile pour assurer le suivi de petites et moyennes quantités de données sans avoir besoin d'une base de données SQL.

## Architectures et API de l'analyseur XML

La bibliothèque standard de Python fournit un ensemble minimal mais utile d'interfaces pour travailler avec XML.

Les deux API les plus basiques et les plus largement utilisées pour les données XML sont les interfaces SAX et DOM.

- **Simple API for XML (SAX)** − Ici, vous enregistrez des rappels pour les événements intéressants, puis vous laissez l'analyseur syntaxique parcourir le document. C'est utile lorsque vos documents sont volumineux ou que vous avez des limitations de mémoire, il analyse le fichier au fur et à mesure qu'il le lit sur le disque et le fichier entier n'est jamais stocké en mémoire.
- **Document Object Model (DOM) API** − Il s'agit d'une recommandation du World Wide Web Consortium dans laquelle le fichier entier est lu dans la mémoire et stocké sous une forme hiérarchique (arborescente) pour représenter toutes les caractéristiques d'un document XML.

SAX ne peut évidemment pas traiter l'information aussi rapidement que DOM, lorsqu'on travaille avec de gros fichiers. D'autre part, l'utilisation exclusive de DOM peut vraiment tuer vos ressources, surtout si elle est utilisée sur de nombreux petits fichiers.

SAX est en lecture seule, alors que DOM permet de modifier le fichier XML. Étant donné que ces deux API différentes se complètent littéralement, il n'y a aucune raison pour que vous ne puissiez pas les utiliser toutes les deux pour de grands projets.

Pour tous nos exemples de code XML, utilisons un simple fichier XML movies.xml comme entrée :

```xml
<collection shelf = "New Arrivals">
<movie title = "Enemy Behind">
    <type>War, Thriller</type>
    <format>DVD</format>
    <year>2003</year>
    <rating>PG</rating>
    <stars>10</stars>
    <description>Talk about a US-Japan war</description>
</movie>
<movie title = "Transformers">
    <type>Anime, Science Fiction</type>
    <format>DVD</format>
    <year>1989</year>
    <rating>R</rating>
    <stars>8</stars>
    <description>A schientific fiction</description>
</movie>
    <movie title = "Trigun">
    <type>Anime, Action</type>
    <format>DVD</format>
    <episodes>4</episodes>
    <rating>PG</rating>
    <stars>10</stars>
    <description>Vash the Stampede!</description>
</movie>
<movie title = "Ishtar">
    <type>Comedy</type>
    <format>VHS</format>
    <rating>PG</rating>
    <stars>2</stars>
    <description>Viewable boredom</description>
</movie>
</collection>
```

## Analyser le XML avec les API SAX

SAX est une interface standard pour l'analyse syntaxique XML pilotée par des événements. L'analyse du XML avec SAX nécessite généralement la création de votre propre ContentHandler en sous-classant ```xml.sax.ContentHandler```.

Votre ```ContentHandler``` gère les balises et attributs particuliers de votre ou vos saveurs de XML. Un objet ```ContentHandler``` fournit des méthodes pour gérer divers événements d'analyse. L'analyseur qui lui appartient appelle les méthodes ```ContentHandler``` lorsqu'il analyse le fichier XML.

Les méthodes startDocument et endDocument sont appelées au début et à la fin du fichier XML. La méthode ```characters(text)``` reçoit les données de caractères du fichier XML via le paramètre text.

Le ```ContentHandler``` est appelé au début et à la fin de chaque élément. Si l'analyseur syntaxique n'est pas en mode espace de noms, les méthodes ```startElement(tag, attributes)``` et ```endElement(tag)``` sont appelées ; sinon, les méthodes correspondantes ```startElementNS``` et ```endElementNS``` sont appelées. Ici, tag est la balise de l'élément, et attributes est un objet Attributes.

Voici d'autres méthodes importantes à comprendre avant de poursuivre :

### La méthode make_parser

La méthode suivante crée un nouvel objet analyseur et le renvoie. L'objet d'analyse créé sera du premier type d'analyseur trouvé par le système.

```python
xml.sax.make_parser([parser_list])
```

Voici le détail des paramètres :

- ```parser_list``` − L'argument optionnel consistant en une liste d'analyseurs syntaxiques à utiliser qui doivent tous implémenter la méthode make_parser.

### La méthode parse

La méthode suivante crée un analyseur SAX et l'utilise pour analyser un document.

```python
xml.sax.parse(xmlfile, contenthandler[, errorhandler])
```

Voici le détail des paramètres :

- ```xmlfile``` - Il s'agit du nom du fichier XML à lire.
- ```contenthandler``` - Il doit s'agir d'un objet ContentHandler.
- ```errorhandler``` - S'il est spécifié, errorhandler doit être un objet SAX ErrorHandler.

### La méthode parseString

Il existe une autre méthode pour créer un analyseur SAX et analyser la **chaîne XML** spécifiée.

```python
xml.sax.parseString(xmlstring, contenthandler[, errorhandler])
```

Voici le détail des paramètres :

- ```xmlstring``` - Il s'agit du nom de la chaîne XML à lire.
- ```contenthandler``` - Il doit s'agir d'un objet ContentHandler.
- ```errorhandler``` - S'il est spécifié, errorhandler doit être un objet SAX ErrorHandler.

#### Exemple

```python
#!/usr/bin/python3

import xml.sax

class MovieHandler( xml.sax.ContentHandler ):
    def __init__(self):
        self.CurrentData = ""
        self.type = ""
        self.format = ""
        self.year = ""
        self.rating = ""
        self.stars = ""
        self.description = ""

    # Call when an element starts
    def startElement(self, tag, attributes):
        self.CurrentData = tag
        if tag == "movie":
            print("*****Movie*****")
            title = attributes["title"]
            print("Title:", title)

    # Call when an elements ends
    def endElement(self, tag):
        if self.CurrentData == "type":
            print("Type:", self.type)
        elif self.CurrentData == "format":
            print("Format:", self.format)
        elif self.CurrentData == "year":
            print("Year:", self.year)
        elif self.CurrentData == "rating":
            print("Rating:", self.rating)
        elif self.CurrentData == "stars":
            print("Stars:", self.stars)
        elif self.CurrentData == "description":
            print("Description:", self.description)
        self.CurrentData = ""

    # Call when a character is read
    def characters(self, content):
        if self.CurrentData == "type":
            self.type = content
        elif self.CurrentData == "format":
            self.format = content
        elif self.CurrentData == "year":
            self.year = content
        elif self.CurrentData == "rating":
            self.rating = content
        elif self.CurrentData == "stars":
            self.stars = content
        elif self.CurrentData == "description":
            self.description = content

if ( __name__ == "__main__"):

    # create an XMLReader
    parser = xml.sax.make_parser()
    # turn off namepsaces
    parser.setFeature(xml.sax.handler.feature_namespaces, 0)

    # override the default ContextHandler
    Handler = MovieHandler()
    parser.setContentHandler(Handler)

    parser.parse("movies.xml")
```

#### Résultat

Cela donnerait le résultat suivant :

```bash
*****Movie*****
Title: Enemy Behind
Type: War, Thriller
Format: DVD
Year: 2003
Rating: PG
Stars: 10
Description: Talk about a US-Japan war
*****Movie*****
Title: Transformers
Type: Anime, Science Fiction
Format: DVD
Year: 1989
Rating: R
Stars: 8
Description: A scientific fiction
*****Movie*****
Title: Trigun
Type: Anime, Action
Format: DVD
Rating: PG
Stars: 10
Description: Vash the Stampede!
*****Movie*****
Title: Ishtar
Type: Comedy
Format: VHS
Rating: PG
Stars: 2
Description: Viewable boredom
```

## Analyser le XML avec les API DOM

Le Document Object Model ("DOM") est une API multi-langue du World Wide Web Consortium (W3C) pour accéder et modifier les documents XML.

Le DOM est extrêmement utile pour les applications à accès aléatoire. SAX ne vous permet de voir qu'une partie du document à la fois. Si vous regardez un élément SAX, vous n'avez pas accès à un autre.

Le moyen le plus simple de charger rapidement un document XML est de créer un objet minidom à l'aide du module xml.dom. L'objet minidom fournit une méthode d'analyse simple qui crée rapidement un arbre DOM à partir du fichier XML.

L'exemple de phrase appelle la fonction parse(file[,parser]) de l'objet minidom pour analyser le fichier XML, désigné par file dans un objet DOM tree.

### Exemple

```python
#!/usr/bin/python3

from xml.dom.minidom import parse
import xml.dom.minidom

# Open XML document using minidom parser
DOMTree = xml.dom.minidom.parse("movies.xml")
collection = DOMTree.documentElement
if collection.hasAttribute("shelf"):
    print("Root element : %s" % collection.getAttribute("shelf"))

# Get all the movies in the collection
movies = collection.getElementsByTagName("movie")

# Print detail of each movie.
for movie in movies:
    print("*****Movie*****")
    if movie.hasAttribute("title"):
        print("Title: %s" % movie.getAttribute("title"))

    type = movie.getElementsByTagName('type')[0]
    print("Type: %s" % type.childNodes[0].data)
    format = movie.getElementsByTagName('format')[0]
    print("Format: %s" % format.childNodes[0].data)
    rating = movie.getElementsByTagName('rating')[0]
    print("Rating: %s" % rating.childNodes[0].data)
    description = movie.getElementsByTagName('description')[0]
    print("Description: %s" % description.childNodes[0].data)
```

### Résultat

Cela donnerait le résultat suivant :

```bash
Root element : New Arrivals
*****Movie*****
Title: Enemy Behind
Type: War, Thriller
Format: DVD
Rating: PG
Description: Talk about a US-Japan war
*****Movie*****
Title: Transformers
Type: Anime, Science Fiction
Format: DVD
Rating: R
Description: A scientific fiction
*****Movie*****
Title: Trigun
Type: Anime, Action
Format: DVD
Rating: PG
Description: Vash the Stampede!
*****Movie*****
Title: Ishtar
Type: Comedy
Format: VHS
Rating: PG
Description: Viewable boredom
```
