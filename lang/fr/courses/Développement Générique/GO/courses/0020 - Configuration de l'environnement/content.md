## Configuration de l'environnement local

Si vous souhaitez toujours configurer votre environnement pour le langage de programmation Go, vous avez besoin des deux logiciels suivants, disponibles sur votre ordinateur :

- Un éditeur de texte
- Un compilateur Go

## Éditeur de texte

Vous aurez besoin d'un éditeur de texte pour taper vos programmes. Parmi les exemples d'éditeurs de texte, citons le Bloc-notes de Windows, la commande Edit de l'OS, Brief, Epsilon, EMACS, et vim ou vi.

Le nom et la version des éditeurs de texte peuvent varier selon les systèmes d'exploitation. Par exemple, le Bloc-notes est utilisé sur Windows, et vim ou vi est utilisé sur Windows ainsi que sur Linux ou UNIX.

Les fichiers que vous créez avec l'éditeur de texte sont appelés fichiers sources. Ils contiennent le code source du programme. Les fichiers sources des programmes Go sont généralement nommés avec l'extension ".go".

Avant de commencer votre programmation, assurez-vous que vous disposez d'un éditeur de texte et que vous avez suffisamment d'expérience pour écrire un programme informatique, l'enregistrer dans un fichier, le compiler et enfin l'exécuter.

## Le compilateur Go

Le code source écrit dans le fichier source est la source lisible par l'homme de votre programme. Il doit être compilé et transformé en langage machine pour que votre CPU puisse exécuter le programme selon les instructions données. Le compilateur du langage de programmation Go compile le code source dans son programme exécutable final.

La distribution Go se présente sous la forme d'un binaire installable pour FreeBSD (version 8 et supérieure), Linux, Mac OS X (Snow Leopard et supérieur) et les systèmes d'exploitation Windows avec des architectures de processeur x86 32 bits (386) et 64 bits (amd64).

La section suivante explique comment installer la distribution binaire de Go sur différents OS.

## Télécharger Go Archive

Téléchargez la dernière version du fichier d'archive installable Go depuis la page de téléchargement officielle du site. La version suivante est utilisée dans ce tutoriel : ```go1.4.windows-amd64.msi```.

Elle est copiée dans le dossier ```C:\>go```.

## Installation sur UNIX/Linux/Mac OS X, et FreeBSD

Extrayez l'archive de téléchargement dans le dossier ```/usr/local```, en créant un dossier Go dans ```/usr/local/go```. Par exemple :

```bash
tar -C /usr/local -xzf go1.4.linux-amd64.tar.gz
```

Ajoutez ```/usr/local/go/bin``` à la variable d'environnement PATH : 

- **Linux** : ```export PATH = $PATH:/usr/local/go/bin```
- **Mac** : ```export PATH = $PATH:/usr/local/go/bin```
- **FreeBSD** : ```export PATH = $PATH:/usr/local/go/bin```

Installation sur Windows

Utilisez le fichier MSI et suivez les instructions pour installer les outils Go. Par défaut, le programme d'installation utilise la distribution Go dans c:\Go. Le programme d'installation doit définir le répertoire ```c:\Go\bin``` dans la variable d'environnement PATH de Windows. Redémarrez tout invité de commande ouvert pour que le changement prenne effet.

## Vérification de l'installation

Créez un fichier go nommé test.go :

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

Maintenant exécutez ```test.go``` pour voir le résultat :

```bash
C:\Go_WorkSpace>go run test.go
```

Sortie

```bash
Hello, World!
```