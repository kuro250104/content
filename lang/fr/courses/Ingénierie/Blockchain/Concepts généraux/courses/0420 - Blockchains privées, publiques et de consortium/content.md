Lorsque le bitcoin a été lancé, il a jeté les bases d'une industrie tournant autour de la technologie qui sous-tend le protocole : la blockchain. Des innovateurs enthousiastes ont maintenant découvert le potentiel de cette technologie et explorent ses applications dans tous les secteurs imaginables.

Le bitcoin est ce que l'on appelle une crypto-monnaie, c'est-à-dire une forme de monnaie numérique qui n'est pas contrôlée par une seule entité. Au lieu de cela, il utilise une combinaison de technologie de base de données distribuée, d'incitations financières et de techniques cryptographiques pour permettre à un vaste écosystème de se coordonner sans dirigeants ni administrateurs.

La structure de données utilisée par le réseau Bitcoin a suscité un grand intérêt au cours des dix années et plus qui ont suivi sa création. Aujourd'hui, la technologie blockchain est expérimentée dans des secteurs allant de la finance et des chaînes d'approvisionnement aux systèmes juridiques et au gouvernement.

Au cas où vous auriez manqué notre guide du débutant sur la technologie blockchain : une blockchain est une structure de données simple dont les entrées ne peuvent pas être modifiées, mais seulement étendues. Il peut être utile de l'imaginer comme une feuille de calcul, où chaque cellule renvoie à la précédente, de sorte que toute tentative de modification d'une cellule antérieure serait immédiatement apparente. En général, une blockchain stocke des informations sur les transactions financières, mais elle peut être utilisée avec n'importe quel type de données numériques.

Pour poursuivre l'analogie avec notre feuille de calcul, le document lui-même serait détenu par de nombreuses parties. Chacune d'entre elles exécute un logiciel spécialisé sur son appareil, qui se connecte à d'autres appareils utilisant le même logiciel afin que tous les participants soient en possession d'une base de données actualisée. 

Il n'y a pas de source centrale à partir de laquelle les participants obtiennent ces informations (le réseau est distribué). Cela signifie que la propagation de l'information est plus lente, mais cela rend le réseau plus solide en termes de sécurité et de redondance.

Dans l'article suivant, nous allons examiner trois types de blockchains : les chaînes privées, publiques et de consortium. Avant cela, rappelons quelques caractéristiques clés que les trois ont en commun :

- **Un registre à annexes seulement** - pour être qualifié de blockchain, un système doit suivre la structure de la chaîne de blocs, dans laquelle chaque bloc est lié au dernier. Si notre blockchain est la collection de cellules de notre tableur, les blocs sont les cellules individuelles.
- **Un réseau de pairs** - chaque participant du réseau détient une copie de la blockchain. Ces participants sont appelés "nœuds" et interagissent de manière "peer-to-peer".
- **Un mécanisme de consensus** - il doit exister un mécanisme permettant aux nœuds de s'accorder sur l'exactitude des transactions propagées sur le réseau, afin de garantir qu'aucune donnée erronée n'est inscrite sur la chaîne.

Le tableau ci-dessous résume certaines des principales différences.

| --- | **Blockchain Publique** | **Blockchain Privée** | **Blockchain Consortium** |
| --- | --- | --- | --- |
| **Sans autorisation ?** | Oui | Non | Non |
| **Qui peut lire ?** | Toute personne | Utilisateurs invités uniquement | Dépend |
| **Qui peut écrire ?** | Toute personne | Participants approuvés | Participants approuvés |
| **Propriété** | Personne | Entité unique | Plusieurs entités |
| **Participants connus ?** | Non | Oui | Oui |
| **Vitesse de transaction** | Lent | Rapide | Rapide |

## Blockchains publiques

Si vous avez utilisé une crypto-monnaie récemment, il y a de fortes chances que vous ayez interagi avec une blockchain publique. Celles-ci constituent l'écrasante majorité des grands livres distribués qui existent aujourd'hui. Nous les qualifions de publiques parce que tout le monde peut voir les transactions qui ont lieu et qu'il suffit de télécharger le logiciel nécessaire pour y adhérer.

Nous utilisons aussi souvent le terme "sans permission" à côté de public. Aucun gardien ne peut s'opposer à la participation, et tout le monde peut s'engager dans le mécanisme de consensus (par exemple, en faisant du minage ou du jalonnement). Comme tout le monde est libre de participer et d'être récompensé pour son rôle dans l'obtention du consensus, on peut s'attendre à voir une topologie hautement décentralisée sur un réseau établi autour d'une chaîne publique.

Dans le même ordre d'idées, on peut s'attendre à ce qu'une blockchain publique soit plus résistante à la censure qu'une blockchain privée (ou semi-privée). Comme tout le monde peut rejoindre le réseau, le protocole doit intégrer certains mécanismes pour empêcher les acteurs malveillants de prendre l'avantage de manière anonyme.

L'approche axée sur la sécurité des chaînes publiques s'accompagne toutefois de compromis sur le plan des performances. Beaucoup rencontrent des obstacles de mise à l'échelle et le débit est relativement faible. En outre, il peut être difficile d'apporter des modifications à un réseau sans le faire éclater, car il est rare que tous les participants soient d'accord sur les changements proposés.

## Blockchains privées

Contrairement à la nature sans permission des blockchains publiques, les blockchains privées établissent des règles pour déterminer qui peut voir et écrire sur la chaîne (ce sont des environnements avec permission). Ce ne sont pas des systèmes décentralisés, car il existe une hiérarchie claire en matière de contrôle. Elles sont toutefois distribuées, dans la mesure où de nombreux nœuds conservent une copie de la chaîne sur leurs machines.

Les chaînes privées sont mieux adaptées aux entreprises, qui souhaitent profiter des propriétés de la blockchain sans rendre leur réseau accessible à l'extérieur.

La preuve de travail est un gaspillage, mais elle s'est avérée nécessaire dans un environnement ouvert, étant donné le modèle de sécurité. Dans une blockchain privée, cependant, les menaces que le PoW écarte ne sont pas aussi préjudiciables - l'identité de chaque participant est connue et la gouvernance est directe. 

Un algorithme plus efficace, dans ce cas, est un algorithme avec des validateurs désignés, qui sont des nœuds sélectionnés pour prendre en charge certaines fonctions de validation des transactions. En général, cela implique un assortiment de nœuds qui doivent approuver chaque bloc. Si des nœuds commencent à agir de manière malveillante, ils peuvent être rapidement appréhendés et retirés du réseau. Étant donné le contrôle descendant de la blockchain, il sera assez facile de coordonner un renversement.

## Blockchains de consortium

La blockchain de consortium se situe à la frontière entre les chaînes publiques et privées, combinant des éléments des deux. La différence la plus notable par rapport aux deux systèmes s'observe au niveau du consensus. Au lieu d'un système ouvert où tout le monde peut valider les blocs ou d'un système fermé où une seule entité désigne les producteurs de blocs, une chaîne de consortium voit une poignée de parties de même puissance fonctionner comme validateurs.

À partir de là, les règles du système sont flexibles : la visibilité de la chaîne peut être limitée aux validateurs, visible par les personnes autorisées, ou par tous. Si les validateurs parviennent à un consensus, les changements peuvent être facilement mis en œuvre. Quant au fonctionnement de la blockchain, si un certain seuil de ces parties se comporte honnêtement, le système ne rencontrera aucun problème.

Une blockchain de consortium serait plus avantageuse dans un contexte où plusieurs organisations opèrent dans le même secteur et ont besoin d'un terrain commun pour effectuer des transactions ou relayer des informations. Rejoindre un consortium de ce type pourrait être bénéfique pour une organisation, car cela lui permettrait de partager des informations sur son secteur avec d'autres acteurs.

## Laquelle est la meilleure ?

Fondamentalement, les blockchains publiques, privées et de consortium ne sont pas opposées - ce sont des technologies différentes :

- Les chaînes publiques bien conçues ont tendance à exceller en matière de résistance à la censure, au détriment de la vitesse et du débit. Elles sont idéales pour obtenir des garanties de sécurité accrues sur les règlements de transactions (ou contrats intelligents).
- Une chaîne privée peut donner la priorité à la vitesse du système, car elle n'a pas à se préoccuper de points centraux de défaillance comme c'est le cas des blockchains publiques. Elles sont idéalement déployées dans des situations où un individu ou une organisation doit garder le contrôle, et les informations rester privées.
- Les chaînes de consortium atténuent certains des risques de contrepartie d'une chaîne privée (en supprimant le contrôle centralisé), et un nombre plus restreint de nœuds leur permet généralement d'être beaucoup plus efficaces qu'une chaîne publique. Les consortiums sont susceptibles de séduire les organisations qui souhaitent rationaliser la communication entre elles.

## Conclusion

Il existe une myriade d'options de blockchain pour les particuliers et les entreprises qui se livrent à diverses activités. Même au sein des catégories de blockchains publiques, privées et de consortium, il existe un certain nombre de subtilités qui conduisent à des expériences différentes pour les utilisateurs. En fonction du cas d'utilisation, les utilisateurs devront choisir celle qui est la mieux adaptée pour atteindre leurs propres objectifs.