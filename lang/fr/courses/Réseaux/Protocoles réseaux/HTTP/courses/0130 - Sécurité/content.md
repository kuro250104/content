HTTP est utilisé pour les communications sur Internet. Les développeurs d'applications, les fournisseurs d'informations et les utilisateurs doivent donc être conscients des limites de sécurité de HTTP/1.1. Cette discussion ne comprend pas de solutions définitives aux problèmes mentionnés ici, mais elle fait quelques suggestions pour réduire les risques de sécurité.

## Fuite d'informations personnelles

Les clients HTTP sont souvent au courant d'un grand nombre d'informations personnelles telles que le nom de l'utilisateur, sa localisation, son adresse électronique, ses mots de passe, ses clés de chiffrement, etc. Vous devez donc être très prudent pour éviter toute fuite involontaire de ces informations via le protocole HTTP vers d'autres sources.

- Toutes les informations confidentielles doivent être stockées sur le serveur sous forme cryptée.
- Révéler la version spécifique du logiciel du serveur pourrait rendre la machine serveur plus vulnérable aux attaques contre des logiciels connus pour contenir des failles de sécurité.
- Les proxies qui servent de portail à travers un pare-feu de réseau doivent prendre des précautions particulières concernant le transfert des informations d'en-tête qui identifient les hôtes derrière le pare-feu.
- Les informations envoyées dans le champ "From" peuvent entrer en conflit avec les intérêts de l'utilisateur en matière de confidentialité ou avec la politique de sécurité de son site. Elles ne doivent donc pas être transmises sans que l'utilisateur puisse désactiver, activer et modifier le contenu du champ.
- Les clients ne doivent pas inclure un champ d'en-tête Referer dans une requête HTTP (non sécurisée) si la page de référence a été transférée avec un protocole sécurisé.
- Les auteurs de services qui utilisent le protocole HTTP ne doivent pas utiliser de formulaires basés sur le protocole GET pour la soumission de données sensibles, car les données seront alors codées dans l'URL de la demande.

## Attaque basée sur les noms de fichiers et de chemins

Le document doit être limité aux documents renvoyés par les requêtes HTTP pour être uniquement ceux qui ont été prévus par les administrateurs du serveur.

Par exemple, UNIX, Microsoft Windows et d'autres systèmes d'exploitation utilisent '...' comme composant de chemin pour indiquer un niveau de répertoire supérieur au niveau actuel. Sur un tel système, un serveur HTTP DOIT interdire toute construction de ce type dans l'url de la demande, si elle permet d'accéder à une ressource autre que celles prévues pour être accessibles par le serveur HTTP.

## Usurpation du DNS (spoofing)

Les clients qui utilisent le protocole HTTP s'appuient fortement sur le service de nom de domaine et sont donc généralement exposés à des attaques de sécurité basées sur une mauvaise association délibérée d'adresses IP et de noms DNS. Les clients doivent donc être prudents lorsqu'ils supposent la validité permanente d'une association numéro IP/nom DNS.

Si les clients HTTP mettent en cache les résultats des recherches de noms d'hôtes afin d'obtenir une amélioration des performances, ils doivent respecter les informations TTL communiquées par le DNS. Si les clients HTTP ne respectent pas cette règle, ils risquent d'être usurpés lorsque l'adresse IP d'un serveur précédemment consulté change.

## En-têtes de localisation et usurpation d'identité

Si un serveur unique prend en charge plusieurs organisations qui ne se font pas confiance, il DOIT vérifier les valeurs des en-têtes Location et Content Location dans les réponses qui sont générées sous le contrôle desdites organisations pour s'assurer qu'elles ne tentent pas d'invalider des ressources sur lesquelles elles n'ont aucune autorité.

## Références d'authentification

Les clients et agents utilisateurs HTTP existants conservent généralement les informations d'authentification indéfiniment. HTTP/1.1 ne fournit pas de méthode permettant à un serveur de demander aux clients de se débarrasser de ces informations d'identification mises en cache, ce qui constitue un risque important pour la sécurité.

Il existe un certain nombre de solutions pour contourner ce problème. Il est donc recommandé d'utiliser la protection par mot de passe dans les économiseurs d'écran, les délais d'inactivité et d'autres méthodes qui atténuent les problèmes de sécurité inhérents à ce problème.

## Proxies et mise en cache

Les proxies HTTP sont des hommes du milieu et représentent une opportunité pour les attaques de type man-in-the-middle. Les proxies ont accès à des informations liées à la sécurité, à des informations personnelles sur des utilisateurs individuels et des organisations, ainsi qu'à des informations exclusives appartenant aux utilisateurs et aux fournisseurs de contenu.

Les opérateurs de proxys doivent protéger les systèmes sur lesquels ils fonctionnent, comme ils le feraient pour tout système qui contient ou transporte des informations sensibles.

Les proxys de mise en cache offrent des vulnérabilités potentielles supplémentaires, car le contenu du cache représente une cible attrayante pour une exploitation malveillante. Par conséquent, le contenu du cache doit être protégé comme une information sensible.