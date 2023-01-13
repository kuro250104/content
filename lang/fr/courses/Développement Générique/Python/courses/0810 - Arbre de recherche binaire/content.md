Un arbre de recherche binaire (*Binary Search Tree*) est un arbre dans lequel tous les nœuds suivent les propriétés suivantes : le sous-arbre gauche d'un nœud a une clé inférieure ou égale à la clé de son nœud parent, le sous-arbre droit d'un nœud a une clé supérieure à la clé de son nœud parent, ainsi l’arbre de recherche binaire divise tous ses sous-arbres en deux segments : le sous-arbre gauche et le sous-arbre droit.

```bash
left_subtree (keys)  ≤  node (key)  ≤  right_subtree (keys)
```

## Recherche d'une valeur dans un arbre B

La recherche d'une valeur dans un arbre implique la comparaison de la valeur entrant avec la valeur sortant des nœuds. Ici aussi, nous parcourons les nœuds de gauche à droite et finalement avec le parent. Si la valeur recherchée ne correspond à aucune des valeurs sortantes, nous renvoyons le message non trouvé, sinon le message trouvé est renvoyé.

### Exemple

```python
class Node:
    def __init__(self, data):
        self.left = None
        self.right = None
        self.data = data
    # Insert method to create nodes
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
    # findval method to compare the value with nodes
    def findval(self, lkpval):
        if lkpval < self.data:
            if self.left is None:
                return str(lkpval)+" Not Found"
            return self.left.findval(lkpval)
        else if lkpval > self.data:
                if self.right is None:
                return str(lkpval)+" Not Found"
                return self.right.findval(lkpval)
            else:
                print(str(self.data) + ' is found')
    # Print the tree
    def PrintTree(self):
        if self.left:
            self.left.PrintTree()
        print(self.data),
        if self.right:
            self.right.PrintTree()
root = Node(12)
root.insert(6)
root.insert(14)
root.insert(3)
print(root.findval(7))
print(root.findval(14))
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
7 Not Found
14 is found
```
