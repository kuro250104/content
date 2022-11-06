## Durée approximative

1 jour

## Prérequis

- <a href="https://microlead.fr/echelles/php" title="Prérequis en PHP" target="_blank">PHP niveau 6</a>

## Énoncé

### Description courte

Créer un système de connexion/inscription sur un site web en PHP.

### Listing de fonctionnalités

Le site doit posséder une page de login avec 2 champs : « email » et « mot de passe », ainsi que 2 boutons : « login » (ou « se connecter »), et « register » (ou « s’inscrire »).

Au clic sur le bouton « login » l’application vérifie si la valeur du champ email est existante en base de données et si le mot de passe associé est similaire à celui fourni.

Si c’est le cas, l’utilisateur est redirigé vers une page lui indiquant qu’il a réussi à se connecter avec un message dans le style de « Bravo *Prénom* *Nom*, vous êtes connecté ! ». Sinon il est redirigé vers la page de login, avec une notification d’échec de l’authentification affichée.

Au clic sur le bouton « register », l’utilisateur est redirigé vers une page d’inscription avec 5 champs : « nom », « prénom », « email », « mot de passe », « confirmer le mot de passe » ainsi qu’un bouton « register ».

Au clic sur ce bouton, si les conditions des champs sont respectées (email dans le champ email, deux fois le même mot de passe) l’utilisateur s’inscrit, un nouvel utilisateur est créé en base de données avec ses informations et il se connecte automatiquement pour arriver sur la page de succès de connexion.

Si l’inscription échoue, il revient vers la page d’inscription avec un message lui indiquant son erreur lors de l’inscription.

### Contraintes

- Les caractères entrés dans le champ mot de passe doivent être masqués.
- Un mot de passe doit absolument contenir au moins 1 caractère minuscule, 1 caractère majuscule, 1 chiffre et 1 caractère spécial. Il doit avoir une longueur comprise entre 8 et 20.
- Deux utilisateurs ne peuvent pas avoir le même email.
- Il ne doit pas être possible d’accéder la page de succès de connexion sans être connecté, même en passant par l’URL.

### Critères de réussite

Il est possible de se connecter et de s’inscrire. L’inscription génère bien un utilisateur en base de données et la connexion permet bien de le récupérer. Les deux formulaires respectent bien les contraintes de leurs champs. Il n’est pas possible d’accéder à la page de succès sans être connecté.

### Astuces

#### Astuce 1

Pour gérer les contraintes de champ, il vous sera sans doute utile de vous pencher sur le concept des regex.