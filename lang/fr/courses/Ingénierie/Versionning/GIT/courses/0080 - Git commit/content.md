## Étape avant de réaliser un commit 

Imaginons que l’on décide de créer une nouvelle version de notre projet “commit”. Pour réaliser cela, Il faut s’assurer que l’ensemble des fichiers qui devront être sauvegardés sont rattachés au dépôt. On utilise la commande ```git status``` pour vérifier cela.

exemple :

```git
git status
On branch master

No commits yet

Changes to be committed:
    (use “git rm --cached <file>...” to unstage)
        new file:   texte.txt
```

Dans ce cas précis le fichier texte.txt à un état (new file), il donc bien rattaché au dépôt. Si ce n’est pas le cas, il faudra utiliser la commande ```git add```.

## Réaliser un commit 

Une fois que les fichiers sont rattachés au dépôt, il suffit juste d’utiliser la commande ```git commit``` ce qui permet de créer une nouvelle version du dépôt autrement appelé “commit”. Dans ce cours, je vous présente 2 manières d’utiliser cette commande pour réaliser un “commit” :

### git commit

Lorsqu’on utilise la commande ```git commit``` sans lui passer d’argument, une nouvelle fenêtre s’ouvre utilisant l’éditeur par défaut qui est dans la majorité des cas VIM.

exemple :

```git
git commit
git status

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
# 
# Initial commit
# 
# Changes to be committed:
#       new file:   texte.txt
Project init

```

Pour finaliser le “commit” il faut lui donner un nom. Dans cette situation juste en dessous des symboles # j’écris le nom que je veux donner à ce “commit”, cette étape ne doit pas être négligée, car l’ensemble des collaborateurs du projet verront le nom de ces commits. Un “commit” bien rédigé permet facilement au reste de l’équipe de savoir quelles modifications on été ajouter au projet. Ceci étant fait, la commande nous retourne un message disant que le “commit” à bien été créé.

exemple :

```git
[master (root-commit) 078a46a] Project init
    1 file changed, 1 insertion(+)
    create mode 100644 texte.txt
```

### git commit -m

Une manière à mon sens plus simple de réaliser un nouveau “commit” est de passer à la commande ```git commit``` le drapeau ```-m``` en argument. Il ne reste plus qu'à préciser le nom du “commit” entre ```“”``` pour le créer.

exemple :

```git
git commit -m "Project init"
[master (root-commit) 6068f6e] Project init
    1 file changed, 1 insertion(+)
    create mode 100644 texte.txt
```

Ici la commande nous informe que le commit à bien été réalisé.

## Conseil

Il est conseillé de réaliser des commits régulièrement pour s’assurer d’avoir toujours une version de travail fournie.