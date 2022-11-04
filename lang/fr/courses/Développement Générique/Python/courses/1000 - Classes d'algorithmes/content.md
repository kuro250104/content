Les algorithmes sont des étapes non ambiguës qui doivent nous donner une réponse bien définie en traitant zéro ou plusieurs entrées. Cela conduit à de nombreuses approches dans la conception et l'écriture des algorithmes. Il a été observé que la plupart des algorithmes peuvent être classés dans les catégories suivantes.

## Algorithmes gourmands

Les algorithmes avides tentent de trouver une solution optimale localisée, ce qui peut éventuellement conduire à des solutions optimisées au niveau mondial. Cependant, les algorithmes avides ne fournissent généralement pas de solutions optimisées au niveau mondial.

Les algorithmes avides recherchent donc une solution facile à ce moment précis sans tenir compte de son impact sur les étapes futures. C'est similaire à la façon dont les humains résolvent des problèmes sans examiner en détail les données fournies.

La plupart des algorithmes de mise en réseau utilisent l'approche gourmande. Voici une liste de quelques-uns d'entre eux :

- Problème du voyageur de commerce
- Algorithme de l'arbre à portée minimale de Prim
- Algorithme de l'arbre à portée minimale de Kruskal
- Algorithme de l'arbre à portée minimale de Dijkstra

## Diviser pour mieux régner

Cette classe d'algorithmes consiste à diviser le problème donné en sous-problèmes plus petits, puis à résoudre chacun de ces sous-problèmes indépendamment. Lorsque le problème ne peut plus être divisé, nous commençons à fusionner la solution de chacun des sous-problèmes pour arriver à la solution du plus gros problème.

Les exemples importants d'algorithmes de type diviser pour régner sont :

- Tri par fusion
- Tri rapide
- Algorithme de l'arbre d'expansion minimal de Kruskal
- Recherche binaire

## Programmation dynamique

La programmation dynamique implique de diviser le plus gros problème en plus petits, mais contrairement à la méthode "diviser pour régner", elle n'implique pas de résoudre chaque sous-problème indépendamment. Les résultats des petits sous-problèmes sont plutôt mémorisés et utilisés pour des sous-problèmes similaires ou qui se chevauchent.

La plupart du temps, ces algorithmes sont utilisés pour l'optimisation. Avant de résoudre le sous-problème en cours, l'algorithme dynamique essaie d'examiner les résultats des sous-problèmes précédemment résolus. Les algorithmes dynamiques sont motivés par une optimisation globale du problème et non par une optimisation locale.

Les exemples importants d'algorithmes de programmation dynamique sont :

- Série de nombres de Fibonacci
- Problème de Knapsack
- Tour de Hanoi