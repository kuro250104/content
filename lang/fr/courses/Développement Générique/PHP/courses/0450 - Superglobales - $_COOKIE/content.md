La superglobale ```$_COOKIE``` stocke les variables transmises au script actuel avec la requête HTTP sous la forme de cookies. ```$HTTP_COOKIE_VARS``` contient également les mêmes informations, mais n'est pas une superglobale, et est désormais obsolète.

## Qu'est-ce qu'un cookie ?

Les cookies sont des fichiers texte stockés par un serveur sur l'ordinateur du client et ils sont conservés à des fins de suivi. PHP supporte de manière transparente les cookies HTTP. Les cookies sont généralement placés dans un en-tête HTTP. JavaScript peut aussi définir un cookie directement sur un navigateur.

Le script du serveur envoie un ensemble de cookies au navigateur. Il stocke ces informations sur la machine locale pour une utilisation ultérieure. La prochaine fois que le navigateur enverra une requête au serveur web, il enverra ces informations de cookies au serveur et le serveur utilisera ces informations pour identifier l'utilisateur.

PHP contient la fonction ```setcookie``` pour créer un objet cookie qui sera envoyé au client avec la réponse HTTP.

## setcookie

### Syntaxe

``` php
setcookie(nom, valeur, expiration, chemin, domaine, sécurité);
```

### Paramètres

- **Nom** : nom du cookie stocké.
- **Valeur** : définit la valeur de la variable nommée.
- **Expiration** : spécifie un temps futur en secondes depuis le 1er janvier 1970 00:00:00 GMT.
- **Chemin** : répertoires pour lesquels le cookie est valide.
- **Domaine** : spécifie le nom de domaine dans les très grands domaines.
- **Sécurité** : 1 pour HTTPS. Par défaut, 0 pour le HTTP normal.

### Exemple

``` php
<?php        

//on définit un nouveau cookie prenom
setcookie('prenom','lucie', time()+3600);   
//on affiche le contenu du cookie
echo $_COOKIE['prenom'];

?>
```

### Réponse

Le navigateur affichera le résultat suivant :

``` php
lucie
```

Pour supprimer le cookie, définissez le cookie avec une date qui a déjà expiré.