## Durée approximative

1 jour

## Prérequis

- Python - niveau 5

## Énoncé

### Description courte

Recréer le jeu du Mastermind en console de commande avec Python.

### Listing de fonctionnalités

- Au lancement l’application doit générer 5 chiffres aléatoires allant de 0 à 7, qu’il gardera en mémoire.
- L’application doit ensuite questionner l’utilisateur en lui demandant de rentrer 5 chiffres allant aussi de 0 à 7 via un input.
- Le programme doit ensuite comparer les chiffres fournis par l’utilisateur avec la suite qu’il a stockée.
- Il doit ensuite retourner dans la console le nombre de chiffres présents dans la suite, et combien d’entre eux sont à la bonne place.
- Si la suite de chiffres stockée est strictement identique à celle fournie par l’utilisateur, il gagne et l’application lui fait savoir avant de s’arrêter.
- Si au bout de 12 tours l’utilisateur n’a pas réussi à trouver la suite de chiffres, il perd et le programme lui indique avant de s’arrêter.

### Contraintes

- L’utilisateur ne doit pouvoir rentrer que des chiffres entre 0 et 7.
- Le message demandant à l’utilisateur de rentrer une suite de chiffres doit être envoyé par la même commande que l’input.

### Critères de réussite

- Le jeu est fonctionnel
- Il est possible de gagner ou de perdre
- Le jeu indique correctement la victoire et l’échec avant de s’arrêter

### Astuces

#### Astuce 1

Pour comparer chaque chiffre, il sera utile de transformer la chaîne fournie par l’utilisateur en un tableau.

#### Astuce 2

Pour générer un tableau à partir de la chaîne transmise par l’utilisateur, vous pouvez utiliser la commande « tableau = [int(x) for x in str(chaîneDeChiffres)] »

#### Astuce 3

Pour générer des entiers aléatoires entre 0 et 7, vous pouvez utiliser la fonction « randrange(8) »