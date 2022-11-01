Les champs d'en-tête HTTP fournissent des informations obligatoires sur la demande ou la réponse, ou sur l'objet envoyé dans le corps du message. Il existe quatre types d'en-têtes de message HTTP :

- **General-header (en-tête général)** : Ces champs d'en-tête ont une applicabilité générale pour les messages de demande et de réponse.
- **En-tête de demande du client** : Ces champs d'en-tête ne s'appliquent qu'aux messages de demande.
- **En-tête de réponse du serveur** : Ces champs d'en-tête ne s'appliquent qu'aux messages de réponse.
- **Entity-header (en-tête d'entité)** : Ces champs d'en-tête définissent des méta-informations sur le corps de l'entité ou, si aucun corps n'est présent, sur la ressource identifiée par la demande.

## Accept-Ranges

Le champ d'en-tête de réponse Accept-Ranges permet au serveur d'indiquer qu'il accepte les demandes de plage pour une ressource. La syntaxe générale est la suivante :

```http
Accept-Ranges  : range-unit | none
```

Par exemple, un serveur qui accepte les requêtes de plage d'octets peut envoyer :

```http
Accept-Ranges: bytes
```

Les serveurs qui n'acceptent aucun type de demande de plage pour une ressource peuvent envoyer :

```http
Accept-Ranges: none
```

Le client sera ainsi informé qu'il ne doit pas tenter une demande de plage.

## Age

Le champ **Age** de l'en-tête de réponse indique l'estimation par l'expéditeur du temps écoulé depuis que la réponse (ou sa revalidation) a été générée sur le serveur d'origine. La syntaxe générale est la suivante :

```http
Age : delta-seconds
```

Les valeurs d'âge sont des entiers décimaux non négatifs, représentant le temps en secondes. Voici un exemple simple :

```http
Age: 1030
```

Un serveur HTTP/1.1 qui comprend un cache doit inclure un champ d'en-tête Age dans chaque réponse générée à partir de son propre cache.

## ETag

Le champ d'en-tête de réponse ETag fournit la valeur actuelle de la balise d'entité pour la variante demandée. La syntaxe générale est la suivante :

```http
ETag :  entity-tag
```

Voici quelques exemples simples :

```http
ETag: "xyzzy"
ETag: W/"xyzzy"
ETag: ""
```

## Location

Le champ d'en-tête de réponse Location est utilisé pour rediriger le destinataire vers un emplacement autre que l'URL de la demande. La syntaxe générale est la suivante :

```http
Location : absoluteURI
```

Voici un exemple simple :

```http
Expect : 100-continue | expectation-extension
```

Le champ d'en-tête **Content-Location** diffère de Location en ce sens que **Content-Location** identifie l'emplacement original de l'entité incluse dans la demande.

## Proxy-Authenticate

Le champ d'en-tête de réponse **Proxy-Authenticate** doit être inclus dans une réponse 407 (Proxy Authentication Required). La syntaxe générale est la suivante :

```http
Proxy-Authenticate  : challenge
```

## Retry-After

Le champ d'en-tête de réponse Retry-After peut être utilisé avec une réponse 503 (Service Unavailable) pour indiquer combien de temps le service est censé être indisponible pour le client demandeur. La syntaxe générale est la suivante :

```http
Retry-After : HTTP-date | delta-seconds
```

Exemples :

```http
Retry-After: Fri, 31 Dec 1999 23:59:59 GMT
Retry-After: 120
```

Dans ce dernier exemple, le délai est de 2 minutes.

## Server

Le champ "Server response-header" contient des informations sur le logiciel utilisé par le serveur d'origine pour traiter la demande. La syntaxe générale est la suivante :

```http
Server : product | comment
```

Voici un exemple simple :

```http
Server: Apache/2.2.14 (Win32)
```

Si la réponse est transmise par un proxy, l'application proxy ne doit pas modifier l'en-tête de réponse Server.

## Set-Cookie

Le champ d'en-tête de réponse **Set-Cookie** contient une paire nom/valeur d'informations à conserver pour cette URL. La syntaxe générale est la suivante :

```http
Set-Cookie: NAME=VALUE; OPTIONS
```

L'en-tête de réponse **Set-Cookie** comprend le jeton **Set-Cookie**, suivi d'une liste d'un ou plusieurs cookies séparés par des virgules. Voici les valeurs possibles que vous pouvez spécifier comme options :

- **Comment=comment** - Cette option peut être utilisée pour spécifier tout commentaire associé au cookie.
- **Domain=domain** - L'attribut Domain spécifie le domaine pour lequel le cookie est valide.
- **Expires=Date-time** - La date à laquelle le cookie expirera. S'il est vide, le cookie expirera lorsque le visiteur quittera le navigateur.
- **Path=path** - L'attribut Path spécifie le sous-ensemble d'URL auquel ce cookie s'applique.
- **Secure** - Il indique à l'agent utilisateur de renvoyer le cookie uniquement dans le cadre d'une connexion sécurisée.

Voici un exemple d'un simple en-tête de cookie généré par le serveur :

```http
Set-Cookie: name1=value1,name2=value2; Expires=Wed, 09 Jun 2021 10:18:14 GMT
```

## Vary

Le champ d'en-tête de réponse **Vary** indique que l'entité a plusieurs sources et peut donc varier en fonction de la liste spécifiée d'en-têtes de demande. La syntaxe générale est la suivante :

```http
Vary : field-name
```

Vous pouvez spécifier plusieurs en-têtes séparés par des virgules et une valeur d'astérisque "*" signale que les paramètres non spécifiés ne sont pas limités aux en-têtes de la demande. Voici un exemple simple :

```http
Vary: Accept-Language, Accept-Encoding
```

Les noms des champs sont ici insensibles à la casse.

## WWW-Authenticate

Le champ d'en-tête de réponse **WWW-Authenticate** doit être inclus dans les messages de réponse 401 (non autorisé). La valeur du champ consiste en au moins un défi qui indique le(s) schéma(s) d'authentification et les paramètres applicables à l'URL de la demande. La syntaxe générale est la suivante :

```http
WWW-Authenticate : challenge
```

La valeur du champ **WWW-Authenticate** peut contenir plus d'un défi, ou si plusieurs champs d'en-tête WWW-Authenticate sont fournis, le contenu d'un défi peut lui-même contenir une liste de paramètres d'authentification séparés par des virgules. Voici un exemple simple :

```http
WWW-Authenticate: BASIC realm="Admin"
```