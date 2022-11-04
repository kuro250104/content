Nous avons déjà vu la liste liée dans le chapitre précédent dans laquelle il est possible de voyager uniquement vers l'avant. Dans ce chapitre, nous verrons un autre type de liste liée dans laquelle il est possible de voyager à la fois vers l'avant et vers l'arrière. Une telle liste est appelée liste doublement liée. Voici les caractéristiques de la liste doublement liée.

- Une liste à double lien contient un élément de lien appelé first et last.
- Chaque lien porte un ou plusieurs champs de données et deux champs de lien appelés next et prev.
- Chaque lien est lié à son lien suivant par son lien suivant.
- Chaque lien est lié à son lien précédent à l'aide de son lien précédent.
- Le dernier lien porte un lien comme null pour marquer la fin de la liste.

## Création d'une liste doublement liée

Nous créons une liste doublement liée en utilisant la classe Node. Nous utilisons maintenant la même approche que celle utilisée dans la liste à liaison simple, mais les pointeurs head et next seront utilisés pour une affectation correcte afin de créer deux liens dans chacun des nœuds en plus des données présentes dans le nœud.

### Exemple

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

class doubly_linked_list:
    def __init__(self):
        self.head = None

    # Adding data elements		
    def push(self, NewVal):
        NewNode = Node(NewVal)
        NewNode.next = self.head
        if self.head is not None:
            self.head.prev = NewNode
        self.head = NewNode

    # Print the Doubly Linked list		
    def listprint(self, node):
        while (node is not None):
            print(node.data),
            last = node
            node = node.next

dllist = doubly_linked_list()
dllist.push(12)
dllist.push(8)
dllist.push(62)
dllist.listprint(dllist.head)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
62 8 12
```

## Insertion dans une liste doublement liée

Ici, nous allons voir comment insérer un nœud dans la liste doublement liée à l'aide du programme suivant. Le programme utilise une méthode nommée insert qui insère le nouveau nœud à la troisième position à partir de la tête de la liste doublement liée.

### Exemple

```python
# Create the Node class
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

# Create the doubly linked list
class doubly_linked_list:
    def __init__(self):
        self.head = None

    # Define the push method to add elements		
    def push(self, NewVal):
        NewNode = Node(NewVal)
        NewNode.next = self.head
        if self.head is not None:
            self.head.prev = NewNode
        self.head = NewNode

    # Define the insert method to insert the element		
    def insert(self, prev_node, NewVal):
        if prev_node is None:
            return
        NewNode = Node(NewVal)
        NewNode.next = prev_node.next
        prev_node.next = NewNode
        NewNode.prev = prev_node
        if NewNode.next is not None:
            NewNode.next.prev = NewNode

    # Define the method to print the linked list 
    def listprint(self, node):
        while (node is not None):
            print(node.data),
            last = node
            node = node.next

dllist = doubly_linked_list()
dllist.push(12)
dllist.push(8)
dllist.push(62)
dllist.insert(dllist.head.next, 13)
dllist.listprint(dllist.head)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
62  8  13  12
```

## Ajouter à une liste doublement liée

L'ajout à une liste doublement liée ajoutera l'élément à la fin.

### Exemple

```python
# Create the node class
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None
# Create the doubly linked list class
class doubly_linked_list:
    def __init__(self):
        self.head = None

    # Define the push method to add elements at the begining
    def push(self, NewVal):
        NewNode = Node(NewVal)
        NewNode.next = self.head
        if self.head is not None:
            self.head.prev = NewNode
        self.head = NewNode

    # Define the append method to add elements at the end
    def append(self, NewVal):
        NewNode = Node(NewVal)
        NewNode.next = None
        if self.head is None:
            NewNode.prev = None
            self.head = NewNode
            return
        last = self.head
        while (last.next is not None):
            last = last.next
        last.next = NewNode
        NewNode.prev = last
        return

    # Define the method to print
    def listprint(self, node):
        while (node is not None):
            print(node.data),
            last = node
            node = node.next

dllist = doubly_linked_list()
dllist.push(12)
dllist.append(9)
dllist.push(8)
dllist.push(62)
dllist.append(45)
dllist.listprint(dllist.head)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
62 8 12 9 45
```

__Remarque__ : la position des éléments 9 et 45 pour l'opération d'ajout.