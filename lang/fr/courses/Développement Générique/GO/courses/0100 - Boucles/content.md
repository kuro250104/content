Il peut arriver que vous ayez besoin d'exécuter un bloc de code plusieurs fois. En général, les instructions sont exécutées de manière séquentielle : La première instruction d'une fonction est exécutée en premier, suivie de la deuxième, et ainsi de suite.

Les langages de programmation fournissent diverses structures de contrôle qui permettent des chemins d'exécution plus complexes.

Une instruction de boucle permet d'exécuter une instruction ou un groupe d'instructions plusieurs fois. Voici la forme générale d'une instruction de boucle dans la plupart des langages de programmation :

![Forme générale d'une instruction de boucle](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/GO/courses/0100%20-%20Boucles/images/image1.jpg)

Le langage de programmation Go fournit les types de boucles suivants pour gérer les besoins de bouclage.

**Type de boucle et description**

- **pour la boucle** - Elle exécute une séquence d'instructions plusieurs fois et abrège le code qui gère la variable de la boucle.
- **boucles imbriquées** - Ce sont une ou plusieurs boucles à l'intérieur d'une boucle for.

## Déclarations de contrôle de boucle

Les instructions de contrôle de boucle modifient une exécution par rapport à sa séquence normale. Lorsqu'une exécution quitte sa portée, tous les objets automatiques qui ont été créés dans cette portée sont détruits.

Go supporte les instructions de contrôle suivantes :

**Déclaration de contrôle et description**

- **instruction break** - Elle met fin à une boucle for ou à une instruction switch et transfère l'exécution à l'instruction qui suit immédiatement la boucle for ou l'instruction switch.
- **Instruction continue** - Elle permet à la boucle de sauter le reste de son corps et de tester à nouveau sa condition avant de la réitérer.
- **Instruction goto** - Elle transfère le contrôle à l'instruction étiquetée.

## La boucle infinie

Une boucle devient une boucle infinie si sa condition ne devient jamais fausse. La boucle for est traditionnellement utilisée à cette fin. Comme aucune des trois expressions qui forment la boucle for n'est requise, vous pouvez créer une boucle infinie en laissant l'expression conditionnelle vide ou en lui passant true.

```go
package main

import "fmt"

func main() {
    for true  {
        fmt.Printf("This loop will run forever.\n");
    }
}
```

Lorsque l'expression conditionnelle est absente, elle est supposée être vraie. Vous pouvez avoir une expression d'initialisation et d'incrémentation, mais les programmeurs C utilisent plus souvent la construction for(; ;) pour signifier une boucle infinie.

__Remarque__ : Vous pouvez mettre fin à une boucle infinie en appuyant sur les touches Ctrl + C.