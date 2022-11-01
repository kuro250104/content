Lors de l’utilisation de l’UML dans le cadre d’une documentation, il est courant de ne pas savoir comment organiser ledit document. Ainsi le modèle de vue architecturale 4+1 offre les avantages de classifier les diagrammes tout en proposant une solution de structure de documentation pragmatique, axée sur la typologie de lecteurs potentiels.

## Le modèle de vue architecturale 4+1

Le modèle de vue architecturale 4+1 a été proposé par Philippe Kruchten en 1995 dans le but de décrire une architecture de développement de systèmes depuis plusieurs points de vue tels que les utilisateurs finaux, les développeurs, les chefs de projet ou encore les ingénieurs système.

Comme la dénomination de son modèle architecturale l’indique, Kruchten identifie donc 5 points de vue différents :

- **La Vue Logique** concerne l’ensemble des fonctionnalités que le système fournit aux utilisateurs finaux.
- **La Vue Processus** concerne les aspects dynamiques d’un système en expliquant ses processus. Elle explique notamment comment les processus communiquent entre eux afin de comprendre le comportement d’exécution d’un système.
- **La Vue de Développement** illustre un système du point de vue d’un programmateur et concerne la gestion des logiciels et applications. Elle est également nommée “vue d’implémentation”.
- **La Vue Physique** décrit le système du point de vue d’un ingénieur système. Elle représente donc la topologie des composants logiciels sur la couche physique ainsi que leurs relations. Cette vue est également nommée “vue de déploiement”.
- **Les Scénarios** décrivent quant à eux l’architecture de manière illustrée grâce à un ensemble de cas d’utilisations ou de scénarios, qui deviennent une cinquième vue. Les scénarios décrivent des séquences d’interactions entre les objets et les processus. Ils sont notamment utilisés pour identifier les éléments architecturaux et pour illustrer et valider sa conception. Ils servent également de référence pour la réalisation de tests d’un prototype d’architecture.

## Application du modèle 4+1 à la classification des diagrammes UML

La vue **Logique** peut être dite “**structurelle**”. Elle représente les aspects statiques de la structure d’un projet et apporte les éléments permettant la mise en oeuvre d’une solution répondant aux besoins fonctionnels des utilisateurs finaux. Cet aspect sera développé grâce à différents diagrammes : 

- Diagramme de contexte
- Diagramme de packages
- Diagramme de classes
- Diagramme d’objets
- Diagramme de structure composite
- Diagramme de profil

La vue **Processus** peut être apparentée à un aspect “**comportemental**”. Elle va permettre de mettre en évidence les aspects dynamiques du système en détaillant les interactions et les collaborations entre les différents composants du système. Cet aspect sera développé grâce à différents diagrammes : 

- Diagramme de séquence
- Diagramme de communication
- Diagramme d’activité
- Diagramme d’états-transition
- Diagramme de temps
- Diagramme de vues générale d’interactions

La vue **Développement** représente la phase **d’implémentation** du système. Elle permet d’aborder les aspects structurels et comportementaux de la solution grâce aux diagrammes suivants : 

- Diagramme de packages
- Diagramme de Composants

La vue **Physique** est assimilée à **l’environnement** sur lequel le système va fonctionner. Cette partie va aborder la structure et le comportement de la partie matérielle dans laquelle il va évoluer. Cette vue sera conditionnée à une topologie de matériel mis en place pour le système. Cet aspect se décrit grâce au diagramme de déploiement uniquement.

Enfin la vue **Scénario** est entièrement dédiée aux utilisateurs finaux. Elle doit présenter l’ensemble des besoins des utilisateurs finaux à intégrer dans le système. Deux diagrammes serviront sur ce point : 

- Diagramme de cas d’utilisation
- Diagramme d’activité