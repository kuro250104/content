Les matrices sont un cas particulier de tableaux à deux dimensions où chaque élément de données a strictement la même taille. Ainsi, toute matrice est également un tableau à deux dimensions, mais pas l'inverse.

Les matrices sont des structures de données très importantes pour de nombreux calculs mathématiques et scientifiques. Comme nous avons déjà abordé la structure de données des tableaux bidimensionnels dans le chapitre précédent, nous allons nous concentrer sur les opérations de structure de données spécifiques aux matrices dans ce chapitre.

Nous utiliserons également le paquetage ```numpy``` pour la manipulation des données matricielles.

## Exemple de matrice

Considérons le cas d'un enregistrement de la température pendant une semaine, mesurée le matin, à midi, le soir et la nuit. Il peut être présenté comme une matrice 7X5 en utilisant un tableau et la méthode ```reshape``` disponible dans ```numpy```.

```python
from numpy import * 
a = array([['Mon',18,20,22,17],['Tue',11,18,21,18],
    ['Wed',15,21,20,19],['Thu',11,20,22,21],
    ['Fri',18,17,23,22],['Sat',12,22,20,18],
    ['Sun',13,15,19,16]])
m = reshape(a,(7,5))
print(m)
```

### Réponse

Les données ci-dessus peuvent être représentées comme un tableau à deux dimensions comme ci-dessous :

```bash
[
    ['Mon' '18' '20' '22' '17']
    ['Tue' '11' '18' '21' '18']
    ['Wed' '15' '21' '20' '19']
    ['Thu' '11' '20' '22' '21']
    ['Fri' '18' '17' '23' '22']
    ['Sat' '12' '22' '20' '18']
    ['Sun' '13' '15' '19' '16']
]
```

## Accès aux valeurs

On peut accéder aux éléments de données d'une matrice en utilisant les index. La méthode d'accès est la même que celle utilisée pour accéder aux données dans un tableau à deux dimensions.

### Exemple

```python
from numpy import * 
m = array([['Mon',18,20,22,17],['Tue',11,18,21,18],
    ['Wed',15,21,20,19],['Thu',11,20,22,21],
    ['Fri',18,17,23,22],['Sat',12,22,20,18],
    ['Sun',13,15,19,16]])

# Print data for Wednesday
print(m[2])

# Print data for friday evening
print(m[4][3])
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
['Wed', 15, 21, 20, 19]
23
```

## Ajouter une ligne

Pour ajouter une ligne dans la matrice, nous devons utiliser la méthode ```apend()```. 

### Exemple

```python
from numpy import * 
m = array([['Mon',18,20,22,17],['Tue',11,18,21,18],
    ['Wed',15,21,20,19],['Thu',11,20,22,21],
    ['Fri',18,17,23,22],['Sat',12,22,20,18],
    ['Sun',13,15,19,16]])
m_r = append(m,[['Avg',12,15,13,11]],0)

print(m_r)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
[
    ['Mon' '18' '20' '22' '17']
    ['Tue' '11' '18' '21' '18']
    ['Wed' '15' '21' '20' '19']
    ['Thu' '11' '20' '22' '21']
    ['Fri' '18' '17' '23' '22']
    ['Sat' '12' '22' '20' '18']
    ['Sun' '13' '15' '19' '16']
    ['Avg' '12' '15' '13' '11']
]
```

## Ajout d'une colonne

Nous pouvons ajouter une colonne à une matrice en utilisant la méthode ```insert()```. Ici nous devons mentionner l'index où nous voulons ajouter la colonne et un tableau contenant les nouvelles valeurs des colonnes ajoutées. Dans l'exemple ci-dessous nous ajoutons une nouvelle colonne à la cinquième position depuis le début.

### Exemple

```python
from numpy import * 
m = array([['Mon',18,20,22,17],['Tue',11,18,21,18],
    ['Wed',15,21,20,19],['Thu',11,20,22,21],
    ['Fri',18,17,23,22],['Sat',12,22,20,18],
    ['Sun',13,15,19,16]])
m_c = insert(m,[5],[[1],[2],[3],[4],[5],[6],[7]],1)

print(m_c)
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
[
   ['Mon' '18' '20' '22' '17' '1']
   ['Tue' '11' '18' '21' '18' '2']
   ['Wed' '15' '21' '20' '19' '3']
   ['Thu' '11' '20' '22' '21' '4']
   ['Fri' '18' '17' '23' '22' '5']
   ['Sat' '12' '22' '20' '18' '6']
   ['Sun' '13' '15' '19' '16' '7']
]
```

## Supprimer une ligne

Nous pouvons supprimer une ligne d'une matrice en utilisant la méthode ```delete()```. Nous devons spécifier l'index de la ligne et également la valeur de l'axe qui est 0 pour une ligne et 1 pour une colonne.

### Exemple

```python
from numpy import * 
m = array([['Mon',18,20,22,17],['Tue',11,18,21,18],
    ['Wed',15,21,20,19],['Thu',11,20,22,21],
    ['Fri',18,17,23,22],['Sat',12,22,20,18],
    ['Sun',13,15,19,16]])
m = delete(m,[2],0)

print(m)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
[
   ['Mon' '18' '20' '22' '17']
   ['Tue' '11' '18' '21' '18']
   ['Thu' '11' '20' '22' '21']
   ['Fri' '18' '17' '23' '22']
   ['Sat' '12' '22' '20' '18']
   ['Sun' '13' '15' '19' '16']
]
```

## Supprimer une colonne

Nous pouvons supprimer une colonne d'une matrice en utilisant la méthode ```delete()```. Nous devons spécifier l'index de la colonne et également la valeur de l'axe qui est 0 pour une ligne et 1 pour une colonne.

### Exemple

```python
from numpy import * 
m = array([['Mon',18,20,22,17],['Tue',11,18,21,18],
    ['Wed',15,21,20,19],['Thu',11,20,22,21],
    ['Fri',18,17,23,22],['Sat',12,22,20,18],
    ['Sun',13,15,19,16]])
m = delete(m,s_[2],1)

print(m)
```

### Réponse

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
[
    ['Mon' '18' '22' '17']
    ['Tue' '11' '21' '18']
    ['Wed' '15' '20' '19']
    ['Thu' '11' '22' '21']
    ['Fri' '18' '23' '22']
    ['Sat' '12' '20' '18']
    ['Sun' '13' '19' '16']
]
```

## Mettre à jour une ligne

Pour mettre à jour les valeurs de la ligne d'une matrice, il suffit de réaffecter les valeurs à l'indice de la ligne. Dans l'exemple ci-dessous, toutes les valeurs des données du jeudi sont marquées comme étant nulles. L'indice de cette ligne est 3.

### Exemple

```python
from numpy import * 
m = array([['Mon',18,20,22,17],['Tue',11,18,21,18],
    ['Wed',15,21,20,19],['Thu',11,20,22,21],
    ['Fri',18,17,23,22],['Sat',12,22,20,18],
    ['Sun',13,15,19,16]])
m[3] = ['Thu',0,0,0,0]

print(m)
```

### Réponse

Lorsque le code çi-dessus est exécuté, il produit le résultat suivant :

```bash
[
    ['Mon' '18' '20' '22' '17']
    ['Tue' '11' '18' '21' '18']
    ['Wed' '15' '21' '20' '19']
    ['Thu' '0' '0' '0' '0']
    ['Fri' '18' '17' '23' '22']
    ['Sat' '12' '22' '20' '18']
    ['Sun' '13' '15' '19' '16']
]
```
