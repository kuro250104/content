La programmation Go fournit un cadre de gestion des erreurs assez simple avec une interface d'erreur intégrée de type déclaration suivante :

```go
type error interface {
   Error() string
}
```

Les fonctions renvoient normalement une erreur comme dernière valeur de retour. Utilisez ```errors.New``` pour construire un message d'erreur de base, comme suit :

```go
func Sqrt(value float64)(float64, error) {
    if(value < 0){
        return 0, errors.New("Math: negative number passed to Sqrt")
    }
    return math.Sqrt(value), nil
}
```

Utilisez la valeur de retour et le message d'erreur.

```go
result, err:= Sqrt(-1)

if err != nil {
    fmt.Println(err)
}
```

## Exemple

```go
package main

import "errors"
import "fmt"
import "math"

func Sqrt(value float64)(float64, error) {
    if(value < 0){
        return 0, errors.New("Math: negative number passed to Sqrt")
    }
    return math.Sqrt(value), nil
}
func main() {
    result, err:= Sqrt(-1)

    if err != nil {
        fmt.Println(err)
    } else {
        fmt.Println(result)
    }
    
    result, err = Sqrt(9)

    if err != nil {
        fmt.Println(err)
    } else {
        fmt.Println(result)
    }
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
Math: negative number passed to Sqrt
3
```