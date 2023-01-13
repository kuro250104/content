Les graphes sont des structures de données très utiles pour résoudre de nombreux défis mathématiques importants. Par exemple, la topologie des réseaux informatiques ou l'analyse des structures moléculaires des composés chimiques. Ils sont également utilisés dans la circulation urbaine ou la planification des itinéraires et même dans les langues humaines et leur grammaire. Toutes ces applications ont un défi commun : traverser le graphe en utilisant ses bords et s'assurer que tous les nœuds du graphe sont visités. Il existe deux méthodes courantes établies pour effectuer cette traversée, décrite ci-dessous.

## Depth First Traversal

Le depth first search (DFS) est un algorithme qui parcourt un graphe en profondeur et utilise une pile pour se souvenir du prochain sommet à rechercher, lorsqu'une impasse se produit dans une itération. Nous implémentons DFS pour un graphe en Python en utilisant les types de données set car ils fournissent les fonctionnalités nécessaires pour garder la trace des nœuds visités et non visités.

### Exemple

```python
class graph:
    def __init__(self,gdict=None):
        if gdict is None:
            gdict = {}
        self.gdict = gdict
    # Check for the visisted and unvisited nodes
    def dfs(graph, start, visited = None):
    if visited is None:
        visited = set()
    visited.add(start)
    print(start)
    for next in graph[start] - visited:
        dfs(graph, next, visited)
    return visited

gdict = { 
    "a" : set(["b","c"]),
    "b" : set(["a", "d"]),
    "c" : set(["a", "d"]),
    "d" : set(["e"]),
    "e" : set(["a"])
}
dfs(gdict, 'a')
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
a b d e c
```

## Breadth First Traversal

Le breadth first search (BFS)est un algorithme qui parcourt un graphe breadth ward motion et utilise une file d'attente pour se souvenir d'obtenir le prochain sommet pour commencer une recherche, lorsqu'une impasse se produit dans une itération. 

Nous implémentons BFS pour un graphe en Python en utilisant la structure de données de file d'attente discutée précédemment. Lorsque nous continuons à visiter les nœuds adjacents non visités et à les ajouter à la file d'attente. Ensuite, nous commençons à retirer de la file d'attente uniquement le nœud qui n'est plus visité. Nous arrêtons le programme lorsqu'il n'y a pas de nœud adjacent suivant à visiter.

### Exemple

```python
import collections
class graph:
    def __init__(self,gdict=None):
        if gdict is None:
            gdict = {}
        self.gdict = gdict
    def bfs(graph, startnode):
    # Track the visited and unvisited nodes using queue
    seen, queue = set([startnode]), collections.deque([startnode])
    while queue:
        vertex = queue.popleft()
        marked(vertex)
        for node in graph[vertex]:
            if node not in seen:
                seen.add(node)
                queue.append(node)

def marked(n):
   print(n)

# The graph dictionary
gdict = { 
    "a" : set(["b","c"]),
    "b" : set(["a", "d"]),
    "c" : set(["a", "d"]),
    "d" : set(["e"]),
    "e" : set(["a"])
}
bfs(gdict, "a")
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
a c b d e 
```
