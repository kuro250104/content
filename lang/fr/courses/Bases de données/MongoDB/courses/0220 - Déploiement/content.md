Lorsque vous préparez un déploiement MongoDB, vous devez essayer de comprendre comment votre application va se comporter en production. C'est une bonne idée de développer une approche cohérente et reproductible pour gérer votre environnement de déploiement afin de minimiser les surprises une fois en production.

La meilleure approche consiste à prototyper votre installation, à effectuer des tests de charge, à surveiller les paramètres clés et à utiliser ces informations pour faire évoluer votre installation. L'élément clé de cette approche consiste à surveiller de manière proactive l'ensemble de votre système - cela vous aidera à comprendre comment votre système de production tiendra le coup avant d'être déployé, et à déterminer où vous devrez ajouter de la capacité. En ayant un aperçu des pics potentiels d'utilisation de la mémoire, par exemple, vous pourrez éteindre un feu de verrou d'écriture avant qu'il ne se déclare.

Pour surveiller votre déploiement, MongoDB fournit certaines des commandes suivantes -

## mongostat

Cette commande vérifie l'état de toutes les instances mongod en cours d'exécution et renvoie les compteurs des opérations de la base de données. Ces compteurs incluent les insertions, les requêtes, les mises à jour, les suppressions et les curseurs. La commande indique également quand vous rencontrez des défauts de page, et montre votre pourcentage de verrouillage. Cela signifie que vous êtes à court de mémoire, que vous atteignez la capacité d'écriture ou que vous avez un problème de performance.

Pour exécuter la commande, démarrez votre instance mongod. Dans une autre invite de commande, allez dans le répertoire bin de votre installation mongodb et tapez mongostat.

```
D:\set up\mongodb\bin>mongostat
```

## mongotop

Cette commande suit et rapporte l'activité de lecture et d'écriture de l'instance MongoDB sur la base d'une collection. Par défaut, mongotop renvoie des informations par seconde, que vous pouvez modifier en conséquence. Vous devez vérifier que cette activité de lecture et d'écriture correspond à l'intention de votre application, et que vous ne lancez pas trop d'écritures dans la base de données à la fois, que vous ne lisez pas trop fréquemment depuis un disque, ou que vous ne dépassez pas la taille de votre ensemble de travail.

Pour exécuter la commande, démarrez votre instance mongod. Dans une autre invite de commande, allez dans le répertoire bin de votre installation mongodb et tapez mongotop.

```
D:\set up\mongodb\bin>mongotop
```

Pour que la commande mongotop renvoie des informations moins fréquemment, indiquez un nombre spécifique après la commande mongotop.

```
D:\set up\mongodb\bin>mongotop 30
```

L'exemple ci-dessus renverra des valeurs toutes les 30 secondes.
Outre les outils MongoDB, 10gen propose un service de surveillance hébergé gratuit, MongoDB Management Service (MMS), qui fournit un tableau de bord et vous donne un aperçu des mesures de l'ensemble de votre cluster.