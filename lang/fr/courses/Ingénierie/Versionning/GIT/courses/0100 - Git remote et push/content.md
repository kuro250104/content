## Se connecter à un dépôt distant

La commande ```git remote add``` suivie du nom choisis de la connexion et de l’url du dépôt distant, permet de relier un dépôt distant à un dépôt local.

exemple:

Dans cet exemple, j’ai déjà créé un dépôt distant sur Github et je souhaite relier mon dépôt distant à mon dépôt local.

```git
git remote add origin https://github.com/nom_utilisateur/nom_du_depot_distant
```

Maintenant, une connexion à mon dépôt distant “origin” vient d’être créé.

## Supprimer une connexion à un dépôt distant

La commande ```git remote rm``` suivie du nom de la connexion permet de supprimer une connexion à un dépôt distant.

exemple:

```git
git remote rm origin
```

## Renommer une connexion à un dépôt distant

La commande ```git remote rename``` suivie du nom de la connexion actuelle et du nouveau nom, permet de renommer une connexion à un dépôt distant.

exemple:

```git
git remote rename origin main
```

Maintenant, la connexion à mon dépôt distant “origin”est renommé en “main”.

## Pousser ses commits à un dépôt distant 

La commande ```git push``` suivie du nom de la connexion et de la branche qui doit être poussée sur le dépôt distant, permet de pousser une branche d’un dépôt local sur un dépôt distant.

exemple:

```git
git push origin master
```

Une fois cette commande tapée, les commits de la branche master sont présents sur le dépôt distant.