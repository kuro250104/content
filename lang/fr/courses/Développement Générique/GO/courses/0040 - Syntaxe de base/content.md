Nous avons discuté de la structure de base d'un programme Go dans le chapitre précédent. Il sera maintenant facile de comprendre les autres éléments de base du langage de programmation Go.

## Jetons en Go

Un programme Go est constitué de divers jetons. Un jeton est soit un mot-clé, un identifiant, une constante, une chaîne littérale, ou un symbole. Par exemple, l'instruction Go suivante est composée de six jetons -

```go
fmt.Println("Hello, World!")
```

Les jetons individuels sont :

```go
fmt
.
Println
(
    "Hello, World!"
)
```

## Séparateur de ligne

Dans un programme Go, la touche de séparation de ligne est un terminateur d'instruction. En d'autres termes, les instructions individuelles n'ont pas besoin d'un séparateur spécial comme " ;" en C. Le compilateur Go place en interne " ;" comme terminateur d'instruction pour indiquer la fin d'une entité logique.

Par exemple, jetez un coup d'oeil aux déclarations suivantes :

```go
fmt.Println("Hello, World!")
fmt.Println("I am in Go Programming World!")
```

## Commentaires

Les commentaires sont comme des textes d'aide dans votre programme Go et ils sont ignorés par le compilateur. Ils commencent par ```/*``` et se terminent par les caractères ```*/```, comme indiqué ci-dessous.

```go
/* my first program in Go */
```

Il n'est pas possible d'avoir des commentaires à l'intérieur d'un autre commentaire et ils ne peuvent pas se trouver à l'intérieur d'une chaîne de caractères ou de caractères littéraux.

## Identifiants

Un identifiant Go est un nom utilisé pour identifier une variable, une fonction ou tout autre élément défini par l'utilisateur. Un identifiant commence par une lettre de A à Z ou de a à z ou un trait de soulignement _ suivi de zéro ou plus lettres, traits de soulignement, et chiffres (0 à 9).

```go
identificateur = lettre { lettre | unicode_digit }.
```

Go n'autorise pas les caractères de ponctuation tels que @, $ et % dans les identifiants. Le Go est un langage de programmation **case-sensitive**. Ainsi, Manpower et manpower sont deux identifiants différents en Go. Voici quelques exemples d'identifiants acceptables :

```bash
mahesh      kumar   abc   move_name   a_123
myname50   _temp    j      a23b9      retVal
```

## Mots clés

La liste suivante indique les mots réservés en Go. Ces mots réservés ne peuvent pas être utilisés comme noms de constantes ou de variables ou tout autre identifiant.

- break
- default
- func
- interface
- select
- case
- defer
- Go
- map
- Struct
- chan
- else
- Goto
- package
- Switch
- const
- fallthrough
- if
- range
- Type
- continue
- for
- import
- return
- Var

## Les espaces blancs dans Go

L'espace blanc est le terme utilisé en Go pour décrire les blancs, les tabulations, les caractères de nouvelle ligne et les commentaires. Une ligne ne contenant que des espaces blancs, avec éventuellement un commentaire, est appelée ligne blanche, et le compilateur Go l'ignore totalement.

Les espaces blancs séparent une partie d'une instruction d'une autre et permettent au compilateur d'identifier où un élément d'une instruction, tel que int, se termine et où l'élément suivant commence. Par conséquent, dans l'instruction suivante :

```go
var age int;
```

Il doit y avoir au moins un caractère d'espacement (généralement un espace) entre int et age pour que le compilateur puisse les distinguer. D'autre part, dans l'instruction suivante :

```go
fruit = apples + oranges;   // get the total fruit
```

Aucun caractère d'espacement n'est nécessaire entre fruit et =, ou entre = et pomme, bien que vous soyez libre d'en inclure si vous le souhaitez pour des raisons de lisibilité.