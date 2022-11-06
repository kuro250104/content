Avant d'étudier les éléments de base du langage de programmation Go, discutons d'abord de la structure minimale des programmes Go afin de pouvoir nous y référer dans les chapitres suivants.

## Exemple de Hello World

Un programme Go se compose essentiellement des parties suivantes :

- Déclaration des paquets
- Importation de paquets
- Fonctions
- Variables
- Déclarations et expressions
- Commentaires

Examinons un code simple qui imprimerait les mots "Hello World" :

```go
package main

import "fmt"

func main() {
    /* This is my first sample program. */
    fmt.Println("Hello, World!")
}
```

Examinons les différentes parties du programme ci-dessus :

- La première ligne du programme package main définit le nom du paquet dans lequel ce programme doit se trouver. Il s'agit d'une déclaration obligatoire, car les programmes Go sont exécutés dans des paquets. Le paquet principal est le point de départ de l'exécution du programme. Chaque paquetage a un chemin et un nom qui lui sont associés.
- La ligne suivante ```import "fmt"``` est une commande de préprocesseur qui indique au compilateur Go d'inclure les fichiers se trouvant dans le paquet fmt.
- La ligne suivante ```func main()``` est la fonction principale où l'exécution du programme commence.
- La ligne suivante ```/*...*/``` est ignorée par le compilateur et sert à ajouter des commentaires dans le programme. Les commentaires sont également représentés à l'aide de ```//```, comme les commentaires en Java ou en C++.
- La ligne suivante ```fmt.Println(...)``` est une autre fonction disponible en Go qui permet d'afficher le message "Hello, World !" à l'écran. Ici, le paquet ```fmt``` a exporté la méthode ```Println``` qui est utilisée pour afficher le message à l'écran.
- Remarquez le P majuscule de la méthode ```Println```. Dans le langage Go, un nom est exporté s'il commence par une majuscule. Exporté signifie que la fonction ou la variable/constante est accessible à l'importateur du paquet respectif.

## Exécution d'un programme Go

Voyons comment enregistrer le code source dans un fichier, le compiler, et enfin exécuter le programme. Veuillez suivre les étapes indiquées ci-dessous :

- Ouvrez un éditeur de texte et ajoutez le code mentionné ci-dessus.
- Enregistrez le fichier sous le nom de hello.go
- Ouvrez l'invite de commande.
- Allez dans le répertoire où vous avez enregistré le fichier.
- Tapez go run hello.go et appuyez sur entrée pour exécuter votre code.
- S'il n'y a pas d'erreurs dans votre code, vous verrez "Hello World !" s'afficher à l'écran.

```bash
$ go run hello.go
Hello, World!
```

Assurez-vous que le compilateur Go se trouve dans votre chemin et que vous l'exécutez dans le répertoire contenant le fichier source ```hello.go```.