## Introduction

Tous les documents HTML ou XML sont écrits dans un encodage spécifique comme ASCII ou UTF-8. Cependant, lorsque vous chargez ce document HTML/XML dans BeautifulSoup, il a été converti en Unicode.

```python
>>> markup = "<p>I will display £</p>"
>>> Bsoup = BeautifulSoup(markup)
>>> Bsoup.p
<p>I will display £</p>
>>> Bsoup.p.string
'I will display £'
```

Le comportement ci-dessus est dû au fait que BeautifulSoup utilise en interne la sous-bibliothèque appelée Unicode, Dammit pour détecter l'encodage d'un document, puis le convertir en Unicode.

Cependant, l'Unicode, Dammit ne devine pas toujours correctement. Comme le document est recherché octet par octet pour deviner l'encodage, cela prend beaucoup de temps. Vous pouvez gagner du temps et éviter les erreurs, si vous connaissez déjà l'encodage en le passant au constructeur de BeautifulSoup comme from_encoding.

Voici un exemple où BeautifulSoup identifie mal un document ISO-8859-8 comme étant ISO-8859-7.

```python
>>> markup = b"<h1>\xed\xe5\xec\xf9</h1>"
>>> soup = BeautifulSoup(markup)
>>> soup.h1
<h1>νεμω</h1>
>>> soup.original_encoding
'ISO-8859-7'
>>>
```

Pour résoudre le problème ci-dessus, passez-le à BeautifulSoup en utilisant from_encoding -.

```python
>>> soup = BeautifulSoup(markup, from_encoding="iso-8859-8")
>>> soup.h1
<h1>ולש </h1>
>>> soup.original_encoding
'iso-8859-8'
>>>
```

Une autre nouvelle fonctionnalité ajoutée à BeautifulSoup 4.4.0 est, exclude_encoding. Elle peut être utilisée lorsque vous ne connaissez pas l'encodage correct mais que vous êtes sûr qu'Unicode, bon sang, affiche un résultat erroné.

```python
>>> soup = BeautifulSoup(markup, exclude_encodings=["ISO-8859-7"])
```
## Encodage de sortie

La sortie d'un BeautifulSoup est un document UTF-8, quel que soit le document entré dans BeautifulSoup. Ci-dessous un document, où les caractères polonais sont là en format ISO-8859-2.

```python
html_markup = """
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<HTML>
<HEAD>
<META HTTP-EQUIV="content-type" CONTENT="text/html; charset=iso-8859-2">
</HEAD>
<BODY>
ą ć ę ł ń ó ś ź ż Ą Ć Ę Ł Ń Ó Ś Ź Ż
</BODY>
</HTML>
"""


>>> soup = BeautifulSoup(html_markup)
>>> print(soup.prettify())
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
   <head>
      <meta content="text/html; charset=utf-8" http-equiv="content-type"/>
   </head>
   <body>
      ą ć ę ł ń ó ś ź ż Ą Ć Ę Ł Ń Ó Ś Ź Ż
   </body>
</html>
```

Dans l'exemple ci-dessus, si vous remarquez, la balise ```<meta>``` a été réécrite pour refléter le fait que le document généré par BeautifulSoup est désormais au format UTF-8.

Si vous ne voulez pas que la sortie générée soit en UTF-8, vous pouvez attribuer l'encodage souhaité dans prettify().

```python
>>> print(soup.prettify("latin-1"))
b'<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">\n<html>\n <head>\n <meta content="text/html; charset=latin-1" http-equiv="content-type"/>\n </head>\n <body>\n ą ć ę ł ń \xf3 ś ź ż Ą Ć Ę Ł Ń \xd3 Ś Ź Ż\n </body>\n</html>\n'
```

Dans l'exemple ci-dessus, nous avons encodé le document complet, cependant vous pouvez encoder, n'importe quel élément particulier dans la soupe comme s'il s'agissait d'une chaîne python -.

```python
>>> soup.p.encode("latin-1")
b'<p>0My first paragraph.</p>'
>>> soup.h1.encode("latin-1")
b'<h1>My First Heading</h1>'
```

Tous les caractères qui ne peuvent pas être représentés dans l'encodage que vous avez choisi seront convertis en références numériques d'entités XML. Vous trouverez ci-dessous un exemple de ce type -

```python
>>> markup = u"<b>\N{SNOWMAN}</b>"
>>> snowman_soup = BeautifulSoup(markup)
>>> tag = snowman_soup.b
>>> print(tag.encode("utf-8"))
b'<b>\xe2\x98\x83</b>'
```

Si vous essayez d'encoder ce qui précède en "latin-1" ou "ascii", cela générera "☃", indiquant qu'il n'y a pas de représentation pour cela.

```python
>>> print (tag.encode("latin-1"))
b'<b>☃</b>'
>>> print (tag.encode("ascii"))
b'<b>☃</b>'
```

## Unicode !

Unicode est utilisé principalement lorsque le document entrant est dans un format inconnu (principalement une langue étrangère) et que nous voulons l'encoder dans un format connu (Unicode) et que nous n'avons pas besoin de Beautifulsoup pour faire tout cela.