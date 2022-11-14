Il existe de nombreuses méthodes de Beautifulsoup, qui nous permettent de rechercher un arbre d'analyse. Les deux méthodes les plus courantes et les plus utilisées sont ```find()``` et ```find_all()```.

Avant de parler de ```find()``` et ```find_all()```, voyons quelques exemples de différents filtres que vous pouvez passer dans ces méthodes.

## Types de filtres

Nous disposons de différents filtres que nous pouvons passer dans ces méthodes. La compréhension de ces filtres est cruciale car ils sont utilisés à maintes reprises dans l'API de recherche. Nous pouvons utiliser ces filtres sur la base du nom de la balise, de ses attributs, du texte d'une chaîne ou d'un mélange de ces éléments.

### Une String

L'un des types de filtre les plus simples est une chaîne de caractères. En passant une chaîne à la méthode de recherche, Beautifulsoup effectuera une correspondance avec cette chaîne exacte.

Le code ci-dessous trouvera toutes les balises ```<p>``` dans le document.

```python
>>> markup = BeautifulSoup('<p>Top Three</p><p><pre>Programming Languages are:</pre></p><p><b>Java, Python, Cplusplus</b></p>')
>>> markup.find_all('p')
[<p>Top Three</p>, <p></p>, <p><b>Java, Python, Cplusplus</b></p>]
```

### Regular Expression

Vous pouvez trouver tous les tags commençant par une chaîne/tag donnée. Avant cela, nous devons importer le module re pour utiliser les expressions régulières.

```python
>>> import re
>>> markup = BeautifulSoup('<p>Top Three</p><p><pre>Programming Languages are:</pre></p><p><b>Java, Python, Cplusplus</b></p>')
>>>
>>> markup.find_all(re.compile('^p'))
[<p>Top Three</p>, <p></p>, <pre>Programming Languages are:</pre>, <p><b>Java, Python, Cplusplus</b></p>]
```

### List

Vous pouvez passer plusieurs balises à trouver en fournissant une liste. Le code ci-dessous trouve toutes les balises ```<b>``` et ```<pre>``` -

```python
>>> markup.find_all(['pre', 'b'])
[<pre>Programming Languages are:</pre>, <b>Java, Python, Cplusplus</b>]
```

### True

True renvoie toutes les balises qu'il peut trouver, mais aucune chaîne de caractères en soi.

```python
>>> markup.find_all(True)
[<html><body><p>Top Three</p><p></p><pre>Programming Languages are:</pre>
<p><b>Java, Python, Cplusplus</b> </p> </body></html>, 
<body><p>Top Three</p><p></p><pre> Programming Languages are:</pre><p><b>Java, Python, Cplusplus</b></p>
</body>, 
<p>Top Three</p>, <p></p>, <pre>Programming Languages are:</pre>, <p><b>Java, Python, Cplusplus</b></p>, <b>Java, Python, Cplusplus</b>]
```

Pour ne retourner que les tags de la soupe ci-dessus, -

```python
>>> for tag in markup.find_all(True):
(tag.name)
'html'
'body'
'p'
'p'
'pre'
'p'
'b'
```

## find_all()

Vous pouvez utiliser find_all pour extraire toutes les occurrences d'une balise particulière de la réponse de la page, comme -

### Syntaxe

```python
find_all(name, attrs, recursive, string, limit, **kwargs)
```

Extrayons quelques données intéressantes d'IMDB - "Top rated movies" de tous les temps.

```python
>>> url="https://www.imdb.com/chart/top/?ref_=nv_mv_250"
>>> content = requests.get(url)
>>> soup = BeautifulSoup(content.text, 'html.parser')
#Extract title Page
>>> print(soup.find('title'))
<title>IMDb Top 250 - IMDb</title>

#Extracting main heading
>>> for heading in soup.find_all('h1'):
    print(heading.text)
Top Rated Movies

#Extracting sub-heading
>>> for heading in soup.find_all('h3'):
    print(heading.text)

IMDb Charts
You Have Seen
    IMDb Charts
    Top India Charts
Top Rated Movies by Genre
Recently Viewed
```

D'après ce qui précède, nous pouvons voir que ```find_all``` nous donnera tous les éléments correspondant aux critères de recherche que nous avons définis. Tous les filtres que nous pouvons utiliser avec ```find_all()``` peuvent être utilisés avec ```find()``` et d'autres méthodes de recherche comme ```find_parents()``` ou ```find_siblings()```.

## find()

Nous avons vu ci-dessus, ```find_all()``` est utilisé pour scanner le document entier pour trouver tous les contenus mais quelque chose, l'exigence est de trouver seulement un résultat. Si vous savez que le document ne contient qu'une seule balise ```<body>```, c'est une perte de temps de rechercher le document entier. Une façon de faire est d'appeler ```find_all()``` avec limit=1 à chaque fois ou bien on peut utiliser la méthode ```find()``` pour faire la même chose.

### Syntaxe

```python
find(name, attrs, recursive, string, **kwargs)
```

Ainsi, ci-dessous, deux méthodes différentes donnent le même résultat -

```python
>>> soup.find_all('title',limit=1)
[<title>IMDb Top 250 - IMDb</title>]
>>>
>>> soup.find('title')
<title>IMDb Top 250 - IMDb</title>
```

Dans les résultats ci-dessus, nous pouvons voir que la méthode ```find_all()``` renvoie une liste contenant un seul élément alors que la méthode ```find()``` renvoie un seul résultat.

Une autre différence entre les méthodes ```find()``` et ```find_all()``` est que les méthodes -

```python
>>> soup.find_all('h2')
[]
>>>
>>> soup.find('h2')
```

Si la méthode ```soup.find_all()``` ne trouve rien, elle retourne une liste vide alors que ```find()``` retourne None.

## find_parents() and find_parent()

Contrairement aux méthodes find_all() et find() qui parcourent l'arbre en regardant les descendants des balises, les méthodes find_parents() et find_parents() font le contraire, elles parcourent l'arbre vers le haut et regardent les parents d'une balise (ou d'une chaîne).

### Syntaxe

```python
find_parents(name, attrs, string, limit, **kwargs)
find_parent(name, attrs, string, **kwargs)

>>> a_string = soup.find(string="The Godfather")
>>> a_string
'The Godfather'
>>> a_string.find_parents('a')
[<a href="/title/tt0068646/" title="Francis Ford Coppola (dir.), Marlon Brando, Al Pacino">The Godfather</a>]
>>> a_string.find_parent('a')
<a href="/title/tt0068646/" title="Francis Ford Coppola (dir.), Marlon Brando, Al Pacino">The Godfather</a>
>>> a_string.find_parent('tr')
<tr>

<td class="posterColumn">
<span data-value="2" name="rk"></span>
<span data-value="9.149038526210072" name="ir"></span>
<span data-value="6.93792E10" name="us"></span>
<span data-value="1485540" name="nv"></span>
<span data-value="-1.850961473789928" name="ur"></span>
<a href="/title/tt0068646/"> <img alt="The Godfather" height="67" src="https://m.media-amazon.com/images/M/MV5BM2MyNjYxNmUtYTAwNi00MTYxLWJmNWYtYzZlODY3ZTk3OTFlXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_UY67_CR1,0,45,67_AL_.jpg" width="45"/>
</a> </td>
<td class="titleColumn">
2.
<a href="/title/tt0068646/" title="Francis Ford Coppola (dir.), Marlon Brando, Al Pacino">The Godfather</a>
<span class="secondaryInfo">(1972)</span>
</td>
<td class="ratingColumn imdbRating">
<strong title="9.1 based on 1,485,540 user ratings">9.1</strong>
</td>
<td class="ratingColumn">
<div class="seen-widget seen-widget-tt0068646 pending" data-titleid="tt0068646">
<div class="boundary">
<div class="popover">
<span class="delete"> </span><ol><li>1<li>2<li>3<li>4<li>5<li>6<li>7<li>8<li>9<li>10</li>0</li></li></li></li&td;</li></li></li></li></li></ol> </div>
</div>
<div class="inline">
<div class="pending"></div>
<div class="unseeable">NOT YET RELEASED</div>
<div class="unseen"> </div>
<div class="rating"></div>
<div class="seen">Seen</div>
</div>
</div>
</td>
<td class="watchlistColumn">

<div class="wlb_ribbon" data-recordmetrics="true" data-tconst="tt0068646"></div>
</td>
</tr>
>>>
>>> a_string.find_parents('td')
[<td class="titleColumn">
2.
<a href="/title/tt0068646/" title="Francis Ford Coppola (dir.), Marlon Brando, Al Pacino">The Godfather</a>
<span class="secondaryInfo">(1972)</span>
</td>]
```

Il existe huit autres méthodes similaires -

```python
find_next_siblings(name, attrs, string, limit, **kwargs)
find_next_sibling(name, attrs, string, **kwargs)

find_previous_siblings(name, attrs, string, limit, **kwargs)
find_previous_sibling(name, attrs, string, **kwargs)

find_all_next(name, attrs, string, limit, **kwargs)
find_next(name, attrs, string, **kwargs)

find_all_previous(name, attrs, string, limit, **kwargs)
find_previous(name, attrs, string, **kwargs)
```

Où,

les méthodes ```find_next_siblings()``` et ```find_next_sibling()``` itèrent sur tous les frères et sœurs de l'élément qui viennent après l'élément actuel.
Les méthodes ```find_previous_siblings()``` et ```find_previous_sibling()``` parcourent tous les éléments frères et sœurs qui précèdent l'élément actuel.
Les méthodes ```find_all_next()``` et ```find_next()``` parcourent toutes les balises et chaînes de caractères qui suivent l'élément actuel.
Les méthodes ```find_all_previous()``` et ```find_previous()``` parcourent toutes les balises et chaînes de caractères qui précèdent l'élément courant.

## CSS selectors

La bibliothèque BeautifulSoup prend en charge les sélecteurs CSS les plus couramment utilisés. Vous pouvez rechercher des éléments à l'aide de sélecteurs CSS avec l'aide de la méthode ```select()```.

Voici quelques exemples -

```python
>>> soup.select('title')
[<title>IMDb Top 250 - IMDb</title>, <title>IMDb Top Rated Movies</title>]
>>>
>>> soup.select("p:nth-of-type(1)")
[<p>The Top Rated Movie list only includes theatrical features.</p>, <p> class="imdb-footer__copyright _2-iNNCFskmr4l2OFN2DRsf">(c) 1990-2019 by IMDb.com, Inc.</p>]
>>> len(soup.select("p:nth-of-type(1)"))
2
>>> len(soup.select("a"))
609
>>> len(soup.select("p"))
2

>>> soup.select("html head title")
[<title>IMDb Top 250 - IMDb</title>, <title>IMDb Top Rated Movies</title>]
>>> soup.select("head > title")
[<title>IMDb Top 250 - IMDb</title>]

#print HTML code of the tenth li elemnet
>>> soup.select("li:nth-of-type(10)")
[<li class="subnav_item_main">
<a href="/search/title?genres=film_noir&sort=user_rating,desc&title_type=feature&num_votes=25000,">Film-Noir
</a> </li>]
```