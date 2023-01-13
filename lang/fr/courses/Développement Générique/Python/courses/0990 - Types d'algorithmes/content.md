L'efficacité et la précision des algorithmes doivent être analysées pour les comparer et choisir un algorithme spécifique pour certains scénarios. Le processus de réalisation de cette analyse est appelé analyse asymptotique. Elle consiste à calculer le temps d'exécution de toute opération en unités mathématiques de calcul.

Par exemple, le temps d'exécution d'une opération est calculé comme f(n) et peut être pour une autre opération il est calculé comme g(n2). Cela signifie que le temps d'exécution de la première opération augmentera linéairement avec l'augmentation de n et que le temps d'exécution de la seconde opération augmentera exponentiellement lorsque n augmentera. De même, le temps d'exécution des deux opérations sera presque le même si n est significativement petit.

En général, le temps requis par un algorithme est de trois types :

- **Meilleur cas** : Temps minimum requis pour l'exécution du programme.
- **Cas moyen** : Temps moyen nécessaire à l'exécution du programme.
- **Pire cas** : Temps maximum nécessaire à l'exécution du programme.

## Notations asymptotiques

Les notations asymptotiques couramment utilisées pour calculer la complexité du temps d'exécution d'un algorithme.

- Notation Ο
- Notation Ω
- Notation θ

### Notation Big Oh, Ο

La notation Ο(n) est la manière formelle d'exprimer la limite supérieure du temps d'exécution d'un algorithme. Elle mesure la complexité temporelle dans le pire des cas ou le temps le plus long qu'un algorithme puisse prendre pour se terminer.

### Notation Oméga, Ω

La notation Ω(n) est la manière formelle d'exprimer la borne inférieure du temps d'exécution d'un algorithme. Elle mesure la complexité temporelle dans le meilleur des cas ou la meilleure quantité de temps qu'un algorithme peut éventuellement prendre pour se terminer.

### Notation thêta, θ

La notation θ(n) est la manière formelle d'exprimer à la fois la borne inférieure et la borne supérieure du temps d'exécution d'un algorithme…

## Notations asymptotiques courantes

Une liste de quelques notations asymptotiques courantes est mentionnée ci-dessous :

| **Complexité** | **Notation** |
| -- | -- | 
| constant | Ο(1) |
| logarithmique | Ο(log n) |
| linéaire | Ο(n) |
| n log n | Ο(n log n) |
| quadratique | Ο(n2) |
| cubique | Ο(n3) |
| polynomial | n^O(1) |
| exponentielle | 2^Ο(n) |
