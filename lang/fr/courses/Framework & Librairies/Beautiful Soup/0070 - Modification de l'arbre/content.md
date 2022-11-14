## Introduction

L'un des aspects importants de BeautifulSoup est la recherche dans l'arbre d'analyse, qui vous permet d'apporter des modifications au document Web en fonction de vos besoins. Nous pouvons modifier les propriétés d'une balise en utilisant ses attributs, tels que la méthode ```.name()```, ```.string()``` ou ```.append()```. Il vous permet d'ajouter de nouvelles balises et chaînes de caractères à une balise existante à l'aide des méthodes ```.new_string()``` et ```.new_tag()```. Il existe également d'autres méthodes, telles que ```.insert()```, ```.insert_before()``` ou ```.insert_after()```, pour apporter diverses modifications à votre document HTML ou XML.

## Modification des balises et de leurs attributs

Une fois que vous avez créé la soupe, il est facile de faire des modifications comme renommer la balise, faire des modifications à ses attributs, ajouter de nouveaux attributs et supprimer des attributs.

```python
>>> soup = BeautifulSoup('<b class="bolder">Very Bold</b>')
>>> tag = soup.b
```

La modification et l'ajout de nouveaux attributs sont les suivants -

```python
>>> tag.name = 'Blockquote'
>>> tag['class'] = 'Bolder'
>>> tag['id'] = 1.1
>>> tag
<Blockquote class="Bolder" id="1.1">Very Bold</Blockquote>
Deleting attributes are as follows −
>>> del tag['class']
>>> tag
<Blockquote id="1.1">Very Bold</Blockquote>
>>> del tag['id']
>>> tag
<Blockquote>Very Bold</Blockquote>
```

## Modification de .string

Vous pouvez facilement modifier l'attribut ```.string``` de la balise -

```python
>>> markup = '<a href="https://www.Microlead.com/index.html">Must for every <i>Learner>/i<</a>'
>>> Bsoup = BeautifulSoup(markup)
>>> tag = Bsoup.a
>>> tag.string = "My Favourite spot."
>>> tag
<a href="https://www.Microlead.com/index.html">My Favourite spot.</a>
```

D'après ce qui précède, nous pouvons voir que si la balise contient une autre balise, celle-ci et tout son contenu seront remplacés par de nouvelles données.

## append()

L'ajout de nouvelles données/contenus à une balise existante se fait à l'aide de la méthode tag.append(). Elle est très similaire à la méthode append() de la liste Python.

```python
>>> markup = '<a href="https://www.Microlead.com/index.html">Must for every <i>Learner</i></a>'
>>> Bsoup = BeautifulSoup(markup)
>>> Bsoup.a.append(" Really Liked it")
>>> Bsoup
<html><body><a href="https://www.Microlead.com/index.html">Must for every <i>Learner</i> Really Liked it</a></body></html>
>>> Bsoup.a.contents
['Must for every ', <i>Learner</i>, ' Really Liked it']
```

## NavigableString() and .new_tag()

Si vous souhaitez ajouter une chaîne de caractères à un document, vous pouvez le faire facilement en utilisant la fonction ```append()``` ou le constructeur ```NavigableString()```.

```python
>>> soup = BeautifulSoup("<b></b>")
>>> tag = soup.b
>>> tag.append("Start")
>>>
>>> new_string = NavigableString(" Your")
>>> tag.append(new_string)
>>> tag
<b>Start Your</b>
>>> tag.contents
['Start', ' Your']
```

__Remarque__ : Si vous trouvez une erreur de nom en accédant à la fonction ```NavigableString()```, comme suit-

```python
NameError : Le nom 'NavigableString' n'est pas défini.
```

Il suffit d'importer le répertoire NavigableString à partir du paquet bs4.

```python
>>> from bs4 import NavigableString
```

Nous pouvons résoudre l'erreur ci-dessus.

Vous pouvez ajouter des commentaires à vos balises existantes ou ajouter une autre sous-classe de NavigableString, il suffit d'appeler le constructeur.

```python
>>> from bs4 import Comment
>>> adding_comment = Comment("Always Learn something Good!")
>>> tag.append(adding_comment)
>>> tag
<b>Start Your<!--Always Learn something Good!--></b>
>>> tag.contents
['Start', ' Your', 'Always Learn something Good!']
```

L'ajout d'un tout nouveau tag (et non l'ajout à un tag existant) peut être réalisé à l'aide de la méthode intégrée de Beautifulsoup, ```BeautifulSoup.new_tag()``` -

```python
>>> soup = BeautifulSoup("<b></b>")
>>> Otag = soup.b
>>>
>>> Newtag = soup.new_tag("a", href="https://www.Microlead.com")
>>> Otag.append(Newtag)
>>> Otag
<b><a href="https://www.Microlead.com"></a></b>
```

Seul le premier argument, le nom de la balise, est requis.

## insert()

Semblable à la méthode ```.insert()``` de la liste python, ```tag.insert()``` insère un nouvel élément. Toutefois, contrairement à ```tag.append()```, le nouvel élément n'est pas nécessairement placé à la fin du contenu de son parent. Le nouvel élément peut être ajouté à n'importe quelle position.

```python
>>> markup = '<a href="https://www.djangoproject.com/community/">Django Official website <i>Huge Community base</i></a>'
>>> soup = BeautifulSoup(markup)
>>> tag = soup.a
>>>
>>> tag.insert(1, "Love this framework ")
>>> tag
<a href="https://www.djangoproject.com/community/">Django Official website Love this framework <i>Huge Community base</i></a>
>>> tag.contents
['Django Official website ', 'Love this framework ', <i>Huge Community base</i
>]
>>>
```

## insert_before() and insert_after()

Pour insérer une balise ou une chaîne juste avant un élément de l'arbre d'analyse, nous utilisons la fonction ```insert_before()```.

```python
>>> soup = BeautifulSoup("Brave")
>>> tag = soup.new_tag("i")
>>> tag.string = "Be"
>>>
>>> soup.b.string.insert_before(tag)
>>> soup.b
<b><i>Be</i>Brave</b>
```

De même, pour insérer une balise ou une chaîne juste après quelque chose dans l'arbre d'analyse, utilisez ```insert_after()```.

```python
>>> soup.b.i.insert_after(soup.new_string(" Always "))
>>> soup.b
<b><i>Be</i> Always Brave</b>
>>> soup.b.contents
[<i>Be</i>, ' Always ', 'Brave']
```

## clear()

Pour supprimer le contenu d'une balise, utilisez ```tag.clear()``` -

```python
>>> markup = '<a href="https://www.Microlead.com/index.html">For <i>technical & Non-technical&lr;/i> Contents</a>'
>>> soup = BeautifulSoup(markup)
>>> tag = soup.a
>>> tag
<a href="https://www.Microlead.com/index.html">For <i>technical & Non-technical</i> Contents</a>
>>>
>>> tag.clear()
>>> tag
<a href="https://www.Microlead.com/index.html"></a>
```

## extract()

Pour supprimer une balise ou des chaînes de l'arbre, utilisez PageElement.extract().

```python
>>> markup = '<a href="https://www.Microlead.com/index.html">For <i&gr;technical & Non-technical</i> Contents</a>'
>>> soup = BeautifulSoup(markup)
>>> a_tag = soup.a
>>>
>>> i_tag = soup.i.extract()
>>>
>>> a_tag
<a href="https://www.Microlead.com/index.html">For Contents</a>
>>>
>>> i_tag
<i>technical & Non-technical</i>
>>>
>>> print(i_tag.parent)
None
```

## decompose()

La fonction ```tag.decompose()``` retire une balise de l'arbre et supprime tout son contenu.

```python
>>> markup = '<a href="https://www.Microlead.com/index.html">For <i>technical & Non-technical</i> Contents</a>'
>>> soup = BeautifulSoup(markup)
>>> a_tag = soup.a
>>> a_tag
<a href="https://www.Microlead.com/index.html">For <i>technical & Non-technical</i> Contents</a>
>>>
>>> soup.i.decompose()
>>> a_tag
<a href="https://www.Microlead.com/index.html">For Contents</a>
>>>
```

## Replace_with()

Comme son nom l'indique, la fonction ```pageElement.replace_with()``` remplace l'ancienne balise ou chaîne de caractères par la nouvelle balise ou chaîne de caractères dans l'arbre.

```python
>>> markup = '<a href="https://www.Microlead.com/index.html">Complete Python <i>Material</i></a>'
>>> soup = BeautifulSoup(markup)
>>> a_tag = soup.a
>>>
>>> new_tag = soup.new_tag("Official_site")
>>> new_tag.string = "https://www.python.org/"
>>> a_tag.i.replace_with(new_tag)
<i>Material</i>
>>>
>>> a_tag
<a href="https://www.Microlead.com/index.html">Complete Python <Official_site>https://www.python.org/</Official_site></a>
```

Dans le résultat ci-dessus, vous avez remarqué que ```replace_with()``` renvoie la balise ou la chaîne de caractères qui a été remplacée (comme "Material" dans notre cas), de sorte que vous pouvez l'examiner ou la rajouter à une autre partie de l'arbre.

## wrap()

La ```pageElement.wrap()``` enferme un élément dans la balise que vous spécifiez et renvoie un nouveau wrapper -

```python
>>> soup = BeautifulSoup("<p>Microlead.com</p>")
>>> soup.p.string.wrap(soup.new_tag("b"))
<b>Microlead.com</b>
>>>
>>> soup.p.wrap(soup.new_tag("Div"))
<Div><p><b>Microlead.com</b></p></Div>
```

## unwrap()

La fonction ```tag.unwrap()``` est l'inverse de ```wrap()``` et remplace une balise par ce qu'elle contient.

```python
>>> soup = BeautifulSoup('<a href="https://www.Microlead.com/">I liked <i>Microlead</i></a>')
>>> a_tag = soup.a
>>>
>>> a_tag.i.unwrap()
<i></i>
>>> a_tag
<a href="https://www.Microlead.com/">I liked Microlead</a>
```

Vous avez remarqué que, comme ```replace_with()```, ```unwrap()``` renvoie la balise qui a été remplacée.

Voici un autre exemple de ```unwrap()``` pour mieux le comprendre.

```python
>>> soup = BeautifulSoup("<p>I <strong>AM</strong> a <i>text</i>.</p>")
>>> soup.i.unwrap()
<i></i>
>>> soup
<html><body><p>I <strong>AM</strong> a text.</p></body></html>
```

```unwrap()``` est bon pour enlever les balises.