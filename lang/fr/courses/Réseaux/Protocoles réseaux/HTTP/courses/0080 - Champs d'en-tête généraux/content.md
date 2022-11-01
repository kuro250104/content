Les champs d'en-tête HTTP fournissent des informations obligatoires sur la demande ou la réponse, ou sur l'objet envoyé dans le corps du message. Il existe quatre types d'en-têtes de message HTTP :

- **General-header (en-tête général)** : Ces champs d'en-tête ont une applicabilité générale pour les messages de demande et de réponse.
- **En-tête de demande du client** : Ces champs d'en-tête ne s'appliquent qu'aux messages de demande.
- **En-tête de réponse du serveur** : Ces champs d'en-tête ne s'appliquent qu'aux messages de réponse.
- **Entity-header (en-tête d'entité)** : Ces champs d'en-tête définissent des méta-informations sur le corps de l'entité ou, si aucun corps n'est présent, sur la ressource identifiée par la demande.

## Cache-Control

Le champ Cache-Control general-header est utilisé pour spécifier les directives qui DOIVENT être respectées par tous les systèmes de mise en cache. La syntaxe est la suivante :

```http
Cache-Control : cache-request-directive|cache-response-directive
```

Un client ou un serveur HTTP peut utiliser l'en-tête général Cache-control pour spécifier des paramètres pour le cache ou pour demander certains types de documents au cache. Les directives de mise en cache sont spécifiées dans une liste séparée par des virgules. Par exemple :

```http
Cache-control: no-cache
```

Le tableau suivant énumère les principales directives de demande de cache qui peuvent être utilisées par le client dans sa demande HTTP :

- **no-cache** - Un cache ne doit pas utiliser la réponse pour satisfaire une demande ultérieure sans revalidation réussie auprès du serveur d'origine.
- **no-store** - Le cache ne doit rien stocker concernant la demande du client ou la réponse du serveur.
- **max-age = secondes** - Indique que le client est prêt à accepter une réponse dont l'âge n'est pas supérieur à la durée spécifiée en secondes.
- **max-stale [ = secondes]** - Indique que le client est disposé à accepter une réponse qui a dépassé son délai d'expiration. Si des secondes sont données, le délai d'expiration ne doit pas être supérieur à ce temps.
- **min-fresh = secondes** - Indique que le client est disposé à accepter une réponse dont la durée de vie de fraîcheur n'est pas inférieure à son âge actuel plus le temps spécifié en secondes.
- **no-transform** - Ne convertit pas le corps de l'entité.
- **only-if-cached** - Ne récupère pas de nouvelles données. Le cache peut envoyer un document seulement s'il est dans le cache, et ne doit pas contacter le serveur d'origine pour voir si une copie plus récente existe.

Les directives de réponse de cache suivantes sont importantes et peuvent être utilisées par le serveur dans sa réponse HTTP :

- **public** - Indique que la réponse peut être mise en cache par n'importe quel cache.
- **privé** - Indique que tout ou partie du message de réponse est destiné à un seul utilisateur et ne doit pas être mis en cache par un cache partagé.
- **no-cache** - Un cache ne doit pas utiliser la réponse pour satisfaire une demande ultérieure sans une nouvelle validation réussie auprès du serveur d'origine.
- **no-store** - Le cache ne doit rien stocker concernant la demande du client ou la réponse du serveur.
- **no-transform** - Ne convertit pas le corps de l'entité.
- **must-revalidate** - Le cache doit vérifier l'état des documents périmés avant de les utiliser et les documents expirés ne doivent pas être utilisés.
- **proxy-revalidate** - La directive proxy-revalidate a la même signification que la directive must-revalidate, sauf qu'elle ne s'applique pas aux caches d'agents utilisateurs non partagés.
- **max-age = secondes** - Indique que le client est prêt à accepter une réponse dont l'âge n'est pas supérieur à la durée spécifiée en secondes.
- **s-maxage = secondes** - L'âge maximum spécifié par cette directive remplace l'âge maximum spécifié par la directive max-age ou l'en-tête Expires. La directive s-maxage est toujours ignorée par un cache privé.

## Connexion

Le champ Connection **general-header** permet à l'expéditeur de spécifier des options qui sont souhaitées pour cette connexion particulière et qui ne doivent pas être communiquées par des proxies sur d'autres connexions. Voici la syntaxe simple pour utiliser l'en-tête de connexion :

```http
Connection : "Connection"
```

HTTP/1.1 définit l'option de connexion "**close**" pour que l'expéditeur signale que la connexion sera fermée à la fin de la réponse. Par exemple :

```http
Connection: close
```

Par défaut, HTTP 1.1 utilise des connexions persistantes, où la connexion ne se ferme pas automatiquement après une transaction. Le protocole HTTP 1.0, quant à lui, n'offre pas de connexions persistantes par défaut. Si un client 1.0 souhaite utiliser des connexions persistantes, il utilise le paramètre keep-alive comme suit :

```http
Connection: keep-alive
```

## Date


Tous les timbres date/heure HTTP DOIVENT être représentés en temps moyen de Greenwich (GMT), sans exception. Les applications HTTP sont autorisées à utiliser l'une des trois représentations suivantes de l'horodatage :

```http
Sun, 06 Nov 2020 08:49:37 GMT  ; RFC 822, updated by RFC 1123
Sunday, 06-Nov-20 08:49:37 GMT ; RFC 850, obsoleted by RFC 1036
Sun Nov  6 08:49:37 2020       ; ANSI C's asctime() format
```

Ici, le premier format est celui qui est le plus privilégié.

## Pragma

Le champ **Pragma** general-header est utilisé pour inclure des directives spécifiques à l'implémentation qui peuvent s'appliquer à n'importe quel destinataire le long de la chaîne requête/réponse. Par exemple :

```http
Pragma: no-cache
```

La seule directive définie dans le HTTP/1.0 est la directive no-cache et est maintenue dans le HTTP 1.1 pour une compatibilité descendante. Aucune nouvelle directive Pragma ne sera définie dans le futur.

## Trailer

La valeur du champ général Trailer indique que l'ensemble donné de champs d'en-tête est présent dans la fin d'un message codé avec un codage de transfert par morceaux. Voici la syntaxe du champ d'en-tête Trailer :

```http
Trailer : field-name
```

Les champs d'en-tête de message énumérés dans le champ d'en-tête de fin de message ne doivent pas inclure les champs d'en-tête suivants :

- Transfer-Encoding
- Content-Length
- Trailer

## Transfer-Encoding

Le champ d'en-tête général **Transfer-Encoding** indique quel type de transformation a été appliqué au corps du message afin de le transférer en toute sécurité entre l'expéditeur et le destinataire. Ce n'est pas la même chose que le codage du contenu car les codages de transfert sont une propriété du message et non du corps de l'entité. La syntaxe du champ d'en-tête Transfer-Encoding est la suivante :

```http
Transfer-Encoding: chunked
```

Toutes les valeurs de codage de transfert sont insensibles à la casse.

## Mise à niveau

L'en-tête général **Upgrade** permet au client de spécifier les protocoles de communication supplémentaires qu'il prend en charge et qu'il souhaite utiliser si le serveur juge approprié de changer de protocole. Par exemple :

```http
Upgrade: HTTP/2.0, SHTTP/1.3, IRC/6.9, RTA/x11
```

Le champ d'en-tête "**Upgrade**" est destiné à fournir un mécanisme simple pour la transition de HTTP/1.1 à un autre protocole incompatible.

## Via

L'en-tête général **Via** doit être utilisé par les passerelles et les serveurs mandataires pour indiquer les protocoles intermédiaires et les destinataires. Par exemple, un message de demande peut être envoyé par un agent utilisateur HTTP/1.0 à un proxy interne portant le nom de code "fred", qui utilise HTTP/1.1 pour transmettre la demande à un proxy public à nowhere.com, qui complète la demande en la transmettant au serveur d'origine à www.ics.uci.edu. La demande reçue par www.ics.uci.edu comporterait alors le champ d'en-tête Via suivant :

```http
Via: 1.0 fred, 1.1 nowhere.com (Apache/1.1)
```

## Avertissement

L'en-tête général Warning est utilisé pour transporter des informations supplémentaires sur l'état ou la transformation d'un message, qui pourraient ne pas être reflétées dans le message. Une réponse peut comporter plus d'un en-tête Warning.

```http
Warning : warn-code SP warn-agent SP warn-text SP warn-date
```