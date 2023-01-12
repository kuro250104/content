Un tuple est une séquence d'objets Python immuables. Les tuples sont des séquences, tout comme les listes. La principale différence entre les tuples et les listes est que les tuples ne peuvent pas être modifiés, contrairement aux listes. Les tuples utilisent des parenthèses, alors que les listes utilisent des crochets.

Créer un tuples est aussi simple que de mettre différentes valeurs séparées par des virgules. En option, vous pouvez également mettre ces valeurs séparées par des virgules entre parenthèses. Par exemple :

```python
tup1 = ('physics', 'chemistry', 1997, 2000)
tup2 = (1, 2, 3, 4, 5)
tup3 = "a", "b", "c", "d"
```

Le tuple vide est écrit comme deux parenthèses ne contenant rien :

```python
tup1 = ()
```

Pour écrire un tuple contenant une seule valeur, vous devez inclure une virgule, même s'il n'y a qu'une seule valeur.

```python
tup1 = (50,)
```

Comme les indices de chaînes de caractères, les indices de tuple commencent à 0, et ils peuvent être découpés, concaténés, etc.

## Accès aux valeurs des tuples

Pour accéder aux valeurs d'un tuple, il faut utiliser les crochets pour le découpage ainsi que l'indice ou les indices pour obtenir la valeur disponible à cet indice. Par exemple :

```python
#!/usr/bin/python3

tup1 = ('physics', 'chemistry', 1997, 2000)
tup2 = (1, 2, 3, 4, 5, 6, 7)

print("tup1[0]:", tup1[0])
print("tup2[1:5]:", tup2[1:5])
# When the above code is executed, it produces the following result :
tup1[0]: physics
tup2[1:5]: (2, 3, 4, 5)
```

## Mise à jour des Tuples

Les tuples sont immuables, ce qui signifie que vous ne pouvez pas mettre à jour ou modifier les valeurs des éléments des tuples. Vous pouvez prendre des parties des tuples existants pour créer de nouveaux tuples comme le montre l'exemple suivant :

```python
#!/usr/bin/python3

tup1 = (12, 34.56)
tup2 = ('abc', 'xyz')

# Following action is not valid for tuples
# tup1[0] = 100;

# So let's create a new tuple as follows
tup3 = tup1 + tup2
print(tup3)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
(12, 34.56, 'abc', 'xyz')
```

## Supprimer des éléments de tuple

La suppression d'éléments individuels de tuple n'est pas possible. Il n'y a, bien sûr, rien de mal à reconstituer un autre tuple en éliminant les éléments non désirés.

Pour supprimer explicitement un tuple entier, il suffit d'utiliser l'instruction ```del```. Par exemple :

```python
#!/usr/bin/python3

tup = ('physics', 'chemistry', 1997, 2000)

print(tup)
del tup;
print("After deleting tup :")
print(tup)
```

Cela donne le résultat suivant.

```bash
('physics', 'chemistry', 1997, 2000)
After deleting tup :
Traceback (most recent call last):
    File "test.py", line 9, in <module>
        print tup;
NameError: name 'tup' is not defined
```

__Remarque__ : Une exception est levée. C'est parce qu'après ```del tup```, le tuple n'existe plus.

## Opérations de base sur les tuples

Les tuples répondent aux opérateurs ```+``` et ```*``` de la même manière que les chaînes de caractères; ils signifient ici aussi concaténation et répétition, sauf que le résultat est un nouveau tuple, et non une chaîne de caractères.

En fait, les tuples répondent à toutes les opérations générales de séquence que nous avons utilisées sur les chaînes de caractères dans le chapitre précédent.

| **Expression Python** | **Résultats** | **Description** |
| --- | --- | --- |
| ```len((1, 2, 3))``` | ```3``` | Longueur |
| ```(1, 2, 3) + (4, 5, 6)``` | ```(1, 2, 3, 4, 5, 6)``` | Concaténation |
| ```('Hi!',) * 4``` | ```('Hi!', 'Hi!', 'Hi!', 'Hi!')``` | Répétition |
| ```3 in (1, 2, 3)``` | ```True``` | Adhésion |
| ```for x in (1,2,3) : print(x, end = ' ')``` | ```1 2 3``` | Itération |

## Indexation, découpage et matrices

Puisque les tuples sont des séquences, l'indexation et le découpage fonctionnent de la même manière pour les tuples que pour les chaînes de caractères, en supposant l'entrée suivante :

```python
T=('C++', 'Java', 'Python')
```

| **Expression Python** | **Résultats** | **Description** |
| --- | --- | --- |
| ```T[2]``` | ```Python``` | Les décalages commencent à zéro. |
| ```T[-2]``` | ```Java``` | Négatif : Compter à partir de la droite. |
| ```T[1:]``` | ```('Java', 'Python')``` | Découpage des sections de recherche. |

## Délimiteurs non englobants

Un ensemble d'objets multiples, séparés par des virgules, écrits sans symboles d'identification, c'est-à-dire des crochets pour les listes, des parenthèses pour les tuples, etc., est considéré comme un tuples par défaut, comme indiqué dans ces courts exemples.

## Fonctions tuple intégrées

Python inclut les fonctions tuple suivantes :

- ```len(tuple)``` : Donne la longueur totale du tuple.
- ```max(tuple)``` : Retourne l'élément du tuple avec la valeur maximale.
- ```min(tuple)``` : Retourne l'élément du tuple ayant la valeur minimale.
- ```tuple(seq)``` : Convertit une liste en tuple.
