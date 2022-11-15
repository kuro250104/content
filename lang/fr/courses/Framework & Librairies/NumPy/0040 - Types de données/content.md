## Introduction

NumPy prend en charge une variété beaucoup plus grande de types numériques que Python. Le tableau suivant présente les différents types de données scalaires définis dans NumPy.

**Types de données et description**

- **bool_** - Booléen (vrai ou faux) stocké sous forme d'octet.
- **int_** - Type d'entier par défaut (identique au C long ; normalement soit int64 ou int32)
- **intc** - Identique à int en C (normalement int32 ou int64)
- **intp** - Nombre entier utilisé pour l'indexation (identique à ssize_t en C ; normalement int32 ou int64)
- **int8** - Octet (-128 à 127)
- **int16** - Entier (-32768 à 32767)
- **int32** - Entier (-2147483648 à 2147483647)
- **int64** - Entier (-9223372036854775808 à 9223372036854775807)
- **uint8** - Nombre entier non signé (0 à 255)
- **uint16** - Nombre entier non signé (0 à 65535)
- **uint32** - Nombre entier non signé (0 à 4294967295)
- **uint64** - Nombre entier non signé (0 à 18446744073709551615)
- **float_** - Abréviation de float64
- **float16** - Flottant de demi-précision : bit de signe, exposant de 5 bits, mantisse de 10 bits.
- **float32** - Flottant de précision simple : bit de signe, exposant de 8 bits, mantisse de 23 bits.
- **float64** - Flottant à double précision : bit de signe, exposant de 11 bits, mantisse de 52 bits.
- **complex_** - Abréviation de complexe128
- **complex64** - Nombre complexe, représenté par deux flottants de 32 bits (composantes réelles et imaginaires).
- **complex128** - Nombre complexe, représenté par deux flottants de 64 bits (composantes réelles et imaginaires).

Les types numériques de NumPy sont des instances d'objets dtype (data-type), chacun ayant des caractéristiques uniques. Les dtypes sont disponibles en tant que np.bool_, np.float32, etc.

## Objets de type de données (dtype)

Un objet de type de données décrit l'interprétation d'un bloc fixe de mémoire correspondant à un tableau, en fonction des aspects suivants : - le type d'objet est un objet de type de données.

- Type de données (entier, flottant ou objet Python)
- Taille des données
- Ordre des octets (little-endian ou big-endian)
- Dans le cas d'un type structuré, les noms des champs, le type de données de chaque champ et la partie du bloc de mémoire occupée par chaque champ.
- Si le type de données est un sous-réseau, sa forme et son type de données

L'ordre des octets est déterminé par la préfixation de "<" ou ">" au type de données. <' signifie que le codage est little-endian (l'octet le moins significatif est stocké à la plus petite adresse). >' signifie que le codage est big-endian (l'octet le plus significatif est stocké à l'adresse la plus petite).

Un objet dtype est construit à l'aide de la syntaxe suivante -

```python
numpy.dtype(object, align, copy)
```

Les paramètres sont -

- **Object** − A convertir en objet de type de données
- **Align** − Si vrai, ajoute du remplissage au champ pour le rendre similaire à une structure C.
- **Copy** − Crée une nouvelle copie de l'objet dtype. Si false, le résultat est une référence à l'objet de type de données intégré.

### Exemple 1

```python
# using array-scalar type 
import numpy as np 
dt = np.dtype(np.int32) 
print dt
```

Le résultat est le suivant -

```python
int32
```

### Example 2

```python
#int8, int16, int32, int64 can be replaced by equivalent string 'i1', 'i2','i4', etc. 
import numpy as np 

dt = np.dtype('i4')
print dt
```

Le résultat est le suivant -

```python
int32
```

### Exemple 3

```python
# using endian notation 
import numpy as np 
dt = np.dtype('>i4') 
print dt
```

Le résultat est le suivant -

```python
>i4
```

Les exemples suivants montrent l'utilisation du type de données structuré. Ici, il s'agit de déclarer le nom du champ et le type de données scalaires correspondant.

### Exemple 4

```python
# first create structured data type 
import numpy as np 
dt = np.dtype([('age',np.int8)]) 
print dt
```

Le résultat est le suivant -

```python
[('age', 'i1')] 
```

### Exemple 5

```python
# now apply it to ndarray object 
import numpy as np 

dt = np.dtype([('age',np.int8)]) 
a = np.array([(10,),(20,),(30,)], dtype = dt) 
print a
```

Le résultat est le suivant -

```python
[(10,) (20,) (30,)]
```

### Exemple 6

```python
# file name can be used to access content of age column 
import numpy as np 

dt = np.dtype([('age',np.int8)]) 
a = np.array([(10,),(20,),(30,)], dtype = dt) 
print a['age']
```

Le résultat est le suivant -

```python
[10 20 30]
```

### Exemple 7

Les exemples suivants définissent un type de données structuré appelé student avec un champ de type string 'name', un champ de type integer 'age' et un champ de type float 'marks'. Ce type de données est appliqué à l'objet ndarray.

```python
import numpy as np 
student = np.dtype([('name','S20'), ('age', 'i1'), ('marks', 'f4')]) 
print student
```

Le résultat est le suivant -

```python
[('name', 'S20'), ('age', 'i1'), ('marks', '<f4')])
```

### Exemple 8

```python
import numpy as np 

student = np.dtype([('name','S20'), ('age', 'i1'), ('marks', 'f4')]) 
a = np.array([('abc', 21, 50),('xyz', 18, 75)], dtype = student) 
print a
```

Le résultat est le suivant -

```python
[('abc', 21, 50.0), ('xyz', 18, 75.0)]
```

Chaque type de données intégré possède un code de caractère qui l'identifie de manière unique.

- **'b'** − boolean
- **'i'** − Nombre entier (signé)
- **'u'** − entier non signé
- **'f'** − virgule flottante
- **'c'** − point flottant complexe
- **'m'** − timedelta
- **'M'** − datetime
- **'O'** − Objets (Python)
- **'S', 'a'** − (octet) chaîne de caractères
- **'U'** − Unicode
- **'V'** − données brutes (void)