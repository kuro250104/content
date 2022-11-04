L'analyse amortie consiste à estimer le temps d'exécution de la séquence d'opérations d'un programme sans tenir compte de l'étendue de la distribution des données dans les valeurs d'entrée. Un exemple simple est de trouver une valeur dans une liste triée plus rapidement que dans une liste non triée.

Si la liste est déjà triée, la distribution des données n'a pas d'importance. Mais bien sûr, la longueur de la liste a un impact car elle détermine le nombre d'étapes que l'algorithme doit franchir pour obtenir le résultat final.

Nous constatons donc que si le coût initial d'une seule étape d'obtention d'une liste triée est élevé, le coût des étapes suivantes pour trouver un élément devient considérablement faible. L'analyse amortie nous aide donc à trouver une limite au temps d'exécution le plus défavorable d'une séquence d'opérations. Il existe trois approches de l'analyse amortie.

- **Méthode comptable** : Elle consiste à attribuer un coût à chaque opération effectuée. Si l'opération réelle se termine plus rapidement que le temps imparti, un crédit positif est accumulé dans l'analyse.

Dans le scénario inverse, il s'agira d'un crédit négatif. Pour garder la trace de ces crédits accumulés, nous utilisons une pile ou une structure de données en arbre. Les opérations qui sont effectuées tôt (comme le tri de la liste) ont un coût amorti élevé, mais les opérations qui sont effectuées tard dans la séquence ont un coût amorti plus faible, car le crédit accumulé est utilisé. Le coût amorti est donc une limite supérieure du coût réel.

- **Méthode potentielle** : Dans cette méthode, le crédit accumulé est utilisé pour les opérations futures en tant que fonction mathématique de l'état de la structure de données. L'évaluation de la fonction mathématique et le coût amorti doivent être égaux. Ainsi, lorsque le coût réel est supérieur au coût amorti, il y a une diminution du potentiel et il est utilisé pour des opérations futures qui sont coûteuses.
- **Analyse globale** : Dans cette méthode, nous estimons la limite supérieure du coût total de n étapes. Le coût amorti est une simple division du coût total et du nombre d'étapes (n).