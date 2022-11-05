## Qu'est ce qu’une branche ?

Créer une branche, c’est créer une “copie” d’un dépôt. Les branches permettent de développer et tester de nouvelles fonctionnalités sans impacter le dépôt de base. Par défaut dans un projet qui utilise Git la branche principale s’appelle “master”. On peut utiliser la commande ```git status``` qui retourne la branche sur laquelle on se situe.

exemple :

```git
git status
On branch master
```

Dans cet exemple, la commande nous informe que l’on se situe sur la branche “master”.

## Créer une branche 

Pour créer une branche, on utilise la commande ```git branch``` suivi du nom que l’on veut donner à celle-ci.

exemple :

```git
git branch fixture
```

Dans cet exemple, une nouvelle branche est créée. Elle porte le nom “fixture”. On peut afficher la liste des branches en tapant la commande ```git branch``` sans lui passer d’argument.

```git
git branch fixture
* master
```

La commande nous informe qu’il y a 2 branches et le symbole (*) indique sur quelle branche l’on se situe.

## Se déplacer sur une branche 

Pour se déplacer dans une branche, on utilise la commande ```git checkout``` suivi du nom de la branche sur laquelle on souhaite aller.

exemple :

```bash
git checkout fixture
Switched to branch 'fixture'
```

Dans cet exemple, la commande nous informe que l’on se situe à présent sur la branche  “fixture”.

## Supprimer sur une branche 

Pour supprimer une branche, on utilise la commande ```git branch -d``` suivi du nom de la branche que l’on veut supprimer.

exemple:

Imaginons que je souhaite supprimer la branche “fixture” que je viens de créer, pour commencer je dois plus me situer sur la branche que je veux supprimer.

```git
git checkout master
Switched to branch 'master'
```

Une fois que je suis sur la branche master je peux supprimer la branche “fixture”.

```bash
git branch -d fixture
Deleted branch fixture (was 2b341fd).
```

La commande ci-dessus renvoie un message informant que la branche “fixture” à été supprimée.