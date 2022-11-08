Une fonction est un groupe d'instructions qui, ensemble, exécutent une tâche. Chaque programme Go possède au moins une fonction, qui est main(). Vous pouvez diviser votre code en plusieurs fonctions distinctes. La façon dont vous divisez votre code entre les différentes fonctions vous appartient, mais logiquement, la division devrait être telle que chaque fonction effectue une tâche spécifique.

Une **déclaration** de fonction indique au compilateur le nom de la fonction, le type de retour et les paramètres. Une **définition** de fonction fournit le corps réel de la fonction.

La bibliothèque standard de Go fournit de nombreuses fonctions intégrées que votre programme peut appeler. Par exemple, la fonction ```len()``` prend des arguments de différents types et renvoie la longueur du type. Si une chaîne de caractères lui est passée, la fonction renvoie la longueur de la chaîne en octets. Si un tableau lui est transmis, la fonction renvoie la longueur du tableau.

Les fonctions sont également appelées **méthodes**, **sous-routines** ou **procédures**.

## Définir une fonction

La forme générale d'une définition de fonction dans le langage de programmation Go est la suivante :

```go
func function_name( [parameter list] ) [return_types]
{
    body of the function
}
```

Une définition de fonction dans le langage de programmation Go se compose d'un en-tête de fonction et d'un corps de fonction. Voici toutes les parties d'une fonction :

- **Func** - Il commence la déclaration d'une fonction.
- **Nom de la fonction** - C'est le nom réel de la fonction. Le nom de la fonction et la liste des paramètres constituent ensemble la signature de la fonction.
- **Paramètres** - Un paramètre est comme un espace réservé. Lorsqu'une fonction est invoquée, vous transmettez une valeur au paramètre. Cette valeur est appelée paramètre réel ou argument. La liste des paramètres fait référence au type, à l'ordre et au nombre de paramètres d'une fonction. Les paramètres sont facultatifs, c'est-à-dire qu'une fonction peut ne pas contenir de paramètres.
- **Type de retour** - Une fonction peut retourner une liste de valeurs. Le paramètre return_types est la liste des types de données des valeurs que la fonction renvoie. Certaines fonctions effectuent les opérations souhaitées sans renvoyer de valeur. Dans ce cas, le return_type n'est pas nécessaire.
- **Corps de la fonction** - Il contient un ensemble d'instructions qui définissent ce que fait la fonction.

## Exemple

Le code source suivant présente une fonction appelée max(). Cette fonction prend deux paramètres, num1 et num2, et renvoie le maximum entre les deux.

```go
/* function returning the max between two numbers */
func max(num1, num2 int) int {
    /* local variable declaration */
    result int

    if (num1 > num2) {
        result = num1
    } else {
        result = num2
    }
    return result 
}
```

## Appeler une fonction

Lorsque vous créez une fonction Go, vous donnez une définition de ce que la fonction doit faire. Pour utiliser une fonction, vous devrez appeler cette fonction pour effectuer la tâche définie.

Lorsqu'un programme appelle une fonction, le contrôle du programme est transféré à la fonction appelée. Une fonction appelée exécute une tâche définie et, lorsque son instruction de retour est exécutée ou lorsque son accolade de fin de fonction est atteinte, elle renvoie le contrôle du programme au programme principal.

Pour appeler une fonction, il suffit de lui transmettre les paramètres requis ainsi que son nom. Si la fonction renvoie une valeur, vous pouvez stocker cette valeur. Par exemple :

```go
package main

import "fmt"

func main() {
    /* local variable definition */
    var a int = 100
    var b int = 200
    var ret int

    /* calling a function to get max value */
    ret = max(a, b)

    fmt.Printf( "Max value is : %d\n", ret )
}

/* function returning the max between two numbers */
func max(num1, num2 int) int {
    /* local variable declaration */
    var result int

    if (num1 > num2) {
        result = num1
    } else {
        result = num2
    }
    return result 
}
```

Nous avons conservé la fonction ```max()``` avec la fonction ```main()``` et compilé le code source. En exécutant l'exécutable final, il produirait le résultat suivant :

```go
Max value is : 200
```

## Renvoi de valeurs multiples à partir d'une fonction

Une fonction Go peut renvoyer plusieurs valeurs. Par exemple :

```go
package main

import "fmt"

func swap(x, y string) (string, string) {
    return y, x
}
func main() {
    a, b := swap("Lead", "Micro")
    fmt.Println(a, b)
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
Micro Lead
```

## Arguments de la fonction

Si une fonction doit utiliser des arguments, elle doit déclarer des variables qui acceptent les valeurs des arguments. Ces variables sont appelées les paramètres formels de la fonction.

Les paramètres formels se comportent comme les autres variables locales à l'intérieur de la fonction et sont créés à l'entrée de la fonction et détruits à la sortie.

Lors de l'appel d'une fonction, les arguments peuvent être transmis à la fonction de deux manières différentes :

**Type d'appel et description**

- **Appel par valeur** : Cette méthode copie la valeur réelle d'un argument dans le paramètre formel de la fonction. Dans ce cas, les modifications apportées au paramètre à l'intérieur de la fonction n'ont aucun effet sur l'argument.

- **Appel par référence** : Cette méthode copie l'adresse d'un argument dans le paramètre formel. Dans la fonction, l'adresse est utilisée pour accéder à l'argument réel utilisé dans l'appel. Cela signifie que les modifications apportées au paramètre ont un effet sur l'argument.

Par défaut, Go utilise l'appel par valeur pour passer les arguments. En général, cela signifie que le code à l'intérieur d'une fonction ne peut pas modifier les arguments utilisés pour appeler la fonction. Le programme ci-dessus, en appelant la fonction max(), a utilisé la même méthode.

## Utilisation des fonctions

Une fonction peut être utilisée de la manière suivante :

**Utilisation et description des fonctions**

- **Fonction comme valeur** : Les fonctions peuvent être créées à la volée et peuvent être utilisées comme valeurs.
- **Fermetures de fonctions** : Les fermetures de fonctions sont des fonctions anonymes et peuvent être utilisées dans la programmation dynamique.
- **Méthode** : Les méthodes sont des fonctions spéciales avec un récepteur.