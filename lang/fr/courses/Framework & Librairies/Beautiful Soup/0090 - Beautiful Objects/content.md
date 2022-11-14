## Introduction

Le point de départ de tout projet BeautifulSoup est l'objet BeautifulSoup. Un objet BeautifulSoup représente le document HTML/XML d'entrée utilisé pour sa création.

Nous pouvons passer soit une chaîne de caractères ou un objet de type fichier pour BeautifulSoup, où les fichiers (objets) sont soit stockés localement dans notre machine ou une page web.

Les objets BeautifulSoup les plus courants sont les suivants -

- Tag
- NavigableString
- BeautifulSoup
- Comment

## Comparaison de l'égalité des objets

Selon la belle soupe, deux objets chaîne ou balise navigable sont égaux s'ils représentent le même balisage HTML/XML.

Voyons maintenant l'exemple ci-dessous, où deux balises ```<b>``` sont comparées, même s'ils sont chacun dans des parties différentes de l'arbre et si leur contenu sont similaires.

```python
>>> markup = "<p>Learn Python and <b>Java</b> and advanced <b>Java</b>! from Microlead</p>"
>>> soup = BeautifulSoup(markup, "html.parser")
>>> first_b, second_b = soup.find_all('b')
>>> print(first_b == second_b)
True
>>> print(first_b.previous_element == second_b.previous_element)
False
```

Cependant, pour vérifier si les deux variables se réfèrent aux mêmes objets, vous pouvez utiliser la méthode suivante-.

```python
>>> print(first_b is second_b)
False
```

## Copier des objects Beautiful Soup

Pour créer une copie de n'importe quel tag ou NavigableString, utilisez la fonction copy.copy(), comme ci-dessous -

```python
>>> import copy
>>> p_copy = copy.copy(soup.p)
>>> print(p_copy)
<p>Learn Python and <b>Java</b> and advanced <b>Java</b>! from Tutorialspoint</p>
>>>
```

Bien que les deux copies (l'original et la copie) contiennent la même balise, elles ne représentent pas le même objet.

```python
>>> print(soup.p == p_copy)
True
>>>
>>> print(soup.p is p_copy)
False
>>>
```

La seule différence réelle est que la copie est complètement détachée de l'arbre d'objets Beautiful Soup original, comme si extract() avait été appelé sur elle.

```python
>>> print(p_copy.parent)
None
```

Le comportement ci-dessus est dû à deux tags différents qui ne peuvent pas occuper le même espace en même temps.