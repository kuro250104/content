L'arbre représente les nœuds reliés par des arêtes. Il s'agit d'une structure de données non linéaire. Il possède les propriétés suivantes :

- Un nœud est marqué comme nœud racine.
- Chaque nœud autre que la racine est associé à un nœud parent.
- Chaque nœud peut avoir un nombre arbitraire de nœud enfant.

Nous créons une structure de données arborescente en python en utilisant le concept de nœud os discuté précédemment. Nous désignons un nœud comme nœud racine et ajoutons ensuite d'autres nœuds comme nœuds enfants. Le programme ci-dessous permet de créer le nœud racine.

## Créer une racine

Nous créons simplement une classe Node et ajoutons une valeur au nœud. Cela devient un arbre avec seulement un nœud racine.

### Exemple

```python
class Node:
    def __init__(self, data):
        self.left = None
        self.right = None
        self.data = data
    def PrintTree(self):
        print(self.data)

root = Node(10)
root.PrintTree()
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
10
```

## Insertion dans un arbre

Pour insérer dans un arbre, nous utilisons la même classe de nœud créée ci-dessus et lui ajoutons une classe d'insertion. La classe insert compare la valeur du nœud au nœud parent et décide de l'ajouter en tant que nœud gauche ou droit. Enfin, la classe ```PrintTree``` est utilisée pour imprimer l'arbre.

### Exemple

```python
class Node:
    def __init__(self, data):
        self.left = None
        self.right = None
        self.data = data

    def insert(self, data):
        # Compare the new value with the parent node
        if self.data:
            if data < self.data:
                if self.left is None:
                self.left = Node(data)
                else:
                self.left.insert(data)
                elif data > self.data:
                if self.right is None:
                    self.right = Node(data)
                else:
                    self.right.insert(data)
        else:
            self.data = data

    # Print the tree
    def PrintTree(self):
        if self.left:
            self.left.PrintTree()
        print(self.data),
        if self.right:
            self.right.PrintTree()

# Use the insert method to add nodes
root = Node(12)
root.insert(6)
root.insert(14)
root.insert(3)
root.PrintTree()
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
3 6 12 14
```

## Traverser un arbre

L'arbre peut être traversé en décidant d'une séquence pour visiter chaque nœud. Comme nous pouvons le voir clairement, nous pouvons commencer par un nœud, puis visiter le sous-arbre de gauche en premier et le sous-arbre de droite ensuite. On peut aussi visiter d'abord le sous-arbre de droite, puis le sous-arbre de gauche. En conséquence, il existe différents noms pour ces méthodes de traversée des arbres.

## Algorithmes de traversée d'arbre

La traversée est un processus qui permet de visiter tous les nœuds d'un arbre et peut également imprimer leurs valeurs. Étant donné que tous les nœuds sont reliés par des arêtes (liens), nous commençons toujours par le nœud racine (tête). Autrement dit, nous ne pouvons pas accéder au hasard à un nœud d'un arbre. Il existe trois façons de parcourir un arbre.

- Traversée en cours de commande
- Traversée avant l'ordre
- Traversée post-ordre

### Traversée en ordre

Dans cette méthode de traversée, le sous-arbre de gauche est visité en premier, puis la racine et enfin le sous-arbre de droite. Nous devons toujours nous rappeler que chaque nœud peut représenter un sous-arbre lui-même.

Dans le programme python ci-dessous, nous utilisons la classe Node pour créer des supports de place pour le nœud racine ainsi que pour les nœuds gauche et droit. Ensuite, nous créons une fonction d'insertion pour ajouter des données à l'arbre. Enfin, la logique de traversée dans l'ordre est implémentée en créant une liste vide et en ajoutant d'abord le nœud gauche, puis le nœud racine ou parent.

Enfin, le nœud de gauche est ajouté pour terminer la traversée dans l'ordre. Veuillez noter que ce processus est répété pour chaque sous-arbre jusqu'à ce que tous les nœuds soient traversés.

#### Exemple

```python
class Node:
    def __init__(self, data):
        self.left = None
        self.right = None
        self.data = data
    # Insert Node
    def insert(self, data):
        if self.data:
            if data < self.data:
                if self.left is None:
                self.left = Node(data)
                else:
                self.left.insert(data)
            else data > self.data:
                if self.right is None:
                self.right = Node(data)
                else:
                self.right.insert(data)
        else:
            self.data = data
    # Print the Tree
    def PrintTree(self):
        if self.left:
            self.left.PrintTree()
        print(self.data),
        if self.right:
            self.right.PrintTree()
    # Inorder traversal
    # Left -> Root -> Right
    def inorderTraversal(self, root):
        res = []
        if root:
            res = self.inorderTraversal(root.left)
            res.append(root.data)
            res = res + self.inorderTraversal(root.right)
        return res
root = Node(27)
root.insert(14)
root.insert(35)
root.insert(10)
root.insert(19)
root.insert(31)
root.insert(42)
print(root.inorderTraversal(root))
```

#### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[10, 14, 19, 27, 31, 35, 42]
```

### Traversée de pré-commande

Dans cette méthode de traversée, le nœud racine est visité en premier, puis le sous-arbre de gauche et enfin le sous-arbre de droite.

Dans le programme python ci-dessous, nous utilisons la classe Node pour créer des espaces pour le nœud racine ainsi que pour les nœuds gauche et droit. Ensuite, nous créons une fonction d'insertion pour ajouter des données à l'arbre. Enfin, la logique de traversée préordonnée est mise en œuvre en créant une liste vide et en ajoutant d'abord le nœud racine, puis le nœud gauche.

Enfin, le nœud de droite est ajouté pour terminer la traversée du préordre. Veuillez noter que ce processus est répété pour chaque sous-arbre jusqu'à ce que tous les nœuds soient traversés.

#### Exemple

```python
class Node:
    def __init__(self, data):
        self.left = None
        self.right = None
        self.data = data
    # Insert Node
    def insert(self, data):
        if self.data:
            if data < self.data:
                if self.left is None:
                self.left = Node(data)
                else:
                self.left.insert(data)
            elif data > self.data:
                if self.right is None:
                self.right = Node(data)
                else:
                self.right.insert(data)
            else:
                self.data = data
    # Print the Tree
    def PrintTree(self):
        if self.left:
            self.left.PrintTree()
        print(self.data),
        if self.right:
            self.right.PrintTree()
    # Preorder traversal
    # Root -> Left ->Right
    def PreorderTraversal(self, root):
        res = []
        if root:
            res.append(root.data)
            res = res + self.PreorderTraversal(root.left)
            res = res + self.PreorderTraversal(root.right)
        return res
root = Node(27)
root.insert(14)
root.insert(35)
root.insert(10)
root.insert(19)
root.insert(31)
root.insert(42)
print(root.PreorderTraversal(root))
```

#### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[27, 14, 10, 19, 35, 31, 42]
```

### Traversée post-ordre

Dans cette méthode de traversée, le nœud racine est visité en dernier, d'où son nom. Nous traversons d'abord le sous-arbre de gauche, puis le sous-arbre de droite et enfin le nœud racine.

Dans le programme python ci-dessous, nous utilisons la classe Node pour créer des emplacements pour le nœud racine ainsi que pour les nœuds gauche et droit. Ensuite, nous créons une fonction d'insertion pour ajouter des données à l'arbre. Enfin, la logique de traversée post-ordre est mise en œuvre en créant une liste vide et en ajoutant d'abord le nœud gauche, puis le nœud droit.

Enfin, le nœud racine ou parent est ajouté pour terminer la traversée post-ordre. Veuillez noter que ce processus est répété pour chaque sous-arbre jusqu'à ce que tous les nœuds soient traversés.

#### Exemple

```python
class Node:
    def __init__(self, data):
        self.left = None
        self.right = None
        self.data = data
    # Insert Node
    def insert(self, data):
        if self.data:
            if data < self.data:
                if self.left is None:
                self.left = Node(data)
                else:
                self.left.insert(data)
            else if data > self.data:
                if self.right is None:
                self.right = Node(data)
                else:

                self.right.insert(data)
        else:
            self.data = data
    # Print the Tree
    def PrintTree(self):
        if self.left:
            self.left.PrintTree()
print(self.data),
if self.right:
self.right.PrintTree()
# Postorder traversal
# Left ->Right -> Root
def PostorderTraversal(self, root):
res = []
if root:
res = self.PostorderTraversal(root.left)
res = res + self.PostorderTraversal(root.right)
res.append(root.data)
return res
root = Node(27)
root.insert(14)
root.insert(35)
root.insert(10)
root.insert(19)
root.insert(31)
root.insert(42)
print(root.PostorderTraversal(root))
```

#### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
[10, 19, 14, 31, 42, 35, 27]
```
