HTTP est généralement utilisé pour les systèmes d'information distribués, où les performances peuvent être améliorées par l'utilisation de caches de réponses. Le protocole HTTP/1.1 comprend un certain nombre d'éléments destinés à faire fonctionner la mise en cache.

L'objectif de la mise en cache dans le protocole HTTP/1.1 est d'éliminer la nécessité d'envoyer des demandes dans de nombreux cas, et d'éliminer la nécessité d'envoyer des réponses complètes dans de nombreux autres cas.

Les mécanismes de base de la mise en cache dans HTTP/1.1 sont des directives implicites aux caches où le serveur spécifie les délais d'expiration et les validateurs. Nous utilisons l'en-tête **Cache-Control** à cette fin.

L'en-tête **Cache-Control** permet à un client ou à un serveur de transmettre une variété de directives dans les demandes ou les réponses. Ces directives remplacent généralement les algorithmes de mise en cache par défaut. Les directives de mise en cache sont spécifiées dans une liste séparée par des virgules. Par exemple :

```http
Cache-control: no-cache
```

Les directives de demande de cache suivantes peuvent être utilisées par le client dans sa demande HTTP :

- **no-cache** - Un cache ne doit pas utiliser la réponse pour satisfaire une demande ultérieure sans revalidation réussie auprès du serveur d'origine.
- **no-store** - Le cache ne doit rien stocker concernant la demande du client ou la réponse du serveur.
- **max-age = seconds** - Indique que le client est prêt à accepter une réponse dont l'âge n'est pas supérieur à la durée spécifiée en secondes.
- **max-stale [ = seconds ]** - Indique que le client est disposé à accepter une réponse qui a dépassé son délai d'expiration. Si des secondes sont données, le délai d'expiration ne doit pas être supérieur à ce temps.
- **min-fresh = seconds** - Indique que le client est disposé à accepter une réponse dont la durée de vie de fraîcheur n'est pas inférieure à son âge actuel plus le temps spécifié en secondes.
- **no-transform** - Ne convertit pas le corps de l'entité.
- **only-if-cached** - Ne récupère pas de nouvelles données. Le cache peut envoyer un document seulement s'il est dans le cache, et ne doit pas contacter le serveur d'origine pour voir si une copie plus récente existe.

Les directives de réponse de cache suivantes peuvent être utilisées par le serveur dans sa réponse HTTP :

- **public** - Indique que la réponse peut être mise en cache par n'importe quel cache.
- **private** - Indique que tout ou partie du message de réponse est destiné à un seul utilisateur et ne doit pas être mis en cache par un cache partagé.
- **no-cache** - Un cache ne doit pas utiliser la réponse pour satisfaire une demande ultérieure sans une nouvelle validation réussie auprès du serveur d'origine.
- **no-store** - Le cache ne doit rien stocker concernant la demande du client ou la réponse du serveur.
- **no-transform** - Ne convertit pas le corps de l'entité.
- **must-revalidate** - Le cache doit vérifier l'état des documents périmés avant de les utiliser et les documents expirés ne doivent pas être utilisés.
- **proxy-revalidate** - La directive proxy-revalidate a la même signification que la directive must-revalidate, sauf qu'elle ne s'applique pas aux caches d'agents utilisateurs non partagés.
- **max-age = seconds** - Indique que le client est prêt à accepter une réponse dont l'âge n'est pas supérieur à la durée spécifiée en secondes.
- **s-maxage = seconds** - L'âge maximum spécifié par cette directive remplace l'âge maximum spécifié par la directive max-age ou l'en-tête Expires. La directive s-maxage est toujours ignorée par un cache privé.