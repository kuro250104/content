Les pointeurs en Go sont faciles et amusants à apprendre. Certaines tâches de programmation en Go sont exécutées plus facilement avec des pointeurs, et d'autres tâches, comme l'appel par référence, ne peuvent être exécutées sans utiliser de pointeurs. Il devient donc nécessaire d'apprendre les pointeurs pour devenir un parfait programmeur Go.

Comme vous le savez, chaque variable est un emplacement mémoire et chaque emplacement mémoire à son adresse définie, à laquelle on peut accéder en utilisant l'opérateur esperluette (&), qui désigne une adresse en mémoire. Considérez l'exemple suivant, qui imprimera l'adresse des variables définies :

```go
package main

import "fmt"

func main() {
    var a int = 10   
    fmt.Printf("Address of a variable: %x\n", &a  )
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
Address of a variable: 10328000
```

Vous avez donc compris ce qu'est une adresse mémoire et comment y accéder. Voyons maintenant ce que sont les pointeurs.

## Que sont les pointeurs ?

Un **pointeur** est une variable dont la valeur est l'adresse d'une autre variable, c'est-à-dire l'adresse directe de l'emplacement mémoire. Comme toute variable ou constante, vous devez déclarer un pointeur avant de pouvoir l'utiliser pour stocker une adresse de variable. La forme générale d'une déclaration de variable de type pointeur est :

```go
var var_name *var-type
```

Ici, **type** est le type de base du pointeur ; il doit être un type de données C valide et **var-name** est le nom de la variable du pointeur. L'astérisque * utilisé pour déclarer un pointeur est le même astérisque que celui utilisé pour la multiplication. Toutefois, dans cette déclaration, l'astérisque est utilisé pour désigner une variable comme un pointeur. Voici les déclarations de pointeurs valides :

```go
var ip *int        /* pointer to an integer */
var fp *float32    /* pointer to a float */
```

Le type de données réel de la valeur de tous les pointeurs, qu'il s'agisse d'un nombre entier, d'un nombre flottant ou autre, est le même : un long nombre hexadécimal qui représente une adresse mémoire. La seule différence entre les pointeurs de différents types de données est le type de données de la variable ou de la constante vers laquelle le pointeur pointe.

## Comment utiliser les pointeurs ?

Il existe quelques opérations importantes, que nous effectuons fréquemment avec les pointeurs : (a) nous définissons des variables pointeurs, (b) nous assignons l'adresse d'une variable à un pointeur, et (c) nous accédons à la valeur à l'adresse stockée dans la variable pointeur.

Toutes ces opérations sont effectuées à l'aide de l'opérateur unaire * qui renvoie la valeur de la variable située à l'adresse spécifiée par son opérande. L'exemple suivant démontre comment effectuer ces opérations :

```go
package main

import "fmt"

func main() {
    var a int = 20   /* actual variable declaration */
    var ip *int      /* pointer variable declaration */

    ip = &a  /* store address of a in pointer variable*/

    fmt.Printf("Address of a variable: %x\n", &a  )

    /* address stored in pointer variable */
    fmt.Printf("Address stored in ip variable: %x\n", ip )

    /* access the value using the pointer */
    fmt.Printf("Value of *ip variable: %d\n", *ip )
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
Address of var variable: 10328000
Address stored in ip variable: 10328000
Value of *ip variable: 20
```

## Pointeurs nuls en Go

Le compilateur Go assigne une valeur Nil à une variable pointeur dans le cas où vous n'avez pas l'adresse exacte à assigner. Ceci est fait au moment de la déclaration de la variable. Un pointeur qui se voit attribuer la valeur Nil est appelé pointeur **Nil**.

Le pointeur nul est une constante avec une valeur de zéro définie dans plusieurs bibliothèques standard. Considérons le programme suivant :

```go
package main

import "fmt"

func main() {
    var  ptr *int

    fmt.Printf("The value of ptr is : %x\n", ptr  )
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
The value of ptr is 0
```

Sur la plupart des systèmes d'exploitation, les programmes ne sont pas autorisés à accéder à la mémoire à l'adresse 0 car cette mémoire est réservée par le système d'exploitation. Cependant, l'adresse mémoire 0 a une signification particulière ; elle signale que le pointeur n'est pas destiné à pointer vers un emplacement mémoire accessible. Mais par convention, si un pointeur contient la valeur nil (zéro), on suppose qu'il ne pointe sur rien.

Pour vérifier l'existence d'un pointeur nul, vous pouvez utiliser une instruction if comme suit :

```go
if(ptr != nil)     /* succeeds if p is not nil */
if(ptr == nil)    /* succeeds if p is null */
```

## Les pointeurs Go en détail

Les pointeurs ont des concepts nombreux mais simples et ils sont très importants pour la programmation en Go. Les concepts de pointeurs suivants devraient être clairs pour un programmeur de Go...

**Concept et description**

- **Tableau de pointeurs** - Vous pouvez définir des tableaux pour contenir un certain nombre de pointeurs.
- **Pointeur sur pointeur** - Go vous permet d'avoir un pointeur sur un pointeur et ainsi de suite.
- **Passer des pointeurs aux fonctions en Go** - Passer un argument par référence ou par adresse permet à l'argument passé d'être modifié dans la fonction appelante par la fonction appelée.