La conversion de type est un moyen de convertir une variable d'un type de données à un autre type de données. Par exemple, si vous souhaitez stocker une valeur longue dans un simple entier, vous pouvez convertir le type long en int. Vous pouvez convertir des valeurs d'un type à un autre en utilisant l'opérateur cast. Sa syntaxe est la suivante :

```go
type_name(expression)
```

## Exemple

Prenons l'exemple suivant où l'opérateur cast fait en sorte que la division d'une variable entière par une autre soit effectuée comme une opération sur un nombre flottant.

```go
package main

import "fmt"

func main() {
    var sum int = 17
    var count int = 5
    var mean float32
    
    mean = float32(sum)/float32(count)
    fmt.Printf("Value of mean : %f\n",mean)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
Value of mean : 3.400000
```