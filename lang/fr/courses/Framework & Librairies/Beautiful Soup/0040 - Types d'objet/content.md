## Introduction

Lorsque nous passons un document html ou une chaîne de caractères à un constructeur de beautifulsoup, beautifulsoup convertit essentiellement une page html complexe en différents objets python. Ci-dessous, nous allons discuter de quatre types d'objets principaux :

- Tag
- NavigableString
- BeautifulSoup
- Comments

### Tag Objects

Un tag HTML est utilisé pour définir différents types de contenu. Un objet tag dans BeautifulSoup correspond à un tag HTML ou XML dans la page ou le document actuel.

```python
>>> from bs4 import BeautifulSoup
>>> soup = BeautifulSoup('<b class="boldest">Microlead</b>')
>>> tag = soup.html
>>> type(tag)
<class 'bs4.element.Tag'>
```

Les balises contiennent beaucoup d'attributs et de méthodes. Les deux caractéristiques importantes d'une balise sont son nom et ses attributs.

### Name (tag.name)

Chaque balise contient un nom et est accessible par le suffixe '.name'. tag.name renvoie le type de balise dont il s'agit.

```python
>>> tag.name
'html'
```

Cependant, si nous changeons le nom de la balise, cela se reflétera dans le balisage HTML généré par BeautifulSoup.

```python
>>> tag.name = "Strong"
>>> tag
<Strong><body><b class="boldest">Microlead</b></body></Strong>
>>> tag.name
'Strong'
```

## Attributes (tag.attrs)

Un objet balise peut avoir un nombre quelconque d'attributs. La balise ```<b class="boldest">``` possède un attribut 'class' dont la valeur est "boldest". Tout ce qui n'est PAS une balise, est fondamentalement un attribut et doit contenir une valeur. Vous pouvez accéder aux attributs soit en accédant aux clés (comme l'accès à "class" dans l'exemple ci-dessus), soit directement en accédant à ".attrs".

```python
>>> Microlead = BeautifulSoup("<div class='Microlead'></div>",'lxml')
>>> tag2 = Microlead.div
>>> tag2['class']
['Microlead']
```

Nous pouvons apporter toutes sortes de modifications aux attributs de nos balises (ajouter/supprimer/modifier).

```bash
>>> tag2['class'] = 'E-Learning'
>>> tag2['style'] = '2007'
>>>
>>> tag2
<div class="E-Learning" style="2007"></div>
>>> del tag2['style']
>>> tag2
<div class="E-Learning"></div>
>>> del tag['class']
>>> tag
<b SecondAttribute="2">Microlead</b>
>>>
>>> del tag['SecondAttribute']
>>> tag
</b>
>>> tag2['class']
'E-Learning'
>>> tag2['style']
KeyError: 'style'
```

## Multi-valued attributes

Certains des attributs HTML5 peuvent avoir plusieurs valeurs. Le plus couramment utilisé est l'attribut "class", qui peut avoir plusieurs valeurs CSS. Les autres attributs sont 'rel', 'rev', 'headers', 'accesskey' et 'accept-charset'. Les attributs à valeurs multiples dans beautiful soup sont présentés sous forme de liste.

```python
>>> from bs4 import BeautifulSoup
>>>
>>> css_soup = BeautifulSoup('<p class="body"></p>')
>>> css_soup.p['class']
['body']
>>>
>>> css_soup = BeautifulSoup('<p class="body bold"></p>')
>>> css_soup.p['class']
['body', 'bold']
```

Toutefois, si un attribut contient plus d'une valeur mais qu'il ne s'agit pas d'un attribut multivalent selon une version quelconque de la norme HTML, la belle soupe laissera l'attribut intact.

```python
>>> id_soup = BeautifulSoup('<p id="body bold"></p>')
>>> id_soup.p['id']
'body bold'
>>> type(id_soup.p['id'])
<class 'str'>
```

Vous pouvez consolider plusieurs valeurs d'attributs si vous transformez une balise en chaîne.

```python
>>> rel_soup = BeautifulSoup("<p> Microlead Main <a rel='Index'> Page</a></p>")
>>> rel_soup.a['rel']
['Index']
>>> rel_soup.a['rel'] = ['Index', ' Online Library, Its all Free']
>>> print(rel_soup.p)
<p> Microlead Main <a rel="Index Online Library, Its all Free"> Page</a></p>
```

En utilisant 'get_attribute_list', vous obtenez une valeur qui est toujours une liste, une chaîne, indépendamment du fait qu'il s'agisse d'une valeur multiple ou non.

```python
id_soup.p.get_attribute_list('id')
```

Toutefois, si vous analysez le document en tant que "xml", il n'y a pas d'attributs à valeurs multiples.

```python
>>> xml_soup = BeautifulSoup('<p class="body bold"></p>', 'xml')
>>> xml_soup.p['class']
'body bold'
```

## NavigableString

L'objet navigablestring est utilisé pour représenter le contenu d'une balise. Pour accéder au contenu, utilisez ".string" avec la balise.

```python
>>> from bs4 import BeautifulSoup
>>> soup = BeautifulSoup("<h2 id='message'>Hello, Microlead!</h2>")
>>>
>>> soup.string
'Hello, Microlead!'
>>> type(soup.string)
>
```

Vous pouvez remplacer la chaîne par une autre chaîne, mais vous ne pouvez pas modifier la chaîne existante.

```python
>>> soup = BeautifulSoup("<h2 id='message'>Hello, Microlead!</h2>")
>>> soup.string.replace_with("Online Learning!")
'Hello, Microlead!'
>>> soup.string
'Online Learning!'
>>> soup
<html><body><h2 id="message">Online Learning!</h2></body></html>
```

## BeautifulSoup

BeautifulSoup est l'objet créé lorsque nous essayons d'extraire une ressource web. Il s'agit donc du document complet que nous essayons d'extraire. La plupart du temps, il est traité comme un objet tag.

```python
>>> from bs4 import BeautifulSoup
>>> soup = BeautifulSoup("<h2 id='message'>Hello, Microlead!</h2>")
>>> type(soup)
<class 'bs4.BeautifulSoup'>
>>> soup.name
'[document]'
```

## Commentaires

L'objet commentaire illustre la partie commentaire du document Web. Il s'agit simplement d'un type spécial de NavigableString.

```python
>>> soup = BeautifulSoup('<p><!-- Everything inside it is COMMENTS --></p>')
>>> comment = soup.p.string
>>> type(comment)
<class 'bs4.element.Comment'>
>>> type(comment)
<class 'bs4.element.Comment'>
>>> print(soup.p.prettify())
<p>
<!-- Everything inside it is COMMENTS -->
</p>
```