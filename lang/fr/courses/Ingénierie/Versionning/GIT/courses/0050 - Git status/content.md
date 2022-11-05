## Les états d’un fichier

L’ensemble des fichiers contenues dans un projet peuvent avoir 3 états :

- Untracked,
- Modified,
- New file.

L’état “Untracked” signifie que le fichier vient d’être créé et qu’il est présent dans le projet mais qu’il n’est pas rattaché au dépôt.

L'état “Modified” signifie que le fichier a subi une modification.

L'état “New file” signifie que le fichier a bien été rattaché au dépôt.

La commande ```git status``` est très utilisée car elle permet de savoir l’état de l'ensemble des fichiers présents dans le dépôt. Il est conseillé d’utiliser cette commande tout au long du développement d’un projet pour s’assurer que l’ensemble des fichiers sont bien présents dans le dépôt avant un de créer un nouvelle version du dépôt (commit).

## Git status

Imaginons que l’on décide d’ajouter un fichier texte dans notre projet. 

La commande (touch) permet de créer un nouveau fichier dans notre projet.

exemple :

```bash
touch texte.txt
```

Ensuite, on vérifie que le fichier est bien présent dans le projet à l’aide de la commande (ls) qui permet d’afficher l’ensemble des fichiers présent dans le dossier.

exemple :

```bash
ls
texte.txt
```

Maintenant on utilise la commande ```git status``` qui renvoi l’état des fichiers de notre répertoire.

exemple :

```bash
git status
On branch master

No commits yet

Untracked files:
    (use "git add <file>..." to include in what will be committed)
        texte.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Dans cette situation on remarque que le fichier texte.txt à l’état “Untracked” puisqu’il vient d’être créé, de plus cette commande nous dit aussi qu’il n’y a aucun fichier validé (commit), ainsi que la branche sur laquelle on se situe “master”. Nous reparlerons des branches et des commits dans de prochains cours.

__Remarque__ : toutes les commandes sont à utiliser dans l’invité de commande (terminal).