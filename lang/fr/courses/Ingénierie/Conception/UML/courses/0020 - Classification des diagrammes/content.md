Selon l’UML 2.5.1, les diagrammes sont triés par sémantique. On peut en distinguer 2 principales aboutissant à 3 différents regroupements : 

## La sémantique structurelle

Cette sémantique distingue les diagrammes de représentation d’un système à un instant donné. L’ensemble de ces diagrammes ne sont donc représentatifs que d’une période précise, et servent à schématiser l’ensemble ou une partie d’un système sans aucune considération d'événements ou d’évolution au fil du temps.

Lors de la réalisation de diagrammes à sémantique structurelle, il conviendra donc d’indiquer précisément ce que représente le diagramme ainsi que le contexte dans lequel il est placé.

L’ensemble de ces diagrammes sont basés sur des concepts fondamentaux de développements. On y retrouve les notions de typage, de namespace, de relation ou encore de dépendance.

Voici la liste des diagrammes structuraux de l’UML 2.5.1 : 

- **Diagramme de contexte** : Ils décrivent les typologies d’utilisateurs destinés à réaliser des interactions avec le système.
- **Diagramme de package** : Ils représentent des regroupements logiques d’éléments
- **Diagramme de classes** : ils décrivent les classes d’une application ainsi que leurs relations
- **Diagramme d’objets** : ils représentent des objets ainsi que leurs liens à un instant donné
- **Diagramme de composants** : Ils représentent les composants d’un point de vue physique
- **Diagramme de déploiement** : Ils modélisent l’aspect matériel
- **Diagramme de structure composite** : Ils représentent une vue simplifiée des relations entre les composants d’une classe
- **Diagramme de profils** : Ils représentent les différentes extensions d’un métamodèle.

## La sémantique comportementale

A contrario des diagrammes à sémantique structurelle, les diagrammes comportementaux s’axent sur l’évolution des éléments d’un schéma au fil du temps. Ces diagrammes vous permettront donc d’expliciter les évolutions de chaque élément en fonction d'événements définis.

Une notion importante à propos de ces types de diagrammes est qu’ils ne stipulent en aucun cas de durée concernant les évolutions présentées. Celles-ci n’étant pas schématisées, il est important de garder en tête à tout moment que la représentation des évolutions peut représenter aussi bien un intervalle de temps d’une seconde qu’un intervalle d’une année.

On distingue trois types de diagrammes comportementaux : 

- **Diagramme de cas d’utilisation** : Ils décrivent les fonctionnalités d’un système d’un point de vue utilisateur.
- **Diagramme d’états-transitions** :  Ils représentent le comportement d’un objet sous la forme d’un automate à différents états.
- **Diagramme d’activité** : Ils détaillent le comportement d’une opération.

## Les diagrammes à double sémantique

Certains diagrammes utilisés en UML sont concernés par les deux types de sémantiques : structurelle et comportementale. Ainsi ils peuvent représenter un état statique aussi bien qu’un état dynamique. Il sont en général davantage associés aux diagrammes à sémantique comportementale. Ils sont cependant souvent différenciés du fait de leur prise en compte d’éléments statiques. Retenez qu’en cas de doute, vous devrez les classer parmi les diagrammes comportementaux du fait de la prise en compte de potentielles évolutions dans le temps.

On distingue 4 types de diagrammes dans cette catégorie : 

- **Diagramme de séquence** : Ils représentent les interactions entre objets chronologiquement
- **Diagramme de communication** : Ils assurent une représentation spatiale des interactions entre objets.
- **Diagramme de temps** : Ils servent à représenter les variations d’un élément au cours du temps.
- **Diagramme de vue d’ensemble des interactions** : Ils représentent un déroulé logique entre des diagrammes de séquence.
- **Diagramme d’activité** : Ils sont une représentation graphique d’un processus d'exécution d’une action.