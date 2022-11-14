Dans ce chapitre, nous allons parler de la navigation par balises.

Voici notre document html -

```python
>>> html_doc = """
<html><head><title>Microlead</title></head>
<body>
<p class="title"><b>Les meilleurs cours en ligne, et gratuits !</b></p>
<p class="prog">Les 5 langages de programmation les plus utilisés sont :
<a href="https://www.microlead.fr/cours/php" class="prog" id="link1">PHP</a>,
<a href="https://www.microlead.fr/cours/javascript" class="prog" id="link2">Javascript</a>,
<a href="https://www.microlead.fr/cours/go" class="prog" id="link3">Go</a>,
<a href="https://www.microlead.fr/cours/html" class="prog" id="link4">HTML</a> et
<a href="https://www.microlead.fr/cours/css" class="prog" id="link5">CSS</a>;
selon l'enquête en ligne.</p>
<p class="prog">Langage de programmation</p>
"""
>>>
>>> from bs4 import BeautifulSoup
>>> soup = BeautifulSoup(html_doc, 'html.parser')
>>>
```

Sur la base du document ci-dessus, nous allons essayer de passer d'une partie du document à une autre.

## Descendre

Les balises, qui peuvent contenir d'autres balises/chaînes (enfants de la balise), constituent l'un des éléments importants de tout document HTML. Beautiful Soup propose différents moyens de naviguer et d'itérer sur les enfants d'une balise.

### Navigation en utilisant les noms des balises

La façon la plus simple de rechercher un arbre d'analyse est de rechercher la balise par son nom. Si vous voulez la balise ```<head>```, utilisez ```soup.head``` -

```python
>>> soup.head
<head>&t;title>Microlead</title></head>
>>> soup.title
<title>Microlead</title>
```

Pour obtenir une balise spécifique (comme la première balise ```<b>```) dans la balise ```<body>```.

```python
>>> soup.body.b
<b>Les meilleurs cours en ligne, et gratuits !</b>
```

Si vous utilisez le nom d'une balise comme attribut, vous obtiendrez uniquement la première balise portant ce nom.

```python
>>> soup.a
<a class="prog" href="https://www.microlead.fr/cours/php" id="link1">PHP</a>
```

Pour obtenir tous les attributs d'une balise, vous pouvez utiliser la méthode ```find_all()```.

```python
>>> soup.find_all("a")
[<a class="prog" href="https://www.microlead.fr/cours/php" id="link1">PHP</a>, <a class="prog" href="https://www.microlead.fr/cours/javascript" id="link2">C</a>, <a class="prog" href="https://www.microlead.fr/cours/html" id="link3">Python</a>, <a class="prog" href="https://www.microlead.fr/cours/css" id="link4">JavaScript</a>, <a class="prog" href="https://www.microlead.fr/cours/go" id="link5">C</a>]>>> soup.find_all("a")
[<a class="prog" href="https://www.microlead.fr/cours/php" id="link1">PHP</a>, <a class="prog" href="https://www.microlead.fr/cours/javascript" id="link2">C</a>, <a class="prog" href="https://www.microlead.fr/cours/html" id="link3">Python</a>, <a class="prog" href="https://www.microlead.fr/cours/css" id="link4">JavaScript</a>, <a class="prog" href="https://www.microlead.fr/cours/go" id="link5">C</a>]
```

### .contents et .children

Nous pouvons rechercher les enfants d'une balise dans une liste par son ```.contents -```.

```python
>>> head_tag = soup.head
>>> head_tag
<head><title>Microlead</title></head>
>>> Htag = soup.head
>>> Htag
<head><title>Microlead</title></head>
>>>
>>> Htag.contents
[<title>Microlead</title>
>>>
>>> Ttag = head_tag.contents[0]
>>> Ttag
<title>Microlead</title>
>>> Ttag.contents
['Microlead']
```

L'objet BeautifulSoup lui-même a des enfants. Dans ce cas, la balise ```<html>``` est l'enfant de l'objet BeautifulSoup.

```python
>>> len(soup.contents)
2
>>> soup.contents[1].name
'html'
```

Une chaîne de caractères n'a pas de contenu, car elle ne peut rien contenir.

```python
>>> text = Ttag.contents[0]
>>> text.contents
self.__class__.__name__, attr))
AttributeError: 'NavigableString' object has no attribute 'contents'
```

Au lieu de les obtenir sous forme de liste, utilisez le générateur ```.children``` pour accéder aux enfants de la balise -.

```python
>>> for child in Ttag.children:
print(child)
Microlead
```

### .descendants

L'attribut ```.descendants``` vous permet d'itérer sur tous les enfants d'une balise, de manière récursive -

ses enfants directs et les enfants de ses enfants directs et ainsi de suite -

```python
>>> for child in Htag.descendants:
print(child)
<title>Microlead</title>
Microlead
```

La balise ```<head>``` n'a qu'un seul enfant, mais elle a deux descendants : la balise ```<title>``` et l'enfant de la balise ```<title>```. L'objet beautifulsoup n'a qu'un seul enfant direct (la balise ```<html>```), mais il a un gret nombre de descendants : la balise ```<title>``` et l'enfant de la balise ```<title>```.

```python
>>> len(list(soup.children))
2
>>> len(list(soup.descendants))
33
```

### .string

Si la balise n'a qu'un seul enfant, et que cet enfant est un NavigableString, l'enfant est mis à disposition en tant que .string -.

```python
>>> Ttag.string
'Microlead'
```

Si le seul enfant d'une balise est une autre balise, et que cette balise a un .string, alors la balise parent est considérée comme ayant le même .string que son enfant...

```python
>>> Htag.contents
[<title>Microlead</title>]
>>>
>>> Htag.string
'Microlead'
```

Cependant, si une balise contient plus d'un élément, il n'est pas évident de savoir à quoi .string doit faire référence, c'est pourquoi .string est défini à None -.

```python
>>> print(soup.html.string)
None
```

### .strings et stripped_strings

S'il y a plus d'une chose à l'intérieur d'une balise, vous pouvez toujours regarder uniquement les chaînes de caractères. Utilisez le générateur .strings -

```python
>>> for string in soup.strings:
print(repr(string))
'\n'
'Microlead'
'\n'
'\n'
"Les meilleurs cours en ligne, et gratuits !"
'\n'
'Les 5 langages de programmation les plus utilisés sont : \n'
'Java'
',\n'
'C'
',\n'
'Python'
',\n'
'JavaScript'
' et\n'
'C'
';\n \nselon l'enquête en ligne.'
'\n'
'Langage de programmation'
'\n'
```

Pour supprimer les espaces vides, utilisez le générateur .stripped_strings.

```python
>>> for string in soup.stripped_strings:
print(repr(string))
'Microlead'
"Les meilleurs cours en ligne, et gratuits !"
'Les 5 langages de programmation les plus utilisés sont :'
'Java'
','
'C'
','
'Python'
','
'JavaScript'
'et'
'C'
';\n \nselon l'enquête en ligne.'
'Langage de programmation'
```

## Going up

Par analogie avec un "arbre généalogique", chaque balise et chaque chaîne a un parent : la balise qui la contient :

### .parent

Pour accéder à l'élément parent de l'élément, utilisez l'attribut .parent.

```python
>>> Ttag = soup.title
>>> Ttag
<title>Microlead</title>
>>> Ttag.parent
<head>title>Microlead</title></head>
```

Dans notre html_doc, la chaîne de titre elle-même a un parent : la balise ```<title>``` qui la contient-

```python
>>> Ttag.string.parent
<title>Microlead</title>
```

Le parent d'une balise de niveau supérieur comme ```<html>``` est l'objet Beautifulsoup lui-même.

```python
>>> htmltag = soup.html
>>> type(htmltag.parent)
<class 'bs4.BeautifulSoup'>
```

Le .parent d'un objet Beautifulsoup est défini comme None -.

```python
>>> print(soup.parent)
None
```

### .parents

Pour itérer sur tous les éléments parents, utilisez l'attribut .parents.

```python
>>> link = soup.a
>>> link
<a class="prog" href="https://www.Microlead.fr/cours/php" id="link1">PHP</a>
>>>
>>> for parent in link.parents:
        if parent is None:
            print(parent)
        else:
            print(parent.name)
p
body
html
[document]
```

## Sur les côtés

Vous trouverez ci-dessous un document simple -

```python
>>> sibling_soup = BeautifulSoup("<a><b>Micorlead</b><c><strong>Les meilleurs cours en ligne, et gratuits !</strong></b></a>")
>>> print(sibling_soup.prettify())
<html>
<body>
   <a>
      <b>
         Micorlead
      </b>
      <c>
         <strong>
            Les meilleurs cours en ligne, et gratuits !
         </strong>
      </c>
   </a>
</body>
</html>
```

Dans le document ci-dessus, les balises ```<b>``` et ```<c>``` sont au même niveau et elles sont toutes deux enfants de la même balise. Les deux balises ```<b>``` et ```<c>``` sont des frères et sœurs.

### .next_sibling et .previous_sibling

Utilisez ```.next_sibling``` et ```.previous_sibling``` pour naviguer entre les éléments de la page qui se trouvent au même niveau de l'arbre d'analyse :

```python
>>> sibling_soup.b.next_sibling
<c><strong>Les meilleurs cours en ligne, et gratuits !</strong></c>
>>>
>>> sibling_soup.c.previous_sibling
<b>Microlead</b>
```

La balise <b>a un .next_sibling mais pas de .previous_sibling, car il n'y a rien avant la balise ```<b>``` au même niveau de l'arbre, même cas avec la balise ```<c>```.

```python
>>> print(sibling_soup.b.previous_sibling)
None
>>> print(sibling_soup.c.next_sibling)
None
```

Les deux chaînes ne sont pas des frères et sœurs, car elles n'ont pas le même parent.

```python
>>> sibling_soup.b.string
'Microlead'
>>>
>>> print(sibling_soup.b.string.next_sibling)
None
```

### .next_siblings et .previous_siblings

Pour itérer sur les frères et sœurs d'une balise, utilisez .next_siblings et .previous_siblings.

```python
>>> for sibling in soup.a.next_siblings:
print(repr(sibling))
',\n'
<a class="prog" href="https://www.microlead.fr/cours/javascript" id="link2">C</a>
',\n'
>a class="prog" href="https://www.microlead.fr/cours/html" id="link3">Python</a>
',\n'
<a class="prog" href="https://www.microlead.fr/cours/css" id="link4">JavaScript</a>
' et\n'
<a class="prog" href="https://www.microlead.fr/cours/go"
id="link5">C</a>
';\n \nselon l'enquête en ligne.'
>>> for sibling in soup.find(id="link3").previous_siblings:
print(repr(sibling))
',\n'
<a class="prog" href="https://www.microlead.fr/cours/javascript" id="link2">C</a>
',\n'
<a class="prog" href="https://www.microlead.fr/cours/php" id="link1">PHP</a>
'Les 5 langages de programmation les plus utilisés sont : \n'
```

## Going back et forth

Revenons maintenant aux deux premières lignes de notre exemple précédent "html_doc" -

```html
<html><head><title>Microlead</title></head>
<body>
<h4 class="tagLine"><b>Les meilleurs tutos en ligne, et gratuits !</b></h4>
```

Un analyseur HTML prend une chaîne de caractères ci-dessus et la transforme en une série d'événements comme "ouvrir une balise ```<html>```", "ouvrir une balise ```<head>```", "ouvrir la balise ```<title>```", "ajouter une chaîne", "fermer la balise ```</title>```", "fermer la balise ```</head>```", "ouvrir une balise ```<h4>```" et ainsi de suite. BeautifulSoup propose différentes méthodes pour reconstruire l'analyse syntaxique initiale du document.

### .next_element et .previous_element

L'attribut ```.next_element``` d'une balise ou d'une chaîne de caractères pointe vers ce qui a été analysé immédiatement après. Parfois, il ressemble à ```.next_sibling```, mais ce n'est pas tout à fait la même chose. Voici la dernière balise ```<a>``` dans notre document d'exemple "html_doc".

```python
>>> last_a_tag = soup.find("a", id="link5")
>>> last_a_tag
<a class="prog" href="https://www.microlead.fr/cours/go" id="link5">C</a>
>>> last_a_tag.next_sibling
';\n \nselon l'enquête en ligne.'
```

Cependant, l'élément .next_element de cette balise ```<a>```, la chose qui a été analysée immédiatement après la balise ```<a>```, n'est pas le reste de cette phrase : c'est le mot "C" :

```python
>>> last_a_tag.next_element
'C'
```

Le comportement ci-dessus est dû au fait que dans le balisage original, la lettre "C" apparaissait avant ce point-virgule. L'analyseur syntaxique a rencontré une balise ```<a>```, puis la lettre "C", puis la balise ```</a>``` de fermeture, puis le point-virgule et le reste de la phrase. Le point-virgule est au même niveau que la balise ```<a>```, mais la lettre "C" a été rencontrée en premier.

L'attribut ```.previous_element``` est l'exact opposé de ```.next_element```. Il pointe vers l'élément qui a été analysé immédiatement avant celui-ci.

```python
>>> last_a_tag.previous_element
' et\n'
>>>
>>> last_a_tag.previous_element.next_element
<a class="prog" href="https://www.Microlead.fr/cours/go" id="link5">C</a>
```

### .next_elements et .previous_elements

Nous utilisons ces itérateurs pour avancer et reculer vers un élément.

```python
>>> for element in last_a_tag.next_e lements:
print(repr(element))
'C'
';\n \nselon l'enquête en ligne.'
'\n'
<p class="prog">Langage de programmation</p>
'Langage de programmation'
'\n'
```