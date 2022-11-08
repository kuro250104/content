Go Slice est une abstraction sur Go Array. Go Array vous permet de définir des variables qui peuvent contenir plusieurs éléments de données du même type, mais il ne fournit pas de méthode intégrée pour augmenter sa taille dynamiquement ou obtenir un sous-réseau qui lui est propre. Les tranches permettent de surmonter cette limitation. Il fournit de nombreuses fonctions utilitaires nécessaires à Array et est largement utilisé dans la programmation Go.

## Définition d'une tranche

Pour définir une tranche, vous pouvez la déclarer comme un tableau sans spécifier sa taille. Vous pouvez également utiliser la fonction ```make``` pour créer une tranche.

```go
var numbers []int /* a slice of unspecified size */
/* numbers == []int{0,0,0,0,0}*/
numbers = make([]int,5,5) /* a slice of length 5 and capacity 5*/
```

## Fonctions len() et cap()

Un slice est une abstraction sur les tableaux. Elle utilise en fait les tableaux comme structure sous-jacente. La fonction ```len()``` renvoie les éléments présents dans la tranche tandis que la fonction ```cap()``` renvoie la capacité de la tranche (c'est-à-dire le nombre d'éléments qu'elle peut accueillir). L'exemple suivant explique l'utilisation d'une tranche.

```go
package main

import "fmt"

func main() {
    var numbers = make([]int,3,5)
    printSlice(numbers)
}
func printSlice(x []int){
    fmt.Printf("len=%d cap=%d slice=%v\n",len(x),cap(x),x)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
len = 3 cap = 5 slice = [0 0 0]
```

## Tranche de Nil

Si une tranche est déclarée sans entrées, alors par défaut, elle est initialisée comme nil. Sa longueur et sa capacité sont nulles. Par exemple :

```go
package main

import "fmt"

func main() {
    var numbers []int
    printSlice(numbers)
    
    if(numbers == nil){
        fmt.Printf("slice is nil")
    }
}
func printSlice(x []int){
    fmt.Printf("len = %d cap = %d slice = %v\n", len(x), cap(x),x)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
len = 0 cap = 0 slice = []
slice is nil
```

## Sous-tranchement

La tranche permet de spécifier la limite inférieure et la limite supérieure pour obtenir la sous tranche de celle-ci en utilisant ```[lower-bound:upper-bound]```. Par exemple :

```go
package main

import "fmt"

func main() {
    /* create a slice */
    numbers := []int{0,1,2,3,4,5,6,7,8}   
    printSlice(numbers)
    
    /* print the original slice */
    fmt.Println("numbers ==", numbers)
    
    /* print the sub slice starting from index 1(included) to index 4(excluded)*/
    fmt.Println("numbers[1:4] ==", numbers[1:4])
    
    /* missing lower bound implies 0*/
    fmt.Println("numbers[:3] ==", numbers[:3])
    
    /* missing upper bound implies len(s)*/
    fmt.Println("numbers[4:] ==", numbers[4:])
    
    numbers1 := make([]int,0,5)
    printSlice(numbers1)
    
    /* print the sub slice starting from index 0(included) to index 2(excluded) */
    number2 := numbers[:2]
    printSlice(number2)
    
    /* print the sub slice starting from index 2(included) to index 5(excluded) */
    number3 := numbers[2:5]
    printSlice(number3)
   
}
func printSlice(x []int){
    fmt.Printf("len = %d cap = %d slice = %v\n", len(x), cap(x),x)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
len = 9 cap = 9 slice = [0 1 2 3 4 5 6 7 8]
numbers == [0 1 2 3 4 5 6 7 8]
numbers[1:4] == [1 2 3]
numbers[:3] == [0 1 2]
numbers[4:] == [4 5 6 7 8]
len = 0 cap = 5 slice = []
len = 2 cap = 9  slice = [0 1]
len = 3 cap = 7 slice = [2 3 4]
```

## Fonctions append() et copy()

On peut augmenter la capacité d'une tranche en utilisant la fonction ```append()```. En utilisant la fonction ```copy()```, le contenu d'une tranche source est copié sur une tranche de destination. Par exemple :

```go
package main

import "fmt"

func main() {
    var numbers []int
    printSlice(numbers)
    
    /* append allows nil slice */
    numbers = append(numbers, 0)
    printSlice(numbers)
    
    /* add one element to slice*/
    numbers = append(numbers, 1)
    printSlice(numbers)
    
    /* add more than one element at a time*/
    numbers = append(numbers, 2,3,4)
    printSlice(numbers)
    
    /* create a slice numbers1 with double the capacity of earlier slice*/
    numbers1 := make([]int, len(numbers), (cap(numbers))*2)
    
    /* copy content of numbers to numbers1 */
    copy(numbers1,numbers)
    printSlice(numbers1)   
}
func printSlice(x []int){
    fmt.Printf("len=%d cap=%d slice=%v\n",len(x),cap(x),x)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
len = 0 cap = 0 slice = []
len = 1 cap = 2 slice = [0]
len = 2 cap = 2 slice = [0 1]
len = 5 cap = 8 slice = [0 1 2 3 4]
len = 5 cap = 16 slice = [0 1 2 3 4]
```