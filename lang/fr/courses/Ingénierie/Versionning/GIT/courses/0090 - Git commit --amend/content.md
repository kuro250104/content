## Modification du dernier commit

Dans un projet versionné avec Git on a la possibilité de modifier facilement  le dernier commit réalisé. La commande ```git commit --amend``` permet de combiner les changements stagés avec l’ancien commit à la place de créer un nouveau commit. Cette commande est aussi utilisée pour modifier le message attaché au commit.

## Modifier le message du dernier commit

Imaginons que vous venez de faire un commit et que votre message contient une erreur. Pour modifier ce message il faut ajouter le drapeau ```-m``` suivi du nouveau message.

exemple :

```git
git commit --amend -m "nouveau message"
```

Une fois cette commande renseignée le dernier commit aura comme nouveau message “nouveau message”.

## Modifier les fichiers commités

Imaginons que vous venez de faire un commit et que vous avez oublié de rattacher un des fichiers à votre dépôt. Le drapeau ```--no-edit``` permet de modifier le dernier commit sans modifier le message rattaché.

exemple :

```git
git add index.html
```

Avant d’utiliser la commande ```git commit --amend```, il faut d’abord attacher au dépôt les fichiers qu’on veut rajouter à notre commit.

```git
git commit --amend --no-edit
```

Une fois cette commande renseignée le dernier commit aura maintenant le fichier index.html en plus des fichiers que contient déjà le commit.