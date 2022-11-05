La commande git add est utilisée pour ajouter le contenu des fichiers à l'index. Cette commande met à jour le contenu actuel de l'arbre de travail vers la zone de transit. Elle prépare également le contenu de la zone de transit pour le prochain commit. Chaque fois que nous ajoutons ou mettons à jour un fichier dans notre projet, il est nécessaire de transmettre les mises à jour à la zone de transit.

La commande git add est un élément central de la technologie Git. Elle ajoute généralement un fichier à la fois, mais il existe des options permettant d'ajouter plus d'un fichier à la fois.

L'"index" contient un instantané des données de l'arbre de travail. Cet instantané sera transmis pour le prochain commit.

La commande git add peut être exécutée plusieurs fois avant de faire un commit. Toutes ces opérations d'ajout peuvent être regroupées en un seul commit. La commande add ajoute les fichiers qui sont spécifiés sur la ligne de commande.

La commande git add n'ajoute pas le fichier .gitignore par défaut.

## Git add - Ajout d’un fichier

La commande Git add est une commande directe. Elle ajoute des fichiers à la zone de transit. Nous pouvons ajouter un ou plusieurs fichiers à la fois dans la zone de transit. Elle sera exécutée comme :

```git
git add <File name>
```

La commande ci-dessus ajoute le fichier à la zone de transit git, mais elle ne peut pas encore être partagée sur le système de contrôle de version. Une opération de commit est nécessaire pour la partager.

Pour créer un fichier pour votre dépôt, utilisez la commande touch comme suit :

```bash
touch newfile.txt  
```

Et vérifiez l'état si elle est non suivie ou non par la commande git status comme suit :

```git
git status
```

Cette commande affiche le résultat suivant :

```bash
Sur la branche master
Fichiers non suivis:
    (utilisez "git add <fichier>..." pour inclure dans ce qui sera validé)
    	newfile.txt

aucune modification ajoutée à la validation mais des fichiers non suivis sont présents (utilisez "git add" pour les suivre)
```

La commande ci-dessus affichera les fichiers non suivis du dépôt. Ces fichiers peuvent être ajoutés à notre dépôt. Nous avons créé un fichier ```newfile.txt```, donc pour ajouter ce fichier, exécutez la commande ci-dessous :

```git
git add newfile.txt  
```

## Git add - Ajout de tous les fichiers

Git nous facilite la tâche avec une option unique de la commande add qui nous permet d'ajouter tous les fichiers disponibles en une seule fois. Pour ajouter tous les fichiers du dépôt, exécutez la commande add avec l'option -A. Nous pouvons utiliser '.' (un point) au lieu de l'option -A. Cette commande mettra en scène tous les fichiers à la fois. Elle s'exécutera comme suit :

```git
git add -A
# Ou
git add .
```

La commande ci-dessus ajoutera tous les fichiers disponibles dans le dépôt.

## Suppression des fichiers de la zone de transit

La commande git add est également utilisée pour supprimer des fichiers de la staging area. Si nous supprimons un fichier du dépôt, il est alors disponible pour notre dépôt en tant que fichier non suivi. La commande add est utilisée pour le supprimer de la zone de transit.

## Ajouter uniquement les nouveaux fichiers et fichiers modifiés

Git nous permet de ne mettre en scène que les fichiers mis à jour et nouvellement créés à la fois. Pour ce faire, nous utiliserons l'option ignorer la suppression. Elle sera utilisée comme suit : ```git add --ignore-removal .```

## Ajouter tous les fichiers modifiés et supprimés

Git add nous facilite une variété d'options. Il existe une autre option disponible dans Git, qui nous permet de mettre en scène uniquement les fichiers modifiés et supprimés. Il ne mettra pas en scène le fichier nouvellement créé. Pour mettre en scène uniquement les fichiers modifiés et supprimés, exécutez la commande ci-dessous : ```git add -u```

## Ajout de fichiers par Wildcard

Git nous permet d'ajouter tous les fichiers d'un même modèle en une seule fois. C'est une autre façon d'ajouter plusieurs fichiers ensemble. Supposons que je veuille ajouter tous les fichiers java ou les fichiers texte, alors nous pouvons utiliser le pattern .java ou .txt. Pour ce faire, nous allons exécuter la commande suivante : ```git add *.java ```

La commande ci-dessus mettra en scène tous les fichiers Java. Le même schéma sera appliqué pour les fichiers texte.

L'étape suivante après l'ajout des fichiers est le commit pour le partager sur Git.

## Git Undo Add

Nous pouvons annuler une opération de git add. Cependant, cela ne fait pas partie de la commande git add, mais nous pouvons le faire via la commande git reset. Pour annuler une opération d'ajout, exécutez la commande : ```git reset <filename>```