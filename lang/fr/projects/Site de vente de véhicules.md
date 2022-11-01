## Durée approximative

5 jours

## Prérequis

- PHP : niveau 7
- HTML : niveau 8
- MySQL : niveau 6

## Énoncé

### Description courte

Créer un site web de vente de véhicules connecté à une base de données et à un back-office pour gérer les stocks.

### Listing de fonctionnalités

Le site doit afficher une liste des véhicules disponibles rangés par type, avec un résumé de leurs informations respectives.

Chaque présentation de véhicule doit être accompagnée d’un bouton permettant d’accéder à une fiche détaillée de ce véhicule avec toutes les informations qui y sont liées.

Sur cette page de détail d’informations doit se trouver un bouton pour acheter le véhicule.

Au clic, le véhicule est considéré « acheté », son état est changé, il ne doit plus être proposé à la vente et une trace de cet achat doit s’inscrire en base de données.

Il doit exister une page de back-office donnant une vue succincte sur les véhicules et permettant d’en ajouter, modifier, ou supprimer certains. Depuis ce back-office on doit aussi pouvoir accéder à une liste des transactions.

### Contraintes

La base de données doit contenir au moins deux entités distinctes (« voitures » et « motos » par exemple) qui seront héritées d’une entité parent « véhicule ».

### Pour aller plus loin

- Il est possible de réaliser ce type de site de façon bien plus évidente via l’utilisation d’un framework comme Laravel ou Symfony.

### Critères de réussite

Le site est complet et fonctionnel. Il est possible de voir tous les véhicules rangés par type. On peut accéder aux informations d’un véhicule et l’acheter en cliquant sur le bouton associé. Le site est connecté à la base de données et cette dernière se met à jour adéquatement aux actions menées sur le site. Le back-office est accessible, fournit les infos des véhicules et des logs, et permet d’ajouter, modifier et supprimer des véhicules.
