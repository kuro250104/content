Une liste liée est une séquence d'éléments de données, qui sont reliés entre eux par des liens. Chaque élément de données contient une connexion vers un autre élément de données sous la forme d'un pointeur. Python n'a pas de listes liées dans sa bibliothèque standard. Nous implémentons le concept de listes liées en utilisant le concept de nœuds, comme nous l'avons vu dans le chapitre précédent.

Nous avons déjà vu comment créer une classe de nœuds et comment parcourir les éléments d'un nœud. Dans ce cours, nous allons étudier les types de listes liées connues sous le nom de listes singulièrement liées. Dans ce type de structure de données, il n'y a qu'un seul lien entre deux éléments de données. Nous créons une telle liste et créons des méthodes supplémentaires pour insérer, mettre à jour et supprimer des éléments de la liste.

## Création d'une liste liée

Une liste liée est créée en utilisant la classe Node que nous avons étudiée dans le dernier chapitre. Nous créons un objet Node et une autre classe pour utiliser cet objet. Nous passons les valeurs appropriées à travers l'objet node pour pointer vers les éléments de données suivants. Le programme ci-dessous crée la liste liée avec trois éléments de données. Dans la section suivante, nous verrons comment traverser la liste liée.

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None

class SLinkedList:
    def __init__(self):
        self.headval = None

list1 = SLinkedList()
list1.headval = Node("Mon")
e2 = Node("Tue")
e3 = Node("Wed")
# Link first Node to second node
list1.headval.nextval = e2

# Link second Node to third node
e2.nextval = e3
```

## Traverser une liste liée

Les listes singulièrement liées ne peuvent être parcourues que dans le sens direct en commençant par le premier élément de données. Nous imprimons simplement la valeur de l'élément de données suivant en assignant le pointeur du nœud suivant à l'élément de données actuel.

### Exemple

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None

class SLinkedList:
    def __init__(self):
        self.headval = None

    def listprint(self):
        printval = self.headval
        while printval is not None:
            print(printval.dataval)
            printval = printval.nextval

list = SLinkedList()
list.headval = Node("Mon")
e2 = Node("Tue")
e3 = Node("Wed")

# Link first Node to second node
list.headval.nextval = e2

# Link second Node to third node
e2.nextval = e3

list.listprint()
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Mon
Tue
Wed
```

## Insertion dans une liste liée

L'insertion d'un élément dans la liste liée implique la réaffectation des pointeurs des nœuds existants au nœud nouvellement inséré. Selon que le nouvel élément de données est inséré au début, au milieu ou à la fin de la liste liée, nous avons les scénarios suivants.

### Insertion au début

Cela implique de faire pointer le pointeur suivant du nouveau nœud de données vers la tête actuelle de la liste liée. Ainsi, la tête actuelle de la liste liée devient le deuxième élément de données et le nouveau nœud devient la tête de la liste liée.

#### Exemple

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None

class SLinkedList:
    def __init__(self):
        self.headval = None
    # Print the linked list
    def listprint(self):
        printval = self.headval
        while printval is not None:
            print(printval.dataval)
            printval = printval.nextval
    def AtBegining(self,newdata):
        NewNode = Node(newdata)

    # Update the new nodes next val to existing node
    NewNode.nextval = self.headval
    self.headval = NewNode

list = SLinkedList()
list.headval = Node("Mon")
e2 = Node("Tue")
e3 = Node("Wed")

list.headval.nextval = e2
e2.nextval = e3

list.AtBegining("Sun")
list.listprint()
```

#### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Sun
Mon
Tue
Wed
```

### Insertion à la fin

Cela implique de faire pointer le pointeur suivant de l'actuel dernier nœud de la liste liée vers le nouveau nœud de données. Ainsi, le dernier nœud actuel de la liste liée devient l'avant-dernier nœud de données et le nouveau nœud devient le dernier nœud de la liste liée.

#### Exemple

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None
class SLinkedList:
    def __init__(self):
        self.headval = None
    # Function to add newnode
    def AtEnd(self, newdata):
        NewNode = Node(newdata)
        if self.headval is None:
            self.headval = NewNode
            return
        laste = self.headval
        while(laste.nextval):
            laste = laste.nextval
        laste.nextval=NewNode
    # Print the linked list
    def listprint(self):
        printval = self.headval
        while printval is not None:
            print (printval.dataval)
            printval = printval.nextval

list = SLinkedList()
list.headval = Node("Mon")
e2 = Node("Tue")
e3 = Node("Wed")

list.headval.nextval = e2
e2.nextval = e3

list.AtEnd("Thu")

list.listprint()
```

#### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Mon
Tue
Wed
Thu
```

### Insertion entre deux nœuds de données

Cela implique de changer le pointeur d'un nœud spécifique pour qu'il pointe vers le nouveau nœud. Cela est possible en passant à la fois le nouveau nœud et le nœud existant, après quoi le nouveau nœud sera inséré. Nous définissons donc une classe supplémentaire qui changera le pointeur suivant du nouveau noeud en pointeur suivant du noeud central. Ensuite, nous assignons le nouveau noeud au pointeur suivant du noeud central.

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None
class SLinkedList:
    def __init__(self):
        self.headval = None

    # Function to add node
    def Inbetween(self,middle_node,newdata):
        if middle_node is None:
            print("The mentioned node is absent")
            return

        NewNode = Node(newdata)
        NewNode.nextval = middle_node.nextval
        middle_node.nextval = NewNode

    # Print the linked list
    def listprint(self):
        printval = self.headval
        while printval is not None:
            print(printval.dataval)
            printval = printval.nextval

list = SLinkedList()
list.headval = Node("Mon")
e2 = Node("Tue")
e3 = Node("Thu")

list.headval.nextval = e2
e2.nextval = e3

list.Inbetween(list.headval.nextval,"Fri")

list.listprint()
```

#### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Mon
Tue
Fri
Thu
```

## Suppression d'un élément

Nous pouvons supprimer un noeud existant en utilisant la clé de ce noeud. Dans le programme ci-dessous, nous localisons le noeud précédent du noeud qui doit être supprimé, puis nous faisons pointer le pointeur suivant de ce noeud vers le noeud suivant du noeud à supprimer.

### Exemple

```python
class Node:
    def __init__(self, data=None):
        self.data = data
        self.next = None
class SLinkedList:
    def __init__(self):
        self.head = None

    def Atbegining(self, data_in):
        NewNode = Node(data_in)
        NewNode.next = self.head
        self.head = NewNode

    # Function to remove node
    def RemoveNode(self, Removekey):
        HeadVal = self.head
            
        if (HeadVal is not None):
            if (HeadVal.data == Removekey):
                self.head = HeadVal.next
                HeadVal = None
                return
        while (HeadVal is not None):
            if HeadVal.data == Removekey:
                break
            prev = HeadVal
            HeadVal = HeadVal.next

        if (HeadVal == None):
            return

        prev.next = HeadVal.next
            HeadVal = None

   def LListprint(self):
        printval = self.head
        while printval:
            print(printval.data),
            printval = printval.next

llist = SLinkedList()
llist.Atbegining("Mon")
llist.Atbegining("Tue")
llist.Atbegining("Wed")
llist.Atbegining("Thu")
llist.RemoveNode("Tue")
llist.LListprint()
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Thu
Wed
Mon
```
