La structure de données la plus élémentaire en Python est la **séquence**
Chaque élément d'une séquence est identifié par un nombre - aussi appelé "index" ou "indice" qui représente sa position au sein de la séquence. Le premier indice est zéro, le deuxième indice est un, et ainsi de suite.

Python possède six types de séquences intégrées, mais les plus courantes sont les listes et les tuples, que nous verrons dans ce tutoriel.

Il y a certaines choses que vous pouvez faire avec tous les types de séquences. Ces opérations comprennent l'indexation, le découpage, l'addition, la multiplication et la vérification de l'appartenance. En outre, Python dispose de fonctions intégrées pour déterminer la longueur d'une séquence et pour trouver ses éléments les plus grands et les plus petits.

## Listes Python

La liste est le type de données le plus polyvalent disponible en Python, qui peut être écrit comme une liste de valeurs séparées par des virgules (éléments) entre crochets. Ce qui est important dans une liste, c'est que les éléments qui la composent ne doivent pas nécessairement être du même type.

Pour créer une liste, il suffit de mettre entre crochets différentes valeurs séparées par des virgules. Par exemple :

```python
list1 = ['physics', 'chemistry', 1997, 2000]
list2 = [1, 2, 3, 4, 5]
list3 = ["a", "b", "c", "d"]
```

Comme pour les indices de chaînes de caractères, les indices de listes commencent à 0, et les listes peuvent être découpées, concaténées, etc.

## Accès aux valeurs dans les listes

Pour accéder aux valeurs des listes, utilisez les crochets pour le découpage ainsi que l'indice ou les indices pour obtenir la valeur disponible à cet indice. Par exemple :

```python
#!/usr/bin/python3

list1 = ['physics', 'chemistry', 1997, 2000]
list2 = [1, 2, 3, 4, 5, 6, 7]

print("list1[0]: ", list1[0])
print("list2[1:5]: ", list2[1:5])
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
list1[0]:  physics
list2[1:5]:  [2, 3, 4, 5]
```

## Mise à jour des listes

Vous pouvez mettre à jour un ou plusieurs éléments de listes en indiquant la tranche à gauche de l'opérateur d'affectation, et vous pouvez ajouter des éléments dans une liste avec la méthode ```append()```. Par exemple :

```python
#!/usr/bin/python3

list = ['physics', 'chemistry', 1997, 2000]
print("Value available at index 2 :", list[2])

list[2] = 2001
print("New value available at index 2 :", list[2])
```

__Remarque__ : La méthode ```append()``` est abordée dans la section suivante.

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Value available at index 2 : 1997
New value available at index 2 : 2001
```

## Suppression d'éléments de liste

Pour supprimer un élément de liste, vous pouvez utiliser l'instruction del si vous savez exactement quel élément supprimer. Vous pouvez utiliser la méthode remove() si vous ne savez pas exactement quel élément supprimer. Par exemple

```python
#!/usr/bin/python3

list = ['physics', 'chemistry', 1997, 2000]
print(list)

del list[2]
print("After deleting value at index 2 :", list)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
['physics', 'chemistry', 1997, 2000]
After deleting value at index 2 : ['physics', 'chemistry', 2000]
```

__Remarque__ : La méthode ```remove()``` est abordée dans la section suivante.

## Opérations de base sur les listes

Les listes répondent aux opérateurs ```+``` et ```*``` de la même manière que les chaînes de caractères. Ici aussi, il s'agit de concaténation et de répétition, sauf que le résultat est une nouvelle liste et non une chaîne de caractères.

En fait, les listes répondent à toutes les opérations de séquence générale que nous avons utilisées sur les chaînes de caractères dans le chapitre précédent.

| **Expression Python** | **Résultats** | **Description** |
| --- | --- | --- |
| ```len([1, 2, 3])``` | ```3``` | Longueur |
| ```[1, 2, 3] + [4, 5, 6]``` | ```[1, 2, 3, 4, 5, 6]``` | Concaténation |
| ```['Hi!'] * 4``` | ```['Hi!', 'Hi!', 'Hi!', 'Hi!']``` | Répétition |
| ```3 in [1, 2, 3]``` | ```True``` | Adhésion |
| ```for x in [1,2,3] : print(x,end = ' ')``` | ```1 2 3``` | Itération |

## Indexation, découpage et matrices

Les listes étant des séquences, l'indexation et le découpage fonctionnent de la même manière pour les listes que pour les chaînes de caractères.

Supposons l'entrée suivante :

```python
L = ['C++', 'Java', 'Python']
```

| **Expression Python** | **Résultats** | **Description** |
| --- | --- | --- |
| ```L[2]``` | ```Python``` | Les décalages commencent à zéro. |
| ```L[-2]``` | ```Java``` | Négatif : compter à partir de la droite. |
| ```L[1:]``` | ```['Java', 'Python']``` | Découpage des sections de recherche. |

## Fonctions et méthodes de liste intégrées

Python inclut les fonctions de liste suivantes :

- ```len(list)``` : Donne la longueur totale de la liste.
- ```max(list)``` : Retourne l'élément de la liste avec la valeur maximale.
- ```min(list)``` : Retourne l'élément de la liste avec la valeur minimale.
- ```list(seq)``` : Convertit un tuple en liste.

Python comprend les méthodes de la liste suivante :

- ```list.append(obj)``` : Ajoute l'objet obj à la liste.
- ```list.count(obj)``` : Retourne le nombre d'occurrences de l'objet dans la liste.
- ```list.extend(seq)``` : Ajoute le contenu de la seq à la liste.
- ```list.index(obj)``` : Retourne l'indice le plus bas dans la liste où l'objet apparaît.
- ```list.insert(index, obj)``` : Insère l'objet obj dans la liste à l'emplacement de l'index.
- ```list.pop(obj = list[-1])``` : Retire et retourne le dernier objet ou obj de la liste.
- ```list.remove(obj)``` : Supprime l'objet obj de la liste.
- ```list.reverse()``` : Inverse les objets de la liste à la place.
- ```list.sort([func])``` : Trie les objets de la liste, utilise le func de comparaison s'il est donné.
