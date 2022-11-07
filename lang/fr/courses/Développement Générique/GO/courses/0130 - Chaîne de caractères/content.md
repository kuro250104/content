Les chaînes de caractères, qui sont largement utilisées en programmation Go, sont une tranche d'octets en lecture seule. Dans le langage de programmation Go, les chaînes de caractères sont des **tranches**. La plateforme Go fournit diverses bibliothèques pour manipuler les chaînes de caractères.

- unicode
- regexp
- chaînes de caractères

## Création de chaînes de caractères

La manière la plus directe de créer une chaîne est d'écrire :

```go
var greeting = "Hello world!"
```

Chaque fois qu'il rencontre un littéral de chaîne de caractères dans votre code, le compilateur crée un objet chaîne de caractères avec sa valeur ; dans ce cas, "Hello world !".

Une chaîne littérale contient une séquence UTF-8 valide appelée runes. Une chaîne contient des octets arbitraires.

```go
package main

import "fmt"

func main() {
    var greeting =  "Hello world!"
    
    fmt.Printf("normal string: ")
    fmt.Printf("%s", greeting)
    fmt.Printf("\n")
    fmt.Printf("hex bytes: ")
    
    for i := 0; i < len(greeting); i++ {
        fmt.Printf("%x ", greeting[i])
    }
    
    fmt.Printf("\n")
    const sampleText = "\xbd\xb2\x3d\xbc\x20\xe2\x8c\x98" 
    
    /*q flag escapes unprintable characters, with + flag it escapses non-ascii 
    characters as well to make output unambigous */
    fmt.Printf("quoted string: ")
    fmt.Printf("%+q", sampleText)
    fmt.Printf("\n")  
}
```

Cela donnerait le résultat suivant :

```bash
normal string: Hello world!
hex bytes: 48 65 6c 6c 6f 20 77 6f 72 6c 64 21 
quoted string: "\xbd\xb2=\xbc \u2318"
```

__Remarque__ : Le littéral de chaîne est immuable, c'est-à-dire qu'une fois créé, un littéral de chaîne ne peut pas être modifié.

## Longueur de la chaîne

La méthode ```len(str)``` renvoie le nombre d'octets contenus dans la chaîne littérale.

```go
package main

import "fmt"

func main() {
    var greeting =  "Hello world!"

    fmt.Printf("String Length is: ")
    fmt.Println(len(greeting))  
}
```

Cela donnerait le résultat suivant :

```bash
String Length is : 12
```

## Concaténation de chaînes de caractères

Le paquet strings comprend une méthode join pour concaténer plusieurs chaînes de caractères :

```go
strings.Join(sample, " ")
```

Join concatène les éléments d'un tableau pour créer une seule chaîne. Le deuxième paramètre est le séparateur qui est placé entre les éléments du tableau.

Examinons l'exemple suivant :

```go
package main

import ("fmt" "math" )"fmt" "strings")

func main() {
    greetings :=  []string{"Hello","world!"}   
    fmt.Println(strings.Join(greetings, " "))
}
```

Cela donnerait le résultat suivant :

```bash
Hello world!
```