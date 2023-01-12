Les variables ne sont rien d'autre que des emplacements mémoire réservés pour stocker des valeurs. Cela signifie que lorsque vous créez une variable, vous réservez un certain espace dans la mémoire.

En fonction du type de données d'une variable, l'interpréteur alloue la mémoire et décide de ce qui peut être stocké dans la mémoire réservée. Par conséquent, en affectant différents types de données aux variables, vous pouvez y stocker des entiers, des décimales ou des caractères.

## Attribution de valeurs aux variables

Les variables Python ne nécessitent pas de déclaration explicite pour réserver de l'espace mémoire. La déclaration se fait automatiquement lorsque vous attribuez une valeur à une variable. Le signe égal (=) est utilisé pour attribuer des valeurs aux variables.

L'opérande à gauche de l'opérateur ```=``` est le nom de la variable et l'opérande à droite de l'opérateur ```=``` est la valeur stockée dans la variable. Par exemple :

```python
#!/usr/bin/python3

counter = 100          # An integer assignment
miles   = 1000.0       # A floating point
name    = "John"       # A string

print(counter)
print(miles)
print(name)
```

Ici, 100, 1000.0 et "Microlead" sont les valeurs assignées aux variables counter, miles et name, respectivement. Cela produit le résultat suivant :

```bash
100
1000.0
John
```

## Affectation multiple

Python vous permet d'affecter une seule valeur à plusieurs variables simultanément.

Par exemple :

```python
a = b = c = 1
```

Ici, un objet entier est créé avec la valeur 1, et les trois variables sont affectées au même emplacement mémoire. Vous pouvez également affecter plusieurs objets à plusieurs variables. Par exemple :

```python
a, b, c = 1, 2, " john"
```

Ici, deux objets entiers avec les valeurs 1 et 2 sont affectés aux variables a et b respectivement, et un objet chaîne de caractères avec la valeur "john" est affecté à la variable c.

## Types de données standard

Les données stockées en mémoire peuvent être de plusieurs types. Par exemple, l'âge d'une personne est stocké sous forme de valeur numérique et son adresse est stockée sous forme de caractères alphanumériques. Python dispose de plusieurs types de données standard qui servent à définir les opérations possibles sur ces données et la méthode de stockage pour chacune d'entre elles.

Python dispose de cinq types de données standard :

- Nombres
- Chaîne de caractères
- Liste
- Tuple
- Dictionnaire

## Nombres Python

Les types de données numériques stockent des valeurs numériques. Les objets numériques sont créés lorsque vous leur attribuez une valeur. Par exemple :

```python
var1 = 1
var2 = 10
```

Vous pouvez également supprimer la référence à un objet numérique en utilisant l'instruction del. La syntaxe de l'instruction del est la suivante :

```python
del var1[,var2[,var3[....,varN]]]]
```

Vous pouvez supprimer un objet unique ou plusieurs objets à l'aide de l'instruction del.

Par exemple :

```python
del var
del var_a, var_b
```

Python prend en charge trois types numériques différents : 

- int (entiers signés)
- float (valeurs réelles à virgule)
- complex (nombres complexes)

Tous les entiers en Python3 sont représentés comme des entiers longs. Par conséquent, il n'existe pas de type numérique distinct pour les nombres longs.

## Exemples

Voici quelques exemples de nombres :

| **int** | **float** | **complex** |
| --- | --- | --- |
| 10 | 0.0 | 3.14j |
| 100 | 15.20 | 45.j |
| -786 | -21.9 | 9.322e-36j |
| 080 | 32.3+e18 | .876j |
| -0490 | -90. | -.6545+0J |
| -0x260 | -32.54e100 | 3e+26J |
| 0x69 | 70.2-E12 | 4.53e-7j |

Un nombre complexe est constitué d'une paire ordonnée de nombres réels à virgule flottante désignés par x + yj, où x et y sont des nombres réels et j est l'unité imaginaire.

## Chaînes de caractères Python

Les chaînes de caractères en Python sont identifiées comme un ensemble contigu de caractères représentés entre guillemets. Python autorise une paire de guillemets simples ou doubles. Les sous-ensembles de chaînes de caractères peuvent être extraits à l'aide de l'opérateur de découpage ([ ] et [ :] ) avec des indices commençant à 0 au début de la chaîne et allant de -1 à la fin.

Le signe plus (+) est l'opérateur de concaténation des chaînes de caractères et l'astérisque (*) est l'opérateur de répétition. Par exemple :

```python
#!/usr/bin/python3

str = 'Hello World!'

print(str)          # Prints complete string
print(str[0])       # Prints first character of the string
print(str[2:5])     # Prints characters starting from 3rd to 5th
print(str[2:])      # Prints string starting from 3rd character
print(str * 2)      # Prints string two times
print(str + "TEST") # Prints concatenated string
```

Cela donnera le résultat suivant :

```bash
Hello World!
H
llo
llo World!
Hello World!Hello World!
Hello World!TEST
```

## Listes Python

Les listes sont le plus polyvalent des types de données composées de Python. Une liste contient des éléments séparés par des virgules et placés entre crochets ([]). Dans une certaine mesure, les listes sont similaires aux tableaux en C. L'une des différences entre elles est que tous les éléments appartenant à une liste peuvent être de types de données différents.

Les valeurs stockées dans une liste sont accessibles à l'aide de l'opérateur de découpage ([ ] et [ :]) avec des indices commençant à 0 au début de la liste et allant jusqu'à la fin -1. Le signe plus (+) est l'opérateur de concaténation de liste, et l'astérisque (*) est l'opérateur de répétition. Par exemple :

```python
#!/usr/bin/python3

list = [ 'abcd', 786 , 2.23, 'john', 70.2 ]
tinylist = [123, 'john']

print(list)          # Prints complete list
print(list[0])       # Prints first element of the list
print(list[1:3])     # Prints elements starting from 2nd till 3rd 
print(list[2:])      # Prints elements starting from 3rd element
print(tinylist * 2)  # Prints list two times
print(list + tinylist) # Prints concatenated lists
This produces the following result −
['abcd', 786, 2.23, 'john', 70.200000000000003]
abcd
[786, 2.23]
[2.23, 'john', 70.200000000000003]
[123, 'john', 123, 'john']
['abcd', 786, 2.23, 'john', 70.200000000000003, 123, 'john']
```

## Tuples Python

Un tuple est un autre type de données de séquence qui est similaire à la liste. Un tuple est constitué d'un certain nombre de valeurs séparées par des virgules. Toutefois, contrairement aux listes, les tuples sont placés entre parenthèses.

La principale différence entre les listes et les tuples est la suivante : les listes sont placées entre crochets ( [ ] ) et leurs éléments et leur taille peuvent être modifiés, tandis que les tuples sont placés entre parenthèses ( ) et ne peuvent pas être mis à jour. Les tuples peuvent être considérés comme des listes en lecture seule. Par exemple :

```python
#!/usr/bin/python3

tuple = ( 'abcd', 786 , 2.23, 'john', 70.2  )
tinytuple = (123, 'john')

print(tuple)           # Prints complete tuple
print(tuple[0])        # Prints first element of the tuple
print(tuple[1:3])      # Prints elements starting from 2nd till 3rd 
print(tuple[2:])       # Prints elements starting from 3rd element
print(tinytuple * 2)   # Prints tuple two times
print(tuple + tinytuple) # Prints concatenated tuple
This produces the following result −
('abcd', 786, 2.23, 'john', 70.200000000000003)
abcd
(786, 2.23)
(2.23, 'john', 70.200000000000003)
(123, 'john', 123, 'john')
('abcd', 786, 2.23, 'john', 70.200000000000003, 123, 'john')
```

Le code suivant est invalide avec les tuples, car nous avons tenté de mettre à jour un tuple, ce qui n'est pas autorisé. Un cas similaire est possible avec les listes :

```python
#!/usr/bin/python3

tuple = ( 'abcd', 786 , 2.23, 'john', 70.2  )
list = [ 'abcd', 786 , 2.23, 'john', 70.2  ]
tuple[2] = 1000    # Invalid syntax with tuple
list[2] = 1000     # Valid syntax with list
```

## Dictionnaire Python

Les dictionnaires de Python sont une sorte de table de hachage. Ils fonctionnent comme les tableaux associatifs ou les hachages que l'on trouve en Perl et sont constitués de paires clé-valeur. La clé d'un dictionnaire peut être presque n'importe quel type Python, mais il s'agit généralement de nombres ou de chaînes de caractères. Les valeurs, quant à elles, peuvent être n'importe quel objet Python arbitraire.

Les dictionnaires sont entourés d'accolades ({ }) et les valeurs peuvent être assignées et accessibles à l'aide d'accolades carrées ([]). Par exemple :

```python
#!/usr/bin/python3

dict = {}
dict['one'] = "This is one"
dict[2]     = "This is two"

tinydict = {'name': 'john','code':6734, 'dept': 'sales'}

print(dict['one'])       # Prints value for 'one' key
print(dict[2])           # Prints value for 2 key
print(tinydict)          # Prints complete dictionary
print(tinydict.keys())   # Prints all the keys
print(tinydict.values()) # Prints all the values
This produces the following result −
This is one
This is two
{'name': 'john', 'dept': 'sales', 'code': 6734}
dict_keys(['name', 'dept', 'code'])
dict_values(['john', 'sales', 6734])
```

Les dictionnaires n'ont aucun concept d'ordre parmi les éléments. Il est incorrect de dire que les éléments sont "hors d'ordre" ; ils sont simplement non ordonnés.

## Conversion des types de données

Il est parfois nécessaire d'effectuer des conversions entre les types intégrés. Pour convertir entre les types, il suffit d'utiliser les noms de type comme une fonction.

Il existe plusieurs fonctions intégrées permettant d'effectuer la conversion d'un type de données à un autre. Ces fonctions renvoient un nouvel objet représentant la valeur convertie.
| Fonctions | |
| --- | --- | 
| ```int(x [,base])``` | Convertit ```x``` en un nombre entier. La base spécifie la base si x est une chaîne de caractères. |
| ```float(x)``` | Convertit ```x``` en un nombre à virgule flottante. |
| ```complex(real [,imag])``` | Crée un nombre complexe. |
| ```str(x)``` | Convertit l'objet ```x``` en une représentation de type chaîne de caractères. |
| ```repr(x)``` | Convertit l'objet ```x``` en une chaîne d'expression. |
| ```eval(str)``` | Évalue une chaîne de caractères et renvoie un objet. |
| ```tuple(s)``` | Convertit ```s``` en un tuple. |
| ```list(s)``` | Convertit ```s``` en une liste. |
| ```set(s)``` | Convertit ```s``` en un ensemble. |
| ```dict(d)``` | Crée un dictionnaire. ```d``` doit être une séquence de tuples (clé, valeur). |
| ```frozenset(s)``` | Convertit ```s``` en un frozenset. |
| ```chr(x)``` | Convertit un nombre entier en un caractère. |
| ```unichr(x)``` | Convertit un nombre entier en un caractère Unicode. |
| ```ord(x)``` | Convertit un seul caractère en sa valeur entière. |
| ```hex(x)``` | Convertit un nombre entier en une chaîne hexadécimale. |
| ```oct(x)``` | Convertit un nombre entier en une chaîne de caractères octales. |

