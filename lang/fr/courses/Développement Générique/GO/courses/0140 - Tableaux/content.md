Le langage de programmation Go fournit une structure de données appelée tableau, qui permet de stocker une collection séquentielle de taille fixe d'éléments du même type. Un tableau est utilisé pour stocker une collection de données, mais il est souvent plus utile de considérer un tableau comme une collection de variables du même type.

Au lieu de déclarer des variables individuelles, telles que nombre0, nombre1, ..., et nombre99, vous déclarez une variable de tableau telle que nombres et utilisez nombres[0], nombres[1], et ..., nombres[99] pour représenter les variables individuelles. On accède à un élément spécifique d'un tableau par un index.

Tous les tableaux sont constitués d'emplacements mémoire contigus. L'adresse la plus basse correspond au premier élément et l'adresse la plus haute au dernier élément.

![Représentation des adresses dans un tableau](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/GO/courses/0140%20-%20Tableaux/images/image2.jpg)

## Déclarer des tableaux

Pour déclarer un tableau en Go, le programmeur spécifie le type d'éléments et le nombre d'éléments requis par un tableau comme suit :

```go
var variable_name [SIZE] variable_type
```

C'est ce qu'on appelle un *tableau unidimensionnel*. L'**arraySize** doit être une constante entière supérieure à zéro et le **type** peut être tout type de données Go valide. Par exemple, pour déclarer un tableau de 10 éléments appelé **balance** de type float32, utilisez l'instruction :

```go
var balance [10] float32
```

Ici, **balance** est un tableau variable qui peut contenir jusqu'à 10 nombres flottants.

## Initialisation des tableaux

Vous pouvez initialiser les tableaux dans Go soit un par un, soit en utilisant une seule instruction comme suit :

```go
var balance = [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

Le nombre de valeurs entre accolades { } ne peut pas être supérieur au nombre d'éléments que nous déclarons pour le tableau entre crochets [ ].

Si vous omettez la taille du tableau, un tableau juste assez grand pour contenir l'initialisation est créé. Par conséquent, si vous écrivez :

```go
var balance = []float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

Vous allez créer exactement le même tableau que dans l'exemple précédent. L'exemple suivant permet d'assigner un seul élément du tableau :

```go
balance[4] = 50.0
```

L'instruction ci-dessus attribue à l'élément numéro 5 du tableau une valeur de 50.0. Tous les tableaux ont 0 comme indice de leur premier élément qui est également appelé indice de base et le dernier indice d'un tableau sera la taille totale du tableau moins 1. Voici la représentation graphique du même tableau que celui dont nous avons parlé plus haut.

![représentation graphique du tableau mentionné](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/GO/courses/0140%20-%20Tableaux/images/image1.jpg)

## Accès aux éléments d'un tableau

On accède à un élément en indexant le nom du tableau. Pour ce faire, on place l'indice de l'élément entre crochets après le nom du tableau. Par exemple :

```go
float32 salary = balance[9]
```

L'instruction ci-dessus prendra le 10ème élément du tableau et assignera la valeur à la variable salaire. Voici un exemple qui utilise les trois concepts mentionnés ci-dessus, à savoir la déclaration, l'affectation et l'accès aux tableaux : 

```go
package main

import "fmt"

func main() {
    var n [10]int /* n is an array of 10 integers */
    var i,j int

    /* initialize elements of array n to 0 */         
    for i = 0; i < 10; i++ {
        n[i] = i + 100 /* set element at location i to i + 100 */
    }
    
    /* output each array element's value */
    for j = 0; j < 10; j++ {
        fmt.Printf("Element[%d] = %d\n", j, n[j] )
    }
}
```

Lorsque le code ci-dessus est compilé et exécuté, il produit le résultat suivant :

```bash
Element[0] = 100
Element[1] = 101
Element[2] = 102
Element[3] = 103
Element[4] = 104
Element[5] = 105
Element[6] = 106
Element[7] = 107
Element[8] = 108
Element[9] = 109
```

## Voir les tableaux en détail

Il y a des concepts importants liés aux tableaux qui devraient être clairs pour un programmeur Go :

**Concept et description**

- **Tableaux multidimensionnels** - Go supporte les tableaux multidimensionnels. La forme la plus simple d'un tableau multidimensionnel est le tableau à deux dimensions.
- **Passage de tableaux aux fonctions** - Vous pouvez passer à la fonction un pointeur vers un tableau en spécifiant le nom du tableau sans index.