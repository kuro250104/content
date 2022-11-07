Le mot clé **range** est utilisé dans une boucle for pour itérer sur les éléments d'un tableau, d'une tranche, d'un canal ou d'une carte. Avec les tableaux et les tranches, il renvoie l'index de l'élément en tant qu'entier. Avec les cartes, il renvoie la clé de la paire clé-valeur suivante. **Range** renvoie soit une valeur, soit deux. Si une seule valeur est utilisée à gauche d'une expression de plage, il s'agit de la première valeur du tableau suivant.

| **expression Range** | **1ère valeur** | **2ème valeur (Optionnelle)** |
| --- | --- | --- |
| Array ou slice a [n]E | index i int | a[i] E |
| String s de type string | index i int | rune int |
| map m map[K]V | key k K | valeur m[k] V |
| channel c chan E | élément e E | none |

## Exemple

```go
package main

import "fmt"

func main() {
    /* create a slice */
    numbers := []int{0,1,2,3,4,5,6,7,8} 
    
    /* print the numbers */
    for i:= range numbers {
        fmt.Println("Slice item",i,"is",numbers[i])
    }
    
    /* create a map*/
    countryCapitalMap := map[string] string {"France":"Paris","Italy":"Rome","Japan":"Tokyo"}
    
    /* print map using keys*/
    for country := range countryCapitalMap {
        fmt.Println("Capital of",country,"is",countryCapitalMap[country])
    }
    
    /* print map using key-value*/
    for country,capital := range countryCapitalMap {
        fmt.Println("Capital of",country,"is",capital)
    }
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant : 

```bash
Slice item 0 is 0
Slice item 1 is 1
Slice item 2 is 2
Slice item 3 is 3
Slice item 4 is 4
Slice item 5 is 5
Slice item 6 is 6
Slice item 7 is 7
Slice item 8 is 8
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
```