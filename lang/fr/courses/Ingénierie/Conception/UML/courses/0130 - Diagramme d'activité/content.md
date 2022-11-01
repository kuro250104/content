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

![Action d’évènement entrant](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image1.png)

    - **L’action d’évènement sortant** permet de représenter l’émission d’une ou plusieurs information(s) à l’issue de sa réalisation. Elle est représentée comme suit :

![Action d’évènement sortant](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image4.png)

    - **L’action de délai** permet d’inclure un délai temporel avant la poursuite du flux. Elle est représentée par une schématisation rappelant un sablier :

![Action de délai](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image3.png)

- Le **début** du diagramme d’activité est lui aussi obligatoire. Il ne peut y avoir qu’un seul début, et celui-ci est représenté par un rond noir. Il peut être agrémenté d’un commentaire (en utilisant le symbole UML correspondant) afin de spécifier certaines conditions d’entrée dans le diagramme.
- Les **flux** sont représentés par des flèches. Ils permettent de représenter l’ordre d’exécution des actions et sont par conséquent obligatoires. Une flèche dite “entrante” marque le début d’une activité tandis qu’une autre dite “sortante” marque la direction du flux vers la prochaine étape.
- Les **décisions** sont des éléments permettant d’inclure des conditions au sein du diagramme. Ces décisions sont représentées par des losanges. La condition est généralement écrite à l’intérieur du losange, et au moins deux flux sortants sont présents. Attention, il peut quelquefois y avoir davantage de deux flux sortants. Chaque flux sortant dispose d’une annotation textuelle représentant une potentielle réponse à la condition du losange. Prenons le temps d’un exemple :
![décisions](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image12.png)
L’activité “A” est terminée. Le flux se dirige donc vers la condition. Si la condition n’est pas remplie (du fait du “non”), alors le flux est redirigé vers l’activité “A”. Si la condition est remplie (du fait du “oui”), alors le flux continue son chemin vers l’activité “B”.
- Les **ponts de contrôle de flux** sont des éléments permettant de séparer ou bien de fusionner différents flux. Ils sont représentés par un trait noir épais et permettent soit de réceptionner plusieurs flux entrants, soit d’envoyer plusieurs flux sortants, soit les deux. De la sorte, à partir d’un flux unique, plusieurs peuvent être créés. Réciproquement, plusieurs flux peuvent se regrouper en un seul grâce à un pont de contrôle de flux.
- Il existe enfin **deux type de fin** à un diagramme d’activités :
    - La **fin d’un flux spécifique** est représentée par une croix dans un cercle vide. Elle est utilisée lorsqu’un flux à été créé par un pont de contrôle et que celui-ci se termine prématurément (ou du moins que d’autres actions peuvent exister après sa fin, dans un flux différent).
    - la **fin du flux principal** est quand à elle schématisée par un rond noir entouré d’un cercle noir également. On entend ici “flux principal” comme étant le flux le plus long du diagramme, sa fin représentant donc le chemin le plus long du diagramme. Cette fin représente ainsi la fin de la lecture du diagramme dans sa globalité.

## Formes et symboles

| Symboles | Signification |
| --- | --- |
| ![Symbole de début du diagramme d’activité](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image15.png) | Symbole de début du diagramme d’activité |
| ![Symbole de fin du flux principal](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image5.png) | Symbole de fin du flux principal |
| ![Symbole de fin d’un flux spécifique](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image11.png) | Symbole de fin d’un flux spécifique |
| ![Symbole de délai d’action](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image3.png) | Symbole de délai d’action |
| ![Symbole de représentation d’une activité](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image16.png) | Symbole de représentation d’une activité |
| ![Symbole de représentation d’une condition](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image14.png) | Symbole de représentation d’une condition |
| ![Symbole d’action d'événement sortant](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image4.png) | Symbole d’action d'événement sortant |
| ![Symbole d’action d'événement entrant](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image1.png) | Symbole d’action d'événement entrant |
| ![Symbole de commentaire](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image13.png) | Symbole de commentaire |
| ![Expression d’une condition](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image2.png) | Expression d’une condition |
| ![Symbole de flux](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image7.png) | Symbole de flux |
| ![Symbole de pont de contrôle de flux d’émission](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image6.png) | Symbole de pont de contrôle de flux d’émission de plusieurs flux sortants à partir d’un seul flux entrant |
| ![Symbole de pont de contrôle de flux de regroupement](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image9.png) | Symbole de pont de contrôle de flux de regroupement de plusieurs flux entrants ne générant qu’un seul flux sortant |
| ![Colonne de représentation d’un acteur](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image8.png) | Colonne de représentation d’un acteur. Tout ce que cette colonne contiendra ne concerne par conséquent que l’acteur qui y est décrit tout en haut - généralement par son simple nom. |

## Démarche de création

Malgré les apparences, il peut s’avérer compliqué de réaliser un diagramme d’activité. Si le concept et sa représentation sont souvent simples et parlants, une bonne organisation dans la réalisation sera souvent gage de bonne qualité. 

De manière générale, la réalisation de ce type de schéma est faite quasiment sans réflexion - ou du moins très peu - et c’est surtout cet aspect là qui crée des difficultés : au fur et à mesure de l’avancement, il n’est pas rare de constater des oublis, et c’est souvent la correction de ceux-ci qui entraîne un temps de réalisation parfois considérable. Afin de limiter au mieux les pertes de temps, voici un “workflow” qui doit normalement permettre de réaliser des diagrammes plus sereinement.

- Première étape : faut-il inclure les différents acteurs au sein du diagramme ? Cette question semble anodine, et pourtant le fait de devoir réorganiser un schéma si vous n’avez pas préparé de colonnes en amont peut être extrêmement chronophage ! Si les acteurs doivent être intégrés au diagramme, il faut s’assurer de les avoir identifiés correctement dès le début !
- Il faut ensuite dresser une liste de l’ensemble des actions. Cette liste doit être la plus exhaustive possible. Moins il y aura d’actions à rajouter au fur et à mesure de la réalisation du schéma, plus vite ce dernier sera réalisé.
- Une fois la liste d’action obtenue, il est nécessaire de les ordonner. La classification par ordre chronologique doit permettre normalement d’arriver à un semblant de plan cohérent pour le diagramme d’activité. Par ailleurs, la présentation sous forme de liste permet également de commencer à identifier certaines séparation de flux. Lorsque plusieurs actions sont liées à une seule et même action, il est fort probable qu’il faille intégrer un flux spécifique.
- Maintenant que ce “plan” est ordonné, il faut se questionner quant au passage d’une action à une autre. Il est donc nécessaire de prendre chacune des actions et réfléchir à de potentielles conditions de passage à l’action suivante. Cette étape doit normalement permettre d’affiner l’identification des séparations de flux. Lors de l’identification des conditions, il n’est pas rare de “découvrir” de nouvelles actions à réaliser. C’est ici qu’il faut donc penser à bien les ajouter dans le plan initial afin de ne pas les oublier !
- Il ne reste plus qu’à traiter l’ensemble des actions qui ne disposent pas de condition. Pour chacune d’entre elles, il suffit de déterminer laquelle correspond à l’étape suivante.
- Si les acteurs doivent être représentés dans le diagramme, il convient pour chaque action de déterminer quel est l’acteur réalisant ladite action.
- Réaliser le diagramme !

## Exemples

### Réalisation d’un diagramme d’activités d’un système d’authentification en se basant sur la démarche de création proposée

#### Identification des acteurs

Pour la première étape, nous allons partir du principe que nous avons 3 acteurs :

- l’utilisateur : sera la personne qui va utiliser le système d’authentification
- le système : sera le code qui va gérer le traitement de l’ensemble des données
- une API d’envoie de mail : permettra d’envoyer des mails pour les différents besoins exposés plus bas.

#### Identification des actions

Voici ensuite une liste d’actions, non organisée : 

- début
- fin
- inscription
- connexion
- envoie d’un lien de validation d’inscription valable 24h uniquement par mail
- validation d’inscription
- Vérification de l’existence d’un token de connexion
- création d’un token de connexion
- affichage de la page de connexion
- affichage de la page d’inscription
- soumission du formulaire
- validation du formulaire

#### Organisation des actions

Passons maintenant à l’organisation de ces actions :

- début
- Vérification de l’existence d’un token de connexion
- inscription
  - affichage de la page d’inscription
  - soumission du formulaire
  - validation du formulaire
  - envoie d’un lien de validation d’inscription valable 24h uniquement par mail
  - validation d’inscription
- connexion
  - affichage de la page de connexion
  - soumission du formulaire
  - validation du formulaire
  - création d’un token de connexion
- fin

#### Identification des conditions

A partir de ce point, nous avons donc normalement identifié toutes les actions nécessaires à la réalisation de notre diagramme, ainsi que les acteurs qui y seront présents. Il nous faut maintenant identifier s’il existe des conditions pour passer d’une étape à l’autre pour chacune des actions listées.

Reprenons la liste ci-dessus, et indiquons en *italic* par exemple ces conditions. Par souci de clarté et de simplicité de lecture, nous utiliserons une liste numérotée :

1. début
2. Vérification de l’existence d’un token de connexion *Si un token existe, passer directement à l’étape 5. Si l’utilisateur n’a pas de compte, passer à l’étape 3. Si l’utilisateur a déjà un compte, passer à l’étape 4.*
3. inscription
   1. affichage de la page d’inscription
   2. soumission du formulaire
   3. validation du formulaire *Si les champs du formulaire sont valides, alors on passe à l’étape suivante (3.4), sinon on revient à l’étape précédente (3.2)*
   4. envoie d’un lien de validation d’inscription valable 24h uniquement par mail *Si le lien est déclenché, alors on passe à l’étape suivante (3.5), si au bout de 24h le lien envoyé par mail n’a toujours pas été utilisé, alors l’inscription est annulée, et le flux est interrompu.*
   5. validation d’inscription
4. connexion
   1. affichage de la page de connexion
   2. soumission du formulaire
   3. validation du formulaire *Si les champs sont correctement remplis et que les informations de connexion sont bonnes, alors on passe à l’étape suivante (4.4), sinon on recommence la connexion (4.1).*
   4. création d’un token de connexion *Si le token est créé correctement, alors on retourne à l’étape (2).*
5. fin

#### Identification des flux entre actions

Une fois cette liste dressée, il nous faut passer à l’étape 5 de la démarche de création proposée : inscrire les étapes suivant chacune des actions ne disposant pas de conditions (ici en rouge). Pour plus de clarté, nous représenterons ces éléments en **gras**.

1. début **passage à l’étape 2**
2. Vérification de l’existence d’un token de connexion *Si un token existe, passer directement à l’étape 5. Si l’utilisateur n’a pas de compte, passer à l’étape 3. Si l’utilisateur a déjà un compte, passer à l’étape 4.*
3. inscription **passage à l’étape 3.1**
   1. affichage de la page d’inscription **passage à l’étape 3.2**
   2. soumission du formulaire **passage à l’étape 3.3**
   3. validation du formulaire *Si les champs du formulaire sont valides, alors on passe à l’étape suivante (3.4), sinon on revient à l’étape précédente (3.2)*
   4. envoie d’un lien de validation d’inscription valable 24h uniquement par mail *Si le lien est déclenché, alors on passe à l’étape suivante (3.5), si au bout de 24h le lien envoyé par mail n’a toujours pas été utilisé, alors l’inscription est annulée, et le flux est interrompu.*
   5. validation d’inscription **passage à l’étape 4**
4. connexion **passage à l’étape 4.1**
   1. affichage de la page de connexion **passage à l’étape 4.2**
   2. soumission du formulaire **passage à l’étape 4.3**
   3. validation du formulaire *Si les champs sont correctement remplis et que les informations de connexion sont bonnes, alors on passe à l’étape suivante (4.4), sinon on recommence la connexion (4.1).*
   4. création d’un token de connexion **retour à l’étape 2**
5. fin

#### Identification des acteurs de chaque action

Ayant opté pour l’utilisation d’acteurs au sein de notre diagramme d’activités, il nous reste à réaliser l’étape (6) de la démarche de création. Nous identifierons les acteurs entre crochets au début de chaque étape de la sorte : ```[acteur]```.

1. ```[system]``` début **passage à l’étape 2**
2. ```[system]``` Vérification de l’existence d’un token de connexion *Si un token existe, passer directement à l’étape 5. Si l’utilisateur n’a pas de compte, passer à l’étape 3. Si l’utilisateur a déjà un compte, passer à l’étape 4.*
3. ```[system]``` inscription **passage à l’étape 3.1**
   1. ```[system]``` affichage de la page d’inscription **passage à l’étape 3.2**
   2. ```[utilisateur]``` soumission du formulaire **passage à l’étape 3.3**
   3. ```[system]``` validation du formulaire *Si les champs du formulaire sont valides, alors on passe à l’étape suivante (3.4), sinon on revient à l’étape précédente (3.2)*
   4. ```[API]``` envoie d’un lien de validation d’inscription valable 24h uniquement par mail *Si le lien est déclenché, alors on passe à l’étape suivante (3.5), si au bout de 24h le lien envoyé par mail n’a toujours pas été utilisé, alors l’inscription est annulée, et le flux est interrompu.*
   5. ```[system]``` validation d’inscription **passage à l’étape 4**
4. ```[system]``` connexion **passage à l’étape 4.1**
   1. ```[system]``` affichage de la page de connexion **passage à l’étape 4.2**
   2. ```[utilisateur]``` soumission du formulaire **passage à l’étape 4.3**
   3. ```[system]``` validation du formulaire *Si les champs sont correctement remplis et que les informations de connexion sont bonnes, alors on passe à l’étape suivante (4.4), sinon on recommence la connexion (4.1).*
   4. ```[system]``` création d’un token de connexion **retour à l’étape 2**
5. ```[system]``` fin

#### Réalisation du diagramme d’activités

![Diagramme d'activité représentant le déroulé présenté précédemment](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0130%20-%20Diagramme%20d'activit%C3%A9/images/image10.jpg)