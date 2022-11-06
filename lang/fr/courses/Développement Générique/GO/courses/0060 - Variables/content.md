Une variable n'est rien d'autre que le nom donné à une zone de stockage que les programmes peuvent manipuler. Chaque variable en Go a un type spécifique, qui détermine la taille et la disposition de la mémoire de la variable, la gamme de valeurs qui peuvent être stockées dans cette mémoire, et l'ensemble des opérations qui peuvent être appliquées à la variable.

Le nom d'une variable peut être composé de lettres, de chiffres et du caractère de soulignement. Il doit commencer par une lettre ou un trait de soulignement. Les lettres majuscules et minuscules sont distinctes car Go est sensible à la casse. Sur la base des types de base expliqués dans le chapitre précédent, il y aura les types de variables de base suivants :

**Type et description**

**octet** : Généralement un seul octet (un octet). Il s'agit d'un type d'octet.
**int** : La taille la plus naturelle des entiers pour la machine.
**float32** : Une valeur à virgule flottante de simple précision.

Le langage de programmation Go permet également de définir divers autres types de variables tels que Enumeration, Pointer, Array, Structure, et Union, que nous aborderons dans les chapitres suivants. Dans ce chapitre, nous nous concentrerons uniquement sur les types de variables de base.

## Définition des variables dans Go

Une définition de variable indique au compilateur l'endroit et la quantité de stockage à créer pour la variable. Une définition de variable spécifie un type de données et contient une liste d'une ou de plusieurs variables de ce type, comme suit :

```go
var variable_list optional_data_type;
```

Ici, **optional_data_type** est un type de données Go valide incluant byte, int, float32, complex64, boolean ou tout objet défini par l'utilisateur, etc., et variable_list peut consister en un ou plusieurs noms d'identifiants séparés par des virgules. Quelques déclarations valides sont présentées ici :

```go
var  i, j, k int;
var  c, ch byte;
var  f, salary float32;
d =  42;
```

L'instruction ```var i, j, k ;``` déclare et définit les variables i, j et k ; ce qui indique au compilateur de créer des variables nommées i, j et k de type int.

Les variables peuvent être initialisées (se voir attribuer une valeur initiale) dans leur déclaration. Le type de la variable est automatiquement jugé par le compilateur en fonction de la valeur qui lui est passée. L'initialisateur se compose d'un signe égal suivi d'une expression constante comme suit :

```go
variable_name = value;
```

Par exemple,

```go
d = 3, f = 5;    // declaration of d and f. Here d and f are int 
```

Pour une définition sans initialisateur : les variables avec une durée de stockage statique sont implicitement initialisées avec nil (tous les octets ont la valeur 0) ; la valeur initiale de toutes les autres variables est la valeur zéro de leur type de données.

## Déclaration de type statique en Go

Une déclaration de variable de type statique donne l'assurance au compilateur qu'il existe une variable disponible avec le type et le nom donnés, de sorte que le compilateur peut poursuivre la compilation sans avoir besoin de connaître tous les détails de la variable. Une déclaration de variable n'a de sens qu'au moment de la compilation, le compilateur a besoin de la déclaration de variable réelle au moment de la liaison du programme.

### Exemple

Essayez l'exemple suivant, dans lequel la variable a été déclarée avec un type et initialisée dans la fonction principale.

```go
package main

import "fmt"

func main() {
    var x float64
    x = 20.0
    fmt.Println(x)
    fmt.Printf("x is of type %T\n", x)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
20
x is of type float64
```

## Déclaration dynamique de type / Inférence de type en Go

Une déclaration de variable de type dynamique demande au compilateur d'interpréter le type de la variable en fonction de la valeur qui lui est passée. Le compilateur n'exige pas qu'une variable ait un type statique comme condition nécessaire.

### Exemple

Essayez l'exemple suivant, où les variables ont été déclarées sans aucun type. Remarquez qu'en cas d'inférence de type, nous avons initialisé la variable y avec l'opérateur :=, alors que x est initialisé en utilisant l'opérateur =.

```go
package main

import "fmt"

func main() {
    var x float64 = 20.0

    y := 42 
    fmt.Println(x)
    fmt.Println(y)
    fmt.Printf("x is of type %T\n", x)
    fmt.Printf("y is of type %T\n", y)	
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
20
42
x is of type float64
y is of type int
```

## Déclaration de variables mixtes en Go

Des variables de différents types peuvent être déclarées en une seule fois en utilisant l'inférence de type.

### Exemple

```go
package main

import "fmt"

func main() {
    var a, b, c = 3, 4, "foo"  
        
    fmt.Println(a)
    fmt.Println(b)
    fmt.Println(c)
    fmt.Printf("a is of type %T\n", a)
    fmt.Printf("b is of type %T\n", b)
    fmt.Printf("c is of type %T\n", c)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
3
4
foo
a is of type int
b is of type int
c is of type string
```

## Les valeurs l et les valeurs r en Go

Il existe deux types d'expressions en Go :

- **lvalue** - Les expressions qui font référence à un emplacement mémoire sont appelées expressions "lvalue". Une lvalue peut apparaître à gauche ou à droite d'une affectation.
- **rvalue** - Le terme rvalue fait référence à une valeur de données qui est stockée à une certaine adresse en mémoire. Une rvalue est une expression à laquelle on ne peut pas attribuer de valeur, ce qui signifie qu'une rvalue peut apparaître du côté droit mais pas du côté gauche d'une affectation.

Les variables sont des lvalues et peuvent donc apparaître du côté gauche d'une affectation. Les littéraux numériques sont des rvalues et ne peuvent donc pas être assignés et ne peuvent pas apparaître sur le côté gauche.

L'instruction suivante est valide :

```go
x = 20.0
```

L'instruction suivante n'est pas valide. Elle générerait une erreur de compilation :

```go
10 = 20
```