Un scope dans toute programmation est une région du programme où une variable définie peut exister et au-delà de laquelle la variable ne peut être accédée. Il y a trois endroits où les variables peuvent être déclarées en langage de programmation Go :

- À l'intérieur d'une fonction ou d'un bloc (variables **locales**)
- En dehors de toutes les fonctions (variables **globales**)
- Dans la définition des paramètres de la fonction (paramètres **formels**).

Voyons ce que sont les variables **locales** et **globales** et ce que sont les paramètres **formels**.

## Variables locales

Les variables qui sont déclarées à l'intérieur d'une fonction ou d'un bloc sont appelées variables locales. Elles ne peuvent être utilisées que par les instructions qui se trouvent dans cette fonction ou ce bloc de code. Les variables locales ne sont pas connues des fonctions extérieures à la leur. L'exemple suivant utilise des variables locales. Ici, toutes les variables a, b et c sont locales à la fonction ```main()```.

```go
package main

import "fmt"

func main() {
    /* local variable declaration */
    var a, b, c int 

    /* actual initialization */
    a = 10
    b = 20
    c = a + b

    fmt.Printf ("value of a = %d, b = %d and c = %d\n", a, b, c)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
value of a = 10, b = 20 and c = 30
```

## Variables globales

Les variables globales sont définies en dehors d'une fonction, généralement en haut du programme. Les variables globales conservent leur valeur pendant toute la durée de vie du programme et on peut y accéder dans n'importe quelle fonction définie pour le programme.

Toute fonction peut accéder à une variable globale. En d'autres termes, une variable globale peut être utilisée dans tout le programme après sa déclaration. L'exemple suivant utilise à la fois des variables globales et locales :

```go
package main

import "fmt"

/* global variable declaration */
var g int

func main() {
    /* local variable declaration */
    var a, b int

    /* actual initialization */
    a = 10
    b = 20
    g = a + b

    fmt.Printf("value of a = %d, b = %d and g = %d\n", a, b, g)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
value of a = 10, b = 20 and g = 30
```

Un programme peut avoir le même nom pour les variables locales et globales mais la valeur de la variable locale à l'intérieur d'une fonction a la priorité. Par exemple :

```go
package main

import "fmt"

/* global variable declaration */
var g int = 20

func main() {
    /* local variable declaration */
    var g int = 10

    fmt.Printf ("value of g = %d\n",  g)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
value of g = 10
```

## Paramètres formels

Les paramètres formels sont traités comme des variables locales dans cette fonction et ils ont la préférence sur les variables globales. Par exemple :

```go
package main

import "fmt"

/* global variable declaration */
var a int = 20;

func main() {
    /* local variable declaration in main function */
    var a int = 10
    var b int = 20
    var c int = 0

    fmt.Printf("value of a in main() = %d\n",  a);
    c = sum( a, b);
    fmt.Printf("value of c in main() = %d\n",  c);
}
/* function to add two integers */
func sum(a, b int) int {
    fmt.Printf("value of a in sum() = %d\n",  a);
    fmt.Printf("value of b in sum() = %d\n",  b);

    return a + b;
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
value of a in main() = 10
value of a in sum() = 10
value of b in sum() = 20
value of c in main() = 30
```

## Initialisation des variables locales et globales

Les variables locales et globales sont initialisées à leur valeur par défaut, qui est 0, tandis que les pointeurs sont initialisés à nil.

| **Type de données** | **Valeur initiale par défaut** |
| --- | --- |
| int | 0 |
| float32 | 0 |
| pointer | nil |