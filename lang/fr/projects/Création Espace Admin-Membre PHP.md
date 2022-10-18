## Durée approximative

10 heures

## Prérequis

- HTML niveau 9
- CSS niveau 9
- PHP niveau 6
- Mysql niveau 10

## Énoncé

### Description courte

Réaliser une page de login et d’administration qui permettra de gérer de multiple compte membre ainsi que des publications d'articles.

### Listing de fonctionnalités

- Possibilité de se connecter en tant qu’admin ou membre
- Deux espaces différents en fonction du grade de l’utilisateur
- Possibilité de créer et supprimer des membres en tant qu’admin
- Possibilité de créer, modifier ou supprimer des articles en tant qu’admin
- Possibilité de lecture uniquement pour les membres (liste de membre et articles)
- Possibilité de logout

### Éléments donnés

Espace admin est composé de 9 fichiers: 

- Index.php
- Connexion.php
- Deconnexion.php
- Membres.php
- Supprimer-membre.php
- Articles.php
- Modifier-article.php
- Publier-article.php
- Supprimer-article.php

La base de données sera composée de deux tables :

- Membres
- Articles

### Contraintes

- Les Formulaires doivent être remplis si ce n’est pas le cas un message d’erreur doit être retourné en fonction des situations.
- La page de Connexion devra rediriger vers une page index.php lorsque les informations entrées dans le formulaire sont correctes.
- Le logout détruira la session en cours et redirigera vers la page de login.
- Les différentes tables doivent être auto-incrémentées.
- Les membres n’ont que le droit de lecture.
- Les mots de passe doivent être cryptés.

### Critères de réussite

Le projet est réussi lorsque quand vous vous connectez en tant qu’admin vous pouvez créer et supprimer des utilisateurs et également créer, modifier et supprimer des articles 

Et que lorsque vous vous connectez en tant que membre vous ne pouvez que regarder la liste des membres et les différents articles.


### Astuces

#### Astuce 1

Utilisez la méthode ```POST``` pour la soumission des formulaires

#### Astuce 2

Voici une liste de quelques fonctions pouvant vous être utile pour la réalisation du projet : 

- ```Isset();```
- ```Empty();```
- ```Session_start();```
- ```Header(‘’);```
- ```PDO(‘mysql:host=localhost;dbname=espace_admin’,’root’,’’);```
- ```->prepare(“SELECT * FROM articles WHERE id = ?”);```
- ```->prepare(“DELETE FROM articles WHERE id = ?”);```
- ```->prepare(“UPDATE articles SET titre = ? AND descritpion = ? WHERE id = ?”);```
- ```->fetch();```
- ```openssl_encrypt():```
- ```openssl_decrypt():```