Le mot pile (*stack* en anglais) signifie disposer des objets les uns sur les autres. C'est de la même manière que la mémoire est allouée dans cette structure de données. Elle stocke les éléments de données de la même manière qu'un tas d'assiettes sont stockées les unes au-dessus des autres dans la cuisine. La structure de données de la pile permet d'effectuer des opérations à une extrémité, que l'on appelle le sommet de la pile, et c'est uniquement à partir de cette extrémité que l'on peut ajouter ou supprimer des éléments.

Dans une pile, l'élément inséré en dernier dans l'ordre sortira en premier car nous ne pouvons retirer que le haut de la pile. Cette caractéristique est connue sous le nom de caractéristique **Last in First Out** (*LIFO*). Les opérations d'ajout et de retrait des éléments sont connues sous le nom de **PUSH** et **POP**. Dans le programme suivant, nous les implémentons comme des fonctions add et remove. Nous déclarons une liste vide et utilisons les méthodes ```append()``` et ```pop()``` pour ajouter et supprimer les éléments de données.

## PUSH dans une pile

Comprenons comment utiliser PUSH dans la pile. Référez-vous au programme mentionné ci-dessous :

### Exemple

```python
class Stack:
    def __init__(self):
        self.stack = []

    def add(self, dataval):
        # Use list append method to add element
        if dataval not in self.stack:
            self.stack.append(dataval)
            return True
        else:
            return False

    # Use peek to look at the top of the stack
    def peek(self):     
        return self.stack[-1]

AStack = Stack()
AStack.add("Mon")
AStack.add("Tue")
AStack.peek()
print(AStack.peek())
AStack.add("Wed")
AStack.add("Thu")
print(AStack.peek())
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Tue
Thu
```

## POP à partir d'une pile

Comme nous savons que nous ne pouvons supprimer que l'élément de données le plus haut de la pile, nous implémentons un programme python qui le fait. La fonction remove du programme suivant renvoie l'élément le plus haut. Nous vérifions l'élément le plus haut en calculant d'abord la taille de la pile, puis nous utilisons la méthode pop() intégrée pour trouver l'élément le plus haut.

```python
class Stack:
    def __init__(self):
        self.stack = []

    def add(self, dataval):
    # Use list append method to add element
        if dataval not in self.stack:
            self.stack.append(dataval)
            return True
        else:
            return False

    # Use list pop method to remove element
    def remove(self):
        if len(self.stack) <= 0:
            return ("No element in the Stack")
        else:
            return self.stack.pop()

AStack = Stack()
AStack.add("Mon")
AStack.add("Tue")
AStack.add("Wed")
AStack.add("Thu")
print(AStack.remove())
print(AStack.remove())
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Thu
Wed
```