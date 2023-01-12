Un graphe est une représentation imagée d'un ensemble d'objets où certaines paires d'objets sont reliées par des liens. Les objets interconnectés sont représentés par des points appelés sommets, et les liens qui relient les sommets sont appelés arêtes. Les différents termes et fonctionnalités associés à un graphe sont décrits de manière très détaillée dans notre tutoriel ici.

Dans ce cours, nous allons voir comment créer un graphe et y ajouter divers éléments de données à l'aide d'un programme python. Voici les opérations de base que nous effectuons sur les graphes.

- Afficher les sommets du graphique
- Afficher les bordure du graphe
- Ajouter un sommet
- Ajouter une bordure
- Créer un graphique

Un graphe peut être facilement présenté en utilisant les types de données du dictionnaire python. Nous représentons les sommets comme les clés du dictionnaire et la connexion entre les sommets, également appelée arêtes, comme les valeurs du dictionnaire.

Regardez le graphique suivant :

![graphique d'exemple](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/Python/courses/0340%20-%20Graphiques/images/image1.jpg)

Dans le graphique ci-dessus : 

```python
V = {a, b, c, d, e}
E = {ab, ac, bd, cd, de}
```

### Exemple

Nous pouvons présenter ce graphique dans un programme python comme ci-dessous :

```python
# Create the dictionary with graph elements
graph = { 
    'a' : ['b','c'],
    'b' : ['a', 'd'],
    'c' : ['a', 'd'],
    'd' : ['e'],
    'e' : ['d']
}
# Print the graph 		 
print(graph)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
{'c': ['a', 'd'], 'a': ['b', 'c'], 'e': ['d'], 'd': ['e'], 'b': ['a', 'd']}
```

## Afficher les sommets du graphique

Pour afficher les sommets du graphe, il suffit de trouver les clés du dictionnaire du graphe. Nous utilisons la méthode ```keys()```.

```python
class graph:
    def __init__(self, gdict=None):
        if gdict is None:
            gdict = []
        self.gdict = gdict
# Get the keys of the dictionary
    def getVertices(self):
        return list(self.gdict.keys())
# Create the dictionary with graph elements
graph_elements = { 
    'a' : ['b','c'],
    'b' : ['a', 'd'],
    'c' : ['a', 'd'],
    'd' : ['e'],
    'e' : ['d']
}
g = graph(graph_elements)
print(g.getVertices())
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
['d', 'b', 'e', 'c', 'a']
```

## Afficher les bords du graphique

Trouver les bords du graphe est un peu plus délicat que de trouver les sommets, car nous devons trouver chacune des paires de sommets qui ont un bord entre eux. Nous créons donc une liste vide d'arêtes puis nous itérons à travers les valeurs d'arêtes associées à chacun des sommets. Une liste est formée contenant le groupe distinct de bords trouvés à partir des sommets.

```python
class graph:
    def __init__(self, gdict=None):
        if gdict is None:
            gdict = {}
        self.gdict = gdict

    def edges(self):
        return self.findedges()

    # Find the distinct list of edges
    def findedges(self):
        edgename = []
        for vrtx in self.gdict:
            for nxtvrtx in self.gdict[vrtx]:
                if {nxtvrtx, vrtx} not in edgename:
                    edgename.append({vrtx, nxtvrtx})
        return edgename
# Create the dictionary with graph elements
graph_elements = { 
    'a' : ['b','c'],
    'b' : ['a', 'd'],
    'c' : ['a', 'd'],
    'd' : ['e'],
    'e' : ['d']
}
g = graph(graph_elements)
print(g.edges())
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
[{'b', 'a'}, {'b', 'd'}, {'e', 'd'}, {'a', 'c'}, {'c', 'd'}]
```

## Ajout d'un sommet

L'ajout d'un sommet est simple : nous ajoutons une clé supplémentaire au dictionnaire des graphes.

### Exemple

```python
class graph:
    def __init__(self, gdict=None):
        if gdict is None:
            gdict = {}
        self.gdict = gdict
    
    def getVertices(self):
        return list(self.gdict.keys())
    
    # Add the vertex as a key
    def addVertex(self, vrtx):
        if vrtx not in self.gdict:
            self.gdict[vrtx] = []
# Create the dictionary with graph elements
graph_elements = { 
    'a' : ['b','c'],
    'b' : ['a', 'd'],
    'c' : ['a', 'd'],
    'd' : ['e'],
    'e' : ['d']
}
g = graph(graph_elements)
g.addVertex('f')
print(g.getVertices())
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
['f', 'e', 'b', 'a', 'c','d']
```

## Ajouter un bord

L'ajout d'une bordure à un graphe existant implique de traiter le nouveau sommet comme un tuple et de valider si la bordure est déjà présente. Si ce n'est pas le cas, le bord est ajouté.

```python
class graph:
    def __init__(self, gdict=None):
        if gdict is None:
            gdict = {}
        self.gdict = gdict

    def edges(self):
        return self.findedges()

    # Add the new edge
    def AddEdge(self, edge):
        edge = set(edge)
        (vrtx1, vrtx2) = tuple(edge)
        if vrtx1 in self.gdict:
            self.gdict[vrtx1].append(vrtx2)
        else:
            self.gdict[vrtx1] = [vrtx2]

    # List the edge names
    def findedges(self):
        edgename = []
        for vrtx in self.gdict:
            for nxtvrtx in self.gdict[vrtx]:
                if {nxtvrtx, vrtx} not in edgename:
                    edgename.append({vrtx, nxtvrtx})
            return edgename
# Create the dictionary with graph elements
graph_elements = { 
   'a' : ['b','c'],
   'b' : ['a', 'd'],
   'c' : ['a', 'd'],
   'd' : ['e'],
   'e' : ['d']
}
g = graph(graph_elements)
g.AddEdge({'a','e'})
g.AddEdge({'a','c'})
print(g.edges())
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[{'e', 'd'}, {'b', 'a'}, {'b', 'd'}, {'a', 'c'}, {'a', 'e'}, {'c', 'd'}]
```
