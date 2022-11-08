Les tableaux de Go vous permettent de définir des variables qui peuvent contenir plusieurs éléments de données de même nature. La **structure** est un autre type de données défini par l'utilisateur disponible dans la programmation Go, qui vous permet de combiner des éléments de données de différents types.

Les structures sont utilisées pour représenter un enregistrement. Supposons que vous vouliez garder la trace des livres d'une bibliothèque. Vous voudrez peut-être suivre les attributs suivants pour chaque livre :

- Titre
- Auteur
- Sujet
- ID du livre

Dans un tel scénario, les structures sont très utiles.

## Définir une structure

Pour définir une structure, vous devez utiliser les instructions **type** et **struct**. L'instruction struct définit un nouveau type de données, avec plusieurs membres pour votre programme. L'instruction type lie un nom au type, qui est struct dans notre cas. Le format de l'instruction struct est le suivant :

```go
type struct_variable_type struct {
    member definition;
    member definition;
    ...
    member definition;
}
```

Une fois qu'un type de structure est défini, il peut être utilisé pour déclarer des variables de ce type en utilisant la syntaxe suivante.

```go
variable_name := structure_variable_type {value1, value2...valuen}
```

## Accès aux membres de la structure

Pour accéder à n'importe quel membre d'une structure, nous utilisons l'**opérateur d'accès aux membres** (.). L'opérateur d'accès aux membres est codé comme un point entre le nom de la variable de structure et le membre de la structure auquel nous souhaitons accéder. Vous utiliserez le mot-clé ```struct``` pour définir des variables de type structure. L'exemple suivant explique comment utiliser une structure.

```go
package main

import "fmt"

type Books struct {
    title string
    author string
    subject string
    book_id int
}
func main() {
    var Book1 Books    /* Declare Book1 of type Book */
    var Book2 Books    /* Declare Book2 of type Book */
    
    /* book 1 specification */
    Book1.title = "Go Programming"
    Book1.author = "Mahesh Kumar"
    Book1.subject = "Go Programming Tutorial"
    Book1.book_id = 6495407

    /* book 2 specification */
    Book2.title = "Telecom Billing"
    Book2.author = "Zara Ali"
    Book2.subject = "Telecom Billing Tutorial"
    Book2.book_id = 6495700
    
    /* print Book1 info */
    fmt.Printf( "Book 1 title : %s\n", Book1.title)
    fmt.Printf( "Book 1 author : %s\n", Book1.author)
    fmt.Printf( "Book 1 subject : %s\n", Book1.subject)
    fmt.Printf( "Book 1 book_id : %d\n", Book1.book_id)

    /* print Book2 info */
    fmt.Printf( "Book 2 title : %s\n", Book2.title)
    fmt.Printf( "Book 2 author : %s\n", Book2.author)
    fmt.Printf( "Book 2 subject : %s\n", Book2.subject)
    fmt.Printf( "Book 2 book_id : %d\n", Book2.book_id)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
Book 1 title      : Go Programming
Book 1 author     : Mahesh Kumar
Book 1 subject    : Go Programming Tutorial
Book 1 book_id    : 6495407
Book 2 title      : Telecom Billing
Book 2 author     : Zara Ali
Book 2 subject    : Telecom Billing Tutorial
Book 2 book_id    : 6495700
```

## Structures comme arguments de fonction

Vous pouvez transmettre une structure comme argument de fonction de la même manière que vous transmettez toute autre variable ou pointeur. Vous accédez aux variables de la structure de la même manière que dans l'exemple ci-dessus :

```go
package main

import "fmt"

type Books struct {
    title string
    author string
    subject string
    book_id int
}
func main() {
    var Book1 Books    /* Declare Book1 of type Book */
    var Book2 Books    /* Declare Book2 of type Book */
    
    /* book 1 specification */
    Book1.title = "Go Programming"
    Book1.author = "Mahesh Kumar"
    Book1.subject = "Go Programming Tutorial"
    Book1.book_id = 6495407

    /* book 2 specification */
    Book2.title = "Telecom Billing"
    Book2.author = "Zara Ali"
    Book2.subject = "Telecom Billing Tutorial"
    Book2.book_id = 6495700
    
    /* print Book1 info */
    printBook(Book1)

    /* print Book2 info */
    printBook(Book2)
}
func printBook( book Books ) {
    fmt.Printf( "Book title : %s\n", book.title);
    fmt.Printf( "Book author : %s\n", book.author);
    fmt.Printf( "Book subject : %s\n", book.subject);
    fmt.Printf( "Book book_id : %d\n", book.book_id);
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
Book title     : Go Programming
Book author    : Mahesh Kumar
Book subject   : Go Programming Tutorial
Book book_id   : 6495407
Book title     : Telecom Billing
Book author    : Zara Ali
Book subject   : Telecom Billing Tutorial
Book book_id   : 6495700
```

## Pointeurs vers les structures

Vous pouvez définir des pointeurs vers des structures de la même manière que vous définissez un pointeur vers n'importe quelle autre variable, comme suit :

```go
var struct_pointer *Books
```

Maintenant, vous pouvez stocker l'adresse d'une variable structure dans la variable pointeur définie ci-dessus. Pour trouver l'adresse d'une variable de structure, placez l'opérateur & devant le nom de la structure, comme suit :

```go
struct_pointer = &Book1;
```

Pour accéder aux membres d'une structure en utilisant un pointeur sur cette structure, vous devez utiliser l'opérateur "." comme suit :

```go
struct_pointer.title;
```

Réécrivons l'exemple ci-dessus en utilisant le pointeur de structure :

```go
package main

import "fmt"

type Books struct {
    title string
    author string
    subject string
    book_id int
}
func main() {
    var Book1 Books   /* Declare Book1 of type Book */
    var Book2 Books   /* Declare Book2 of type Book */
    
    /* book 1 specification */
    Book1.title = "Go Programming"
    Book1.author = "Mahesh Kumar"
    Book1.subject = "Go Programming Tutorial"
    Book1.book_id = 6495407

    /* book 2 specification */
    Book2.title = "Telecom Billing"
    Book2.author = "Zara Ali"
    Book2.subject = "Telecom Billing Tutorial"
    Book2.book_id = 6495700
    
    /* print Book1 info */
    printBook(&Book1)

    /* print Book2 info */
    printBook(&Book2)
}
func printBook( book *Books ) {
    fmt.Printf( "Book title : %s\n", book.title);
    fmt.Printf( "Book author : %s\n", book.author);
    fmt.Printf( "Book subject : %s\n", book.subject);
    fmt.Printf( "Book book_id : %d\n", book.book_id);
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
Book title     : Go Programming
Book author    : Mahesh Kumar
Book subject   : Go Programming Tutorial
Book book_id   : 6495407
Book title     : Telecom Billing
Book author    : Zara Ali
Book subject   : Telecom Billing Tutorial
Book book_id   : 6495700
```