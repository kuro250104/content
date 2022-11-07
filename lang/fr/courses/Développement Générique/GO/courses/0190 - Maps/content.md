Go fournit un autre type de données important appelé **map** qui fait correspondre des clés uniques à des valeurs. Une clé est un objet que vous utilisez pour récupérer une valeur à une date ultérieure. Avec une clé et une valeur, vous pouvez stocker la valeur dans un objet Map. Une fois la valeur stockée, vous pouvez la récupérer en utilisant sa clé.

## Définir une carte

Vous devez utiliser la fonction **make** pour créer une map.

```go
/* declare a variable, by default map will be nil*/
var map_variable map[key_data_type]value_data_type

/* define the map as nil map can not be assigned any value*/
map_variable = make(map[key_data_type]value_data_type)
```

## Exemple

L'exemple suivant illustre comment créer et utiliser une map :

```go
package main

import "fmt"

func main() {
    var countryCapitalMap map[string]string
    /* create a map*/
    countryCapitalMap = make(map[string]string)
    
    /* insert key-value pairs in the map*/
    countryCapitalMap["France"] = "Paris"
    countryCapitalMap["Italy"] = "Rome"
    countryCapitalMap["Japan"] = "Tokyo"
    countryCapitalMap["India"] = "New Delhi"
    
    /* print map using keys*/
    for country := range countryCapitalMap {
        fmt.Println("Capital of",country,"is",countryCapitalMap[country])
    }
    
    /* test if entry is present in the map or not*/
    capital, ok := countryCapitalMap["United States"]
    
    /* if ok is true, entry is present otherwise entry is absent*/
    if(ok){
        fmt.Println("Capital of United States is", capital)  
    } else {
        fmt.Println("Capital of United States is not present") 
    }
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
Capital of India is New Delhi
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of United States is not present
```

## Fonction delete()

La fonction delete() est utilisée pour supprimer une entrée d'une carte. Elle nécessite la carte et la clé correspondante qui doit être supprimée. Par exemple :

```go
package main

import "fmt"

func main() {   
    /* create a map*/
    countryCapitalMap := map[string] string {"France":"Paris","Italy":"Rome","Japan":"Tokyo","India":"New Delhi"}
    
    fmt.Println("Original map")   
    
    /* print map */
    for country := range countryCapitalMap {
        fmt.Println("Capital of",country,"is",countryCapitalMap[country])
    }
    
    /* delete an entry */
    delete(countryCapitalMap,"France");
    fmt.Println("Entry for France is deleted")  
    
    fmt.Println("Updated map")   
    
    /* print map */
    for country := range countryCapitalMap {
        fmt.Println("Capital of",country,"is",countryCapitalMap[country])
    }
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
Original Map
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of India is New Delhi
Entry for France is deleted
Updated Map
Capital of India is New Delhi
Capital of Italy is Rome
Capital of Japan is Tokyo
```