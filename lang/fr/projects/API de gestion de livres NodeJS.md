## Durée approximative

1 jour

## Prérequis

- JavaScript : niveau 10
- NodeJS : niveau 9

## Énoncé

### Description courte

Créer une API de gestion de livres accessible via le protocole REST qui stocke ses données dans un fichier JSON local.

### Listing de fonctionnalités

- L’API doit pouvoir retourner tous les livres stockés ou les informations spécifiques à 1 livre récupéré grâce à son id.
- Elle doit pouvoir modifier les informations d’un livre ou en supprimer un de la base.
- La base de données devra être stockée dans un fichier JSON séparé qui sera lu, modifié et réécrit au besoin.

### Éléments donnés

L’entité livre se constitue des champs suivants :

- Titre
- Auteur
- Genre
- Thèmes
- Etat
- Statut

### Contraintes

- Respecter les conventions REST

### Critères de réussite

Sur différentes routes testées via Postman, l’API renvoie la liste des livres ou les informations d’un livre particulier, crée un nouveau livre et l’ajoute à la base, modifie un livre présent en base, et supprime définitivement un livre stocké.

### Astuces

#### Astuce 1

Pour gérer le protocole REST, l’API doit lancer différentes fonctions dépendamment de la route et de la méthode par laquelle elle est appelée. Pour ce faire, NodeJS dispose du module « express ».

#### Astuce 2

Pour gérer la base de données dans un fichier JSON, l’API doit lire et écrire dans un fichier. Ceci peut se faire en NodeJS via le module « fs ».

#### Astuce 3

L’API peut prendre la forme de plusieurs fonctions appelées sur des routes différentes. Une route pour accéder à la liste de tous les livres (en GET, via une URL du type « …/livre »). Une route pour accéder aux informations relatives à un livre (en GET, via une URL du type « …/livre/ :id »). Une route d’ajout de livre, sur la même URL que l’accès à la liste mais via la méthode PUT. Une route de modification d’un livre similaire à celle d’accès aux informations d’un livre spécifique mais en POST. Une autre, identique mais en DELETE pour gérer la suppression. Et enfin une dernière de modification de statut (en POST, via une URL du type « …/livre/statut/ :id »), servant à indiquer si un livre est emprunté ou disponible.