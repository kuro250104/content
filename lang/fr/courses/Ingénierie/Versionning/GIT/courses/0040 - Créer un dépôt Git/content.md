La commande git init est la première commande que vous exécuterez sur Git. La commande git init est utilisée pour créer un nouveau dépôt vierge. Elle est utilisée pour faire d'un projet existant un projet Git. Plusieurs commandes Git sont exécutées à l'intérieur du dépôt, mais la commande init peut être exécutée en dehors du dépôt.

La commande git init crée un sous-répertoire .git dans le répertoire de travail actuel. Ce sous-répertoire nouvellement créé contient toutes les métadonnées nécessaires. Ces métadonnées peuvent être classées en objets, réfs et fichiers temporaires. Il initialise également un pointeur HEAD pour la branche principale du dépôt.

## Création du premier dépôt

Le système de contrôle de version Git permet de partager des projets entre développeurs. Pour apprendre Git, il est essentiel de comprendre comment on peut créer un projet sur Git. Un dépôt est un répertoire qui contient toutes les données relatives au projet. Il peut également y avoir plus d'un projet sur un seul dépôt.

Il est possible de créer un dépôt pour des projets vierges ou existants. Voici comment créer un dépôt :

### Créer un dépôt vide

Pour créer un dépôt vierge, ouvrez une ligne de commande dans le répertoire souhaité et exécutez la commande init comme suit :

```git
git init
Initialized empty Git repository in /<path folder>/project.git/
```

### Créer un dépôt pour un projet existant

Si vous voulez partager votre projet sur un système de contrôle de version et le contrôler avec Git, alors, parcourez le répertoire de votre projet et lancez la ligne de commande git (Git Bash pour Windows) ici. Pour initialiser un nouveau dépôt, exécutez la commande ci-dessous :

```git
git init 
```

La commande ci-dessus va créer un nouveau sous-répertoire nommé .git qui contient tous les fichiers de dépôt nécessaires. Le sous-répertoire .git peut être considéré comme le squelette d'un dépôt Git.

Un dépôt vide .git est ajouté au projet existant. Si nous voulons commencer le contrôle de version pour les fichiers existants, nous devons suivre ces fichiers avec la commande git add, suivie d'un commit.

### Créer un dépôt et un répertoire en même temps

La commande git init nous permet de créer un nouveau dépôt vide et un répertoire ensemble. Le dépôt vide .git est créé sous le répertoire. Supposons que je veuille créer un dépôt vide avec un nom de projet, alors nous pouvons le faire avec la commande git init.

```git
git init NewDirectory 
```

La commande ci-dessus va créer un dépôt .git vide dans un répertoire nommé ```NewDirectory```.