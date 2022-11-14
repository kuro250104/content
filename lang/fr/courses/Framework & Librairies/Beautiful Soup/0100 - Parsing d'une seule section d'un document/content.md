## Introduction

Il existe de multiples situations où vous souhaitez extraire des types d'informations spécifiques (uniquement les balises <a>) à l'aide de Beautifulsoup4. La classe SoupStrainer de Beautifulsoup vous permet d'analyser uniquement une partie spécifique d'un document entrant.

Une façon de procéder est de créer un SoupStrainer et de le passer au constructeur de Beautifulsoup4 comme argument parse_only.

## SoupStrainer

Un SoupStrainer indique à BeautifulSoup les parties à extraire, et l'arbre d'analyse se compose uniquement de ces éléments. Si vous réduisez l'information requise à une partie spécifique du HTML, cela accélèrera le résultat de votre recherche.

```python
product = SoupStrainer('div',{'id': 'products_list'})
soup = BeautifulSoup(html,parse_only=product)
```

Les lignes de code ci-dessus analyserons uniquement les titres d'un site de produits, qui pourraient se trouver dans un champ de balises.

De même, comme ci-dessus, nous pouvons utiliser d'autres objets soupStrainer, pour analyser des informations spécifiques d'une balise HTML. Voici quelques exemples -

```python
from bs4 import BeautifulSoup, SoupStrainer

#Only "a" tags
only_a_tags = SoupStrainer("a")

#Will parse only the below mentioned "ids".
parse_only = SoupStrainer(id=["first", "third", "my_unique_id"])
soup = BeautifulSoup(my_document, "html.parser", parse_only=parse_only)

#parse only where string length is less than 10
def is_short_string(string):
    return len(string) < 10
only_short_strings =SoupStrainer(string=is_short_string)
```