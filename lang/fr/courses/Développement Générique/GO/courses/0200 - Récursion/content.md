La récursion est le processus qui consiste à répéter des éléments de manière autosimilaire. Le même concept s'applique également aux langages de programmation. Si un programme permet d'appeler une fonction à l'intérieur de la même fonction, on parle alors d'appel de fonction récursive. Regardez l'exemple suivant :

```go
func recursion() {
    recursion() /* function calls itself */
}
func main() {
    recursion()
}
```

Le langage de programmation Go supporte la récursion. C'est-à-dire qu'il permet à une fonction de s'appeler elle-même. Mais lorsqu'ils utilisent la récursion, les programmeurs doivent faire attention à définir une condition de sortie de la fonction, sinon elle deviendra une boucle infinie.

## Exemples de récursion en Go

Les fonctions récursives sont très utiles pour résoudre de nombreux problèmes mathématiques tels que le calcul de la factorielle d'un nombre, la génération d'une série de Fibonacci, etc.

### Exemple 1 : Calcul du factoriel en utilisant la récursion dans Go

L'exemple suivant calcule la factorielle d'un nombre donné à l'aide d'une fonction récursive :

```go
package main

import "fmt"

func factorial(i int)int {
    if(i <= 1) {
        return 1
    }
    return i * factorial(i - 1)
}
func main() { 
    var i int = 15
    fmt.Printf("Factorial of %d is %d", i, factorial(i))
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
Factorial of 15 is 1307674368000
```

### Exemple 2 : Séries de Fibonacci en utilisant la récursion dans Go

L'exemple suivant montre comment générer une série de Fibonacci d'un nombre donné à l'aide d'une fonction récursive :

```go
package main

import "fmt"

func fibonaci(i int) (ret int) {
    if i == 0 {
        return 0
    }
    if i == 1 {
        return 1
    }
    return fibonaci(i-1) + fibonaci(i-2)
}
func main() {
    var i int
    for i = 0; i < 10; i++ {
        fmt.Printf("%d ", fibonaci(i))
    }
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
0 1 1 2 3 5 8 13 21 34 
```