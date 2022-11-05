## Système de contrôle des versions

**Un système de contrôle des versions** (*Version Control System, VCS*) est un logiciel qui aide les développeurs de logiciels à travailler ensemble et à conserver un historique complet de leur travail.

Voici la liste des fonctions d'un VCS :

- Permet aux développeurs de travailler simultanément.
- Ne permet pas d'écraser les modifications de l'autre.
- Maintient un historique de chaque version.

Les types de VCS sont les suivants :

- Système de contrôle de version centralisé (CVCS).
- Système de contrôle de version distribué/décentralisé (DVCS).

Dans ce chapitre, nous nous concentrerons uniquement sur les systèmes de contrôle de version distribués et plus particulièrement sur Git. Git fait partie des systèmes de contrôle de version distribués.

## Système de contrôle de version distribué

Le système de contrôle de version centralisé (CVCS) utilise un serveur central pour stocker tous les fichiers et permet la collaboration en équipe. Mais l'inconvénient majeur du CVCS est son point de défaillance unique, c'est-à-dire la défaillance du serveur central. Malheureusement, si le serveur central tombe en panne pendant une heure, personne ne peut collaborer du tout pendant cette heure. Et même dans le pire des cas, si le disque du serveur central est corrompu et qu'aucune sauvegarde appropriée n'a été effectuée, vous perdrez tout l'historique du projet. C'est ici qu'intervient le système de contrôle de version distribué (DVCS).

Les clients DVCS ne se contentent pas de vérifier le dernier instantané du répertoire, mais ils font également un miroir complet du référentiel. Si le serveur tombe en panne, le référentiel de n'importe quel client peut être copié sur le serveur pour le restaurer. Chaque extraction est une sauvegarde complète du référentiel. Git ne dépend pas du serveur central et c'est pourquoi vous pouvez effectuer de nombreuses opérations lorsque vous êtes hors ligne. Vous pouvez livrer des modifications, créer des branches, consulter les journaux et effectuer d'autres opérations lorsque vous êtes hors ligne. Vous avez besoin d'une connexion réseau uniquement pour publier vos modifications et prendre connaissance des dernières modifications.

## Avantages

### Libre et open source

Git est publié sous la licence open source GPL. Il est disponible gratuitement sur Internet. Vous pouvez utiliser Git pour gérer des projets immobiliers sans payer un seul centime. Comme il s'agit d'une source ouverte, vous pouvez télécharger son code source et également effectuer des modifications en fonction de vos besoins.

### Rapide et petit

Comme la plupart des opérations sont effectuées localement, cela donne un avantage énorme en termes de vitesse. Git ne dépend pas du serveur central ; c'est pourquoi il n'est pas nécessaire d'interagir avec le serveur distant pour chaque opération. La partie centrale de Git est écrite en C, ce qui évite les surcharges d'exécution associées à d'autres langages de haut niveau. Bien que Git reflète l'intégralité du dépôt, la taille des données côté client est faible. Cela illustre l'efficacité de Git pour compresser et stocker les données côté client.

### Sauvegarde implicite

Les risques de perte de données sont très rares lorsqu'il en existe plusieurs copies. Les données présentes sur n'importe quel côté client reflètent le référentiel, et peuvent donc être utilisées en cas de panne ou de corruption du disque.

### Sécurité

Git utilise une fonction de hachage cryptographique commune appelée fonction de hachage sécurisée (SHA1), pour nommer et identifier les objets dans sa base de données. Chaque fichier et chaque commit est vérifié et récupéré par sa somme de contrôle au moment du checkout. Cela implique qu'il est impossible de modifier le fichier, la date, le message de commit et toute autre donnée de la base de données Git sans connaître Git.

### Pas besoin d'un matériel puissant

Dans le cas du CVCS, le serveur central doit être suffisamment puissant pour répondre aux demandes de l'ensemble de l'équipe. Pour les petites équipes, ce n'est pas un problème, mais lorsque la taille de l'équipe augmente, les limitations matérielles du serveur peuvent constituer un goulot d'étranglement en termes de performances. Dans le cas du DVCS, les développeurs n'interagissent pas avec le serveur, sauf s'ils ont besoin de pousser ou de tirer des changements. Tout le travail se fait du côté client, et le matériel du serveur peut donc être très simple.

### Des embranchements plus faciles

CVCS utilise un mécanisme de copie bon marché. Si nous créons une nouvelle branche, il copiera tous les codes dans la nouvelle branche, ce qui prend beaucoup de temps et n'est pas efficace. De plus, la suppression et la fusion de branches dans CVCS sont compliquées et prennent beaucoup de temps. Mais la gestion des branches avec Git est très simple. Il suffit de quelques secondes pour créer, supprimer et fusionner des branches.

## Terminologies DVCS

### Dépôt local

Chaque outil VCS fournit un poste de travail privé comme copie de travail. Les développeurs effectuent des modifications dans leur espace de travail privé et, après validation, ces modifications sont intégrées au dépôt. Git va plus loin en leur fournissant une copie privée de l'ensemble du référentiel. Les utilisateurs peuvent effectuer de nombreuses opérations avec ce dépôt, comme ajouter un fichier, supprimer un fichier, renommer un fichier, déplacer un fichier, livrer des modifications, et bien plus encore.

### Répertoire de travail et index

Le répertoire de travail est l'endroit où les fichiers sont extraits. Dans les autres CVCS, les développeurs effectuent généralement des modifications et livrent leurs changements directement dans le dépôt. Mais Git utilise une stratégie différente. Git ne suit pas chaque fichier modifié. Chaque fois que vous livrez une opération, Git recherche les fichiers présents dans la zone de transit. Seuls les fichiers présents dans la zone de transit sont pris en compte pour le commit et non pas tous les fichiers modifiés.

Voyons le flux de travail de base de Git.

- **Étape 1** : Vous modifiez un fichier du répertoire de travail.
- **Étape 2** : Vous ajoutez ces fichiers à la zone de transit.
- **Étape 3** : Vous effectuez l'opération commit qui déplace les fichiers de la zone de transit. Après l'opération push, les changements sont stockés de façon permanente dans le dépôt Git.

### Blobs

Blob est l'abréviation de Binary Large Object. Chaque version d'un fichier est représentée par un blob. Un blob contient les données du fichier mais ne contient pas de métadonnées sur le fichier. C'est un fichier binaire, et dans la base de données Git, il est nommé comme le hachage SHA1 de ce fichier. Dans Git, les fichiers ne sont pas adressés par des noms. Tout est adressé par le contenu.

### Arbres

Tree est un objet qui représente un répertoire. Il contient des blobs ainsi que d'autres sous-répertoires. Un arbre est un fichier binaire qui stocke les références aux blobs et aux arbres qui sont également nommés comme hachage SHA1 de l'objet arbre.

### Commits

Le commit contient l'état actuel du référentiel. Un commit est également nommé par un hash SHA1. Vous pouvez considérer un objet commit comme un noeud de la liste liée. Chaque objet commit a un pointeur vers l'objet commit parent. A partir d'un commit donné, vous pouvez remonter le temps en regardant le pointeur du parent pour voir l'historique du commit. Si un commit a plusieurs commits parents, alors ce commit particulier a été créé en fusionnant deux branches.

### Branches

Les branches sont utilisées pour créer une autre ligne de développement. Par défaut, Git a une branche master, qui est la même que le tronc dans Subversion. Habituellement, une branche est créée pour travailler sur une nouvelle fonctionnalité. Une fois la fonctionnalité terminée, elle est fusionnée avec la branche master et la branche est supprimée. Chaque branche est référencée par HEAD, qui pointe vers le dernier commit de la branche. Chaque fois que vous faites un commit, HEAD est mis à jour avec le dernier commit.

### Tags

L'étiquette attribue un nom significatif à une version spécifique dans le référentiel. Les tags sont très similaires aux branches, mais la différence est que les tags sont immuables. Cela signifie que le tag est une branche, que personne n'a l'intention de modifier. Une fois qu'une étiquette est créée pour un commit particulier, même si vous créez un nouveau commit, elle ne sera pas mise à jour. Habituellement, les développeurs créent des balises pour les versions de produits.

### Clone

L'opération clone crée l'instance du référentiel. L'opération clone ne vérifie pas seulement la copie de travail, mais elle reflète également le référentiel complet. Les utilisateurs peuvent effectuer de nombreuses opérations avec ce référentiel local. Le seul moment où le réseau est impliqué est lorsque les instances du référentiel sont synchronisées.

### Pull

L'opération pull copie les changements d'une instance de référentiel distante vers une instance locale. L'opération pull est utilisée pour la synchronisation entre deux instances de référentiel. C'est la même chose que l'opération de mise à jour dans Subversion.

### Push

L'opération push copie les changements d'une instance de dépôt locale vers une instance distante. Ceci est utilisé pour stocker les changements de façon permanente dans le dépôt Git. C'est la même chose que l'opération commit dans Subversion.

### HEAD

HEAD est un pointeur, qui pointe toujours vers le dernier commit de la branche. Chaque fois que vous faites un commit, HEAD est mis à jour avec le dernier commit. Les têtes des branches sont stockées dans le répertoire .git/refs/heads/.

### Révision

La révision représente la version du code source. Les révisions dans Git sont représentées par des commits. Ces commits sont identifiés par des hachages sécurisés SHA1.

### URL

L'URL représente l'emplacement du dépôt Git. L'URL Git est stockée dans le fichier de configuration.