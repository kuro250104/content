Les constantes font référence à des valeurs fixes que le programme ne peut pas modifier pendant son exécution. Ces valeurs fixes sont également appelées **littéraux**.

Les constantes peuvent être de n'importe quel type de données de base, comme une constante entière, une constante flottante, une constante de caractère ou un littéral de chaîne de caractères. Il existe également des constantes d'énumération.

Les constantes sont traitées comme des variables ordinaires, sauf que leurs valeurs ne peuvent pas être modifiées après leur définition.

## Littéraux entiers

Un littéral entier peut être une constante décimale, octale ou hexadécimale. Un préfixe spécifie la base ou le radixe : 0x ou 0X pour l'hexadécimal, 0 pour l'octal, et rien pour le décimal.

Un littéral entier peut également avoir un suffixe qui est une combinaison de U et L, pour unsigned et long, respectivement. Le suffixe peut être en majuscules ou en minuscules et peut être dans n'importe quel ordre.

Voici quelques exemples de littéraux de nombres entiers :

```go
212         /* Legal */
215u        /* Legal */
0xFeeL      /* Legal */
078         /* Illegal: 8 is not an octal digit */
032UU       /* Illegal: cannot repeat a suffix */
```

Voici d'autres exemples de différents types de littéraux de type Integer :

```go
85         /* decimal */
0213       /* octal */
0x4b       /* hexadecimal */
30         /* int */
30u        /* unsigned int */
30l        /* long */
30ul       /* unsigned long */
```

## Littéraux en virgule flottante

Un littéral à virgule flottante possède une partie entière, une virgule décimale, une partie fractionnaire et une partie exponentielle. Vous pouvez représenter les littéraux à virgule flottante soit sous forme décimale, soit sous forme exponentielle.

Lors de la représentation sous forme décimale, vous devez inclure le point décimal, l'exposant ou les deux. Lors de la représentation sous forme exponentielle, vous devez inclure la partie entière, la partie fractionnaire ou les deux. L'exposant signé est introduit par e ou E.

Voici quelques exemples de littéraux à virgule flottante :

```go
3.14159       /* Legal */
314159E-5L    /* Legal */
510E          /* Illegal: incomplete exponent */
210f          /* Illegal: no decimal or exponent */
.e55          /* Illegal: missing integer or fraction */
```

## Séquence d'évasion

Lorsque certains caractères sont précédés d'une barre oblique inverse, ils ont une signification particulière dans Go. Il s'agit des codes de séquence d'échappement qui sont utilisés pour représenter une nouvelle ligne (\n), une tabulation (\t), un retour arrière, etc. Vous trouverez ici une liste de certains de ces codes de séquence d'échappement :

| **Caractère d'échappement** | **Signification** |
| --- | --- |
| ``` \\ ``` | caractère ``` \ ``` |
| ``` \' ``` | caractère ``` ' ``` |
| ``` \" ``` | caractère ``` " ``` |
| ``` \? ``` | caractère ``` ? ``` |
| ``` \a ``` | Alerte ou Sonnerie |
| ``` \b ``` | Retour en arrière |
| ``` \f ``` | Alimentation en formulaires |
| ``` \n ``` | Nouvelle ligne |
| ``` \r ``` | Retour chariot |
| ``` \t ``` | Tabulation horizontale |
| ``` \v ``` | Tabulation verticale |
| ``` \ooo ``` | Nombre octal de un à trois chiffres |
| ``` \xhh . . . ``` | Nombre hexadécimal d'un ou plusieurs chiffres |

L'exemple suivant montre comment utiliser ```\t``` dans un programme :

```go
package main

import "fmt"

func main() {
    fmt.Printf("Hello\tWorld!")
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
Hello    World!
```

## Les littéraux de chaîne en Go

Les chaînes de caractères ou les constantes sont placées entre des guillemets doubles "". Une chaîne de caractères contient des caractères similaires aux caractères littéraux : caractères ordinaires, séquences d'échappement et caractères universels.

Vous pouvez diviser une longue ligne en plusieurs lignes en utilisant des littéraux de chaîne et en les séparant par des espaces.

Voici quelques exemples de littéraux de chaîne. Les trois formes sont des chaînes de caractères identiques.

```go
"hello, dear"

"hello, \

dear"

"hello, " "d" "ear"
```

## Le mot-clé const

Vous pouvez utiliser le préfixe **const** pour déclarer des constantes avec un type spécifique comme suit :

```go
const variable type = value;
```

L'exemple suivant montre comment utiliser le mot-clé **const** :

```go
package main

import "fmt"

func main() {
    const LENGTH int = 10
    const WIDTH int = 5   
    var area int

    area = LENGTH * WIDTH
    fmt.Printf("value of area : %d", area)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```go
value of area : 50
```

Notez que c'est une bonne pratique de programmation de définir les constantes en MAJUSCULES.