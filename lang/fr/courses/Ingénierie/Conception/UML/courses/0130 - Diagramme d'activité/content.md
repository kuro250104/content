## Informations génériques

- **Type** : Comportemental
- **Périmètre** : Fonctionnel et Technique
- **Language** : Tous

## Définition / Utilisation

Le diagramme d’activités est un schéma UML permettant de modéliser un processus dans son ensemble. Il permet non seulement de détailler les différentes actions qui y sont présentes, mais également d’y inclure des conditions d’exécution ainsi que la prise en compte de différents acteurs, de telle sorte que le déroulé du processus devienne extrêmement clair et précis. Ce type de diagramme est par exemple tout indiqué pour documenter ou modéliser un workflow au sein d’une équipe.

Contrairement à d’autres diagrammes UML, il apporte également une vision temporelle. Sans pour autant disposer d’unité de valeur précise, il permet de déterminer un ordonnancement des actions d’un processus. Ainsi sans savoir combien de temps peut prendre une action “A”, il sera néanmoins possible de connaître les actions précédentes à effectuer ainsi que les suivantes.

Les diagrammes d’activités sont en UML particulièrement adaptés à la description des cas d’utilisation. En effet, chaque cas d’utilisation représentant en réalité un regroupement d’actions, ce type de diagramme permettra d’obtenir une vision d’ensemble et ordonnée de ces dernières.

Le principal avantage de ce type de diagramme réside dans le fait d’être simplement intelligible et de ce fait s’adresse à n’importe quelle personne, y compris les néophytes de l’UML. Par ailleurs, la permissivité de modélisation d’un algorithme complet, et intelligible par n’importe qui, pourra permettre par exemple à un client de valider les étapes et le déroulé d’un processus sur une fonctionnalité demandée.

Il faut toutefois rester attentif à l’utilisation des diagrammes d’activités. La polyvalence de cette schématisation entraîne souvent son utilisation excessive. Il faut donc de manière générale préférer l’utiliser pour détailler des opérations complexes, sensibles, ou bien qui présentent une nécessité de validation par un tiers.

## Concept et vocabulaire spécifique

Même s’ils peuvent être aisément compris de la majorité des néophytes, il reste néanmoins important dans le cadre de l’utilisation de l’UML de bien comprendre l’ensemble des notions qu’apportent les diagrammes d’activités. Ainsi voici des explications sur les plus importantes :

- Les **acteurs** représentent des éléments qui interagissent tout au long du processus décrit par le diagramme d’activités. Ils peuvent être physiques ou non, il peut s’agir d’un utilisateur ou bien d’un système informatique. L’utilisation des acteurs est facultative au sein de ce type de diagramme. Lors de l’utilisation d’un ou plusieurs acteur(s) au sein d’un schéma, chacun est identifié sous forme de colonne. Chaque colonne ainsi créée est donc dédiée à y insérer les éléments de diagrammes en lien avec l’acteur concerné. Il n’existe pas de limite en nombre d'acteurs, cependant plus il en a, plus le schéma perd en lisibilité.
- Les **actions** sont les principales composantes d’un diagramme d’activités, elles sont par conséquent obligatoires. Elles représentent l’ensemble des activités qui surviennent au fur et à mesure du processus. Chaque action est représentée dans un rectangle aux bords arrondis au sein duquel le nom de l’action est écrit. Dans le cadre de la réalisation d’un diagramme d’activités qui prend en considération les acteurs, alors les actions peuvent être “triées” en fonction de l’acteur déclencheur.

Il existe également plusieurs **actions spécifiques** : 

    - **L’action d’évènement entrant** permet de représenter la nécessité de recevoir une information pour se réaliser. On la représente de la sorte :