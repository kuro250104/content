L'efficacité d'un algorithme peut être analysée à deux stades différents, avant et après sa mise en œuvre. Elles sont les suivantes :

- **Analyse a priori** : Il s'agit d'une analyse théorique d'un algorithme. L'efficacité d'un algorithme est mesurée en supposant que tous les autres facteurs, par exemple la vitesse du processeur, sont constants et n'ont aucun effet sur la mise en œuvre.
- **Analyse a posteriori** : Il s'agit d'une analyse empirique d'un algorithme. L'algorithme sélectionné est mis en œuvre à l'aide d'un langage de programmation. Il est ensuite exécuté sur la machine informatique cible. Dans cette analyse, les statistiques réelles, telles que le temps d'exécution et l'espace requis, sont collectées.

## Complexité de l'algorithme

Supposons que X soit un algorithme et que n soit la taille des données d'entrée. Le temps et l'espace utilisés par l'algorithme X sont les deux principaux facteurs qui déterminent l'efficacité de X.

- **Facteur temps** : Le temps est mesuré en comptant le nombre d'opérations clés telles que les comparaisons dans l'algorithme de tri.
- **Facteur espace** : L'espace est mesuré en comptant l'espace mémoire maximum requis par l'algorithme.

La complexité d'un algorithme ```f(n)``` donne le temps d'exécution et/ou l'espace de stockage requis par l'algorithme en fonction de ```n```, la taille des données d'entrée.

## Complexité de l'espace

La complexité spatiale d'un algorithme représente la quantité d'espace mémoire requise par l'algorithme au cours de son cycle de vie. L'espace requis par un algorithme est égal à la somme des deux composantes suivantes :

- Une partie fixe qui est un espace nécessaire pour stocker certaines données et variables, qui sont indépendantes de la taille du problème. Par exemple, les variables et constantes simples utilisées, la taille du programme, etc.
- Une partie variable est un espace requis par les variables, dont la taille dépend de la taille du problème. Par exemple, l'allocation dynamique de mémoire, l'espace de la pile de récursion, etc.

La complexité spatiale S(P) de tout algorithme P est S(P) = C + SP(I), où C est la partie fixe et S(I) est la partie variable de l'algorithme, qui dépend de la caractéristique d'instance I. Voici un exemple simple qui tente d'expliquer le concept :

Algorithme : SUM(A, B)

- Étape 1 - DÉMARRAGE
- Étape 2 - C ← A + B + 10
- Étape 3 - Arrêt

Ici, nous avons trois variables A, B et C et une constante. Par conséquent, S(P) = 1 + 3. Maintenant, l'espace dépend des types de données des variables données et des types de constantes et il sera multiplié en conséquence.

## Complexité du temps

La complexité temporelle d'un algorithme représente le temps nécessaire à l'algorithme pour s'exécuter jusqu'à son terme. La complexité temporelle peut être définie comme une fonction numérique T(n), où T(n) peut être mesuré comme le nombre d'étapes, à condition que chaque étape consomme un temps constant.

Par exemple, l'addition de deux entiers de n bits prend n étapes. Par conséquent, le temps de calcul total est T(n) = c ∗ n, où c est le temps pris pour l'addition de deux bits. Ici, nous observons que T(n) croît linéairement lorsque la taille de l'entrée augmente.