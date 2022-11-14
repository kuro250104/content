## Introduction

Dans l'exemple de code précédent, nous analysons le document à travers le beau constructeur en utilisant une méthode string. Une autre façon est de passer le document par le biais d'un fichier ouvert.

```python
from bs4 import BeautifulSoup
with open("example.html") as fp:
    soup = BeautifulSoup(fp)
soup = BeautifulSoup("<html>data</html>")
```

Tout d'abord, le document est converti en Unicode, et les entités HTML sont converties en caractères Unicode :

```python
import bs4
html = '''<b>microlead</b>, <i>&web scraping &data science;</i>'''
soup = bs4.BeautifulSoup(html, 'lxml')
print(soup)
```

Sortie : 

```html
<html><body><b>microlead</b>, <i>&web scraping &data science;</i></body></html>
```

BeautifulSoup analyse ensuite les données à l'aide d'un analyseur HTML ou vous lui demandez explicitement d'utiliser un analyseur XML.