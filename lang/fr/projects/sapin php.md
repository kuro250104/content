## Durée approximative

2 jours

## Prérequis

- <a href="https://microlead.fr/echelles/html" title="Prérequis en HTML" target="_blank">PHP niveau 5</a>
- Algorithmie

## Énoncé

### Description courte

Le principe du projet est de générer un sapin de noël à partir d'un algorithme que vous devrez concevoir.

### Listing de fonctionnalités

Les fonctionnalités suivantes sont à réaliser dans l'ordre (n'essayez pas de tout faire en une seule fois si vous n'êtes pas parfaitement à l'aise avec l'algorithmique !).

1. Réaliser un algorithme qui soit capable de "dessiner" le sapin ci-dessous. Ne prenez pas en compre les "S", ni les boules de noël en dessous du sapin.
2. Créer une constante "FLOORS" au début de votre script. Celle-ci contiendra un nombre entier (Integer) ajustable, qui déterminera combien d'étages doit avoir le sapin. Votre algorithme doit maintenant dessiner autant d'étage que le nombre contenu dans cette constante.
3. Créer une constante "GARLAND" au début de votre script. Celle-ci sera de type "Boolean", et devra être définir à TRUE ou FALSE. Si la valeur est vraie, alors les "S" devront s'afficher sur votre sapin, sinon ils ne devront pas s'afficher. Votre algorithme doit être adapté pour prendre en compte ce nouveau paramètre.
4. Créer une constante "BALLS" au début de votre script. Celle-ci sera de type "Boolean", et devra être définir à TRUE ou FALSE. Si la valeur est vraie, alors les boules de noël en bas du sapin devront s'afficher, sinon elles ne s'affichent pas. Votre algorithme doit être adapté pour prendre en compte ce nouveau paramètre.
5. Créer une constante "REPLICA" au début de votre script. Celle-ci contiendra un nombre entier (Integer) ajustable, qui déterminera combien de sapins doivent être dessinés horizontalement, côte à côte (de gauche à droite). Tous les sapins ainsi dessinés doivent être positionnés sur la même ligne, quitte à faire apparaître une scrollbar sur votre navigateur.

### Éléments donnés

Voici le schéma de base du sapin, incluant toutes les options : 

```
            *
           ***
        S*******S
           ***
         *******
      S***********S
         *******
       ***********
    S***************S
       ***********
     ***************
  S*******************S
   | | | | *** | | | |
   0 0 0 0 *** 0 0 0 0
           ***
           ***
```

### Contraintes

- N'utilisez que du PHP
- Ne dessinez rien directement dans votre code PHP : chaque ligne doit ENTIÈREMENT être générée algorithmiquement.
