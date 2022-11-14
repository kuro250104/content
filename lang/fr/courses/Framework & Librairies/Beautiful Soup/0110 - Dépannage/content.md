## Gestion d'erreurs

Il existe deux principaux types d'erreurs qui doivent être traitées dans BeautifulSoup. Ces deux erreurs ne proviennent pas de votre script mais de la structure du snippet car l'API BeautifulSoup lance une erreur.

Les deux erreurs principales sont les suivantes -

### AttributeError

Cette erreur se produit lorsque la notation par points ne trouve pas de balise sœur de la balise HTML actuelle. Par exemple, vous avez peut-être rencontré cette erreur, en raison de l'absence de "balise d'ancrage", cost-key lancera une erreur lorsqu'il parcourra et exigera une balise d'ancrage.

### KeyError

Cette erreur se produit si l'attribut de balise HTML requis est manquant. Par exemple, si l'attribut data-pid n'est pas présent dans un extrait, la clé pid provoquera une erreur de clé.

Pour éviter les deux erreurs mentionnées ci-dessus lors de l'analyse d'un résultat, ce résultat sera contourné pour s'assurer qu'un extrait mal formé n'est pas inséré dans les bases de données.

```python
except(AttributeError, KeyError) as er:
pass
```

## diagnose()

Chaque fois que nous avons des difficultés à comprendre ce que BeautifulSoup fait à notre document ou HTML, il suffit de le passer à la fonction ```diagnose()```. En passant le fichier document à la fonction ```diagnose()```, nous pouvons montrer comment la liste des différents parseurs traite le document.

Ci-dessous est un exemple pour démontrer l'utilisation de la fonction ```diagnose()```.

```python
from bs4.diagnose import diagnose

with open("20 Books.html",encoding="utf8") as fp:
    data = fp.read()

diagnose(data)
```


## Erreurs de Parsing

Il existe deux principaux types d'erreurs d'analyse. Vous pouvez obtenir une exception comme HTMLParseError, lorsque vous alimentez votre document à BeautifulSoup. Vous pouvez également obtenir un résultat inattendu, où l'arbre d'analyse de BeautifulSoup est très différent du résultat attendu du document d'analyse.

Aucune de ces erreurs d'analyse n'est causée par BeautifulSoup. Elle est due à l'analyseur externe que nous utilisons (html5lib, lxml) puisque BeautifulSoup ne contient pas de code d'analyseur. Une façon de résoudre l'erreur d'analyse ci-dessus est d'utiliser un autre analyseur.

```python
from HTMLParser import HTMLParser

try:
    from HTMLParser import HTMLParseError
except ImportError, e:
    # From python 3.5, HTMLParseError is removed. Since it can never be
    # thrown in 3.5, we can just define our own class as a placeholder.
    class HTMLParseError(Exception):
        pass
```

L'analyseur HTML intégré à Python provoque deux erreurs d'analyse les plus courantes, HTMLParser.HTMLParserError : malformed start tag et HTMLParser.HTMLParserError : bad end tag et pour résoudre cela, il faut utiliser un autre analyseur principalement : lxml ou html5lib.

Un autre type commun de comportement inattendu est que vous ne pouvez pas trouver une balise que vous savez être dans le document. Cependant, lorsque vous exécutez la fonction ```find_all()```, elle renvoie ```[]``` ou ```find()``` renvoie ```None```.

Cela peut être dû au fait que l'analyseur HTML intégré de python saute parfois des balises qu'il ne comprend pas.

## XML parser Error

Par défaut, le paquetage BeautifulSoup analyse les documents en tant que HTML, cependant, il est très facile à utiliser et traite le XML mal formé d'une manière très élégante en utilisant beautifulsoup4.

Pour analyser le document en tant que XML, vous devez avoir le parseur lxml et vous devez simplement passer le "xml" comme deuxième argument au constructeur de Beautifulsoup.

```python
soup = BeautifulSoup(markup, "lxml-xml")
```

ou

```python
soup = BeautifulSoup(markup, "xml")
```

Une erreur courante d'analyse XML est -

```python
AttributeError: 'NoneType' object has no attribute 'attrib'
```

Cela peut se produire dans le cas où un élément est manquant ou non défini lors de l'utilisation de la fonction find() ou findall().

## Other parsing errors

Voici quelques-unes des autres erreurs d'analyse syntaxique que nous allons aborder dans cette section.

### Environmental issue

En dehors des erreurs d'analyse mentionnées ci-dessus, vous pouvez rencontrer d'autres problèmes d'analyse tels que des problèmes d'environnement où votre script peut fonctionner dans un système d'exploitation mais pas dans un autre système d'exploitation ou peut fonctionner dans un environnement virtuel mais pas dans un autre environnement virtuel ou peut ne pas fonctionner en dehors de l'environnement virtuel. Tous ces problèmes peuvent être dus au fait que les deux environnements disposent de bibliothèques d'analyseurs différentes.

Il est recommandé de connaître ou de vérifier votre analyseur par défaut dans votre environnement de travail actuel. Vous pouvez vérifier l'analyseur par défaut disponible pour l'environnement de travail actuel ou bien passer explicitement la bibliothèque d'analyse requise comme deuxième argument au constructeur de BeautifulSoup.

### Case-insensitive

Comme les balises et attributs HTML ne sont pas sensibles à la casse, les trois analyseurs HTML convertissent les noms de balises et d'attributs en minuscules. Toutefois, si vous souhaitez conserver les balises et attributs en majuscules ou en minuscules, il est préférable d'analyser le document en XML.


### UnicodeEncodeError

Regardons le segment de code ci-dessous -

```python
soup = BeautifulSoup(response, "html.parser")
    print (soup)
```

Sortie :

```python
UnicodeEncodeError: 'charmap' codec can't encode character '\u011f'
```

Le problème ci-dessus peut être dû à deux situations principales. Vous essayez peut-être d'imprimer un caractère unicode que votre console ne sait pas comment afficher. Deuxièmement, vous essayez d'écrire dans un fichier et vous passez un caractère unicode qui n'est pas pris en charge par votre encodage par défaut.

Une façon de résoudre le problème ci-dessus est de coder le texte/caractère de la réponse avant de faire la soupe pour obtenir le résultat souhaité, comme suit -

```python
responseTxt = response.text.encode('UTF-8')
```

## KeyError: ```[attr]```

Elle est causée par l'accès à ```tag['attr']``` lorsque la balise en question ne définit pas l'attribut attr. Les erreurs les plus courantes sont : "KeyError : 'href'" et "KeyError : 'class'". Utilisez ```tag.get('attr')``` si vous n'êtes pas sûr que attr est défini.

```python
for item in soup.fetch('a'):
   try:
      if (item['href'].startswith('/') or "Microlead" in item['href']):
      (...)
   except KeyError:
      pass # or some other fallback action
```

## AttributeError

Vous pouvez rencontrer l'AttributeError comme suit -

```python
AttributeError: 'list' object has no attribute 'find_all'
```

L'erreur ci-dessus se produit principalement parce que vous vous attendiez à ce que ```find_all()``` renvoie une seule balise ou chaîne de caractères. Cependant, ```soup.find_all()``` renvoie une liste python d'éléments.

Tout ce que vous avez à faire est d'itérer dans la liste et d'attraper les données de ces éléments.