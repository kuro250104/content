Les champs d'en-tête HTTP fournissent des informations obligatoires sur la demande ou la réponse, ou sur l'objet envoyé dans le corps du message. Il existe quatre types d'en-têtes de message HTTP :

- **General-header (en-tête général)** : Ces champs d'en-tête ont une applicabilité générale pour les messages de demande et de réponse.
- **En-tête de demande du client** : Ces champs d'en-tête ne s'appliquent qu'aux messages de demande.
- **En-tête de réponse du serveur** : Ces champs d'en-tête ne s'appliquent qu'aux messages de réponse.
- **Entity-header (en-tête d'entité)** : Ces champs d'en-tête définissent des méta-informations sur le corps de l'entité ou, si aucun corps n'est présent, sur la ressource identifiée par la demande.

## Accept

Le champ d'en-tête de demande **Accept** peut être utilisé pour spécifier certains types de médias qui sont acceptables pour la réponse. La syntaxe générale est la suivante :

```http
Accept: type/subtype [q=qvalue]
```

Plusieurs types de supports peuvent être listés en étant séparés par des virgules et la valeur facultative **qvalue** représente un niveau de qualité acceptable pour les types acceptés sur une échelle de 0 à 1. Voici un exemple :

```http
Accept: text/plain; q=0.5, text/html, text/x-dvi; q=0.8, text/x-c
```

Cela serait interprété comme **text/html** et **text/x-c**, qui sont les types de médias préférés, mais s'ils n'existent pas, alors envoyez l'entité **text/x-dvi**, et si celle-ci n'existe pas, envoyez l'entité text/plain.

## Accept-Charset

Le champ d'en-tête de demande Accept-Charset peut être utilisé pour indiquer les jeux de caractères acceptables pour la réponse. La syntaxe générale est la suivante :

```http
Accept-Charset: character_set [q=qvalue]
```

Plusieurs jeux de caractères peuvent être énumérés en étant séparés par des virgules et la valeur q facultative représente un niveau de qualité acceptable pour les jeux de caractères non préférés sur une échelle de 0 à 1. Voici un exemple :

```http
Accept-Charset: iso-8859-5, unicode-1-1; q=0.8
```

La valeur spéciale "*", si elle est présente dans le champ **Accept-Charset**, correspond à tous les jeux de caractères. Si aucun en-tête **Accept-Charset** n'est présent, la valeur par défaut est que tout jeu de caractères est acceptable.

## Accept-Encoding

Le champ d'en-tête de requête Accept-Encoding est similaire à Accept, mais restreint les codages de contenu qui sont acceptables dans la réponse. La syntaxe générale est la suivante :

```http
Accept-Encoding: encoding types
```

En voici quelques exemples :

```http
Accept-Encoding: compress, gzip
Accept-Encoding:
Accept-Encoding: *
Accept-Encoding: compress;q=0.5, gzip;q=1.0
Accept-Encoding: gzip;q=1.0, identity; q=0.5, *;q=0
```

## Accept-Language

Le champ d'en-tête de requête **Accept-Language** est similaire à **Accept**, mais restreint l'ensemble des langues naturelles qui sont préférées en réponse à la requête. La syntaxe générale est la suivante :

```http
Accept-Language: language [q=qvalue]
```

Plusieurs langues peuvent être énumérées en étant séparées par des virgules et la valeur q facultative représente un niveau de qualité acceptable pour les langues non préférées sur une échelle de 0 à 1. Voici un exemple :

```http
Accept-Language: da, en-gb;q=0.8, en;q=0.7
```

## Authorization

La valeur du champ d'en-tête de demande d'autorisation consiste en des informations d'identification contenant les informations d'authentification de l'agent utilisateur pour le domaine de la ressource demandée. La syntaxe générale est la suivante :

```http
Authorization : credentials
```

La spécification HTTP/1.0 définit le schéma d'autorisation BASIC, où le paramètre d'autorisation est la chaîne **username:password** encodée en base 64. Voici un exemple :

```http
Authorization: BASIC Z3Vlc3Q6Z3Vlc3QxMjM=
```

La valeur se décode en guest:guest123 où guest est l'ID utilisateur et guest123 est le mot de passe.

## Cookie

La valeur du champ d'en-tête de requête Cookie contient une paire nom/valeur d'informations stockées pour cette URL. Voici la syntaxe générale :

```http
Cookie: name=value
```

Plusieurs cookies peuvent être spécifiés, séparés par des points-virgules, comme suit :

```http
Cookie: name1=value1;name2=value2;name3=value3
```

## Expect

Le champ **Expect** request-header est utilisé pour indiquer qu'un ensemble particulier de comportements du serveur est requis par le client. La syntaxe générale est la suivante :

```http
Expect : 100-continue | expectation-extension
```

Si un serveur reçoit une demande contenant un champ Expect qui inclut une extension d'attente qu'il ne prend pas en charge, il doit répondre avec un état 417 (Expectation Failed).

## From

Le champ d'en-tête de demande **From** contient une adresse de courrier électronique Internet pour l'utilisateur humain qui contrôle l'agent utilisateur demandeur. Voici un exemple simple :

```http
From: webmaster@microlead.fr
```

Ce champ d'en-tête peut être utilisé à des fins de journalisation et comme moyen d'identifier la source des demandes invalides ou indésirables.

## Host

Le champ de l'en-tête de demande **Host** est utilisé pour spécifier l'hôte Internet et le numéro de port de la ressource demandée. La syntaxe générale est la suivante :

```http
Host : "Host" ":" host [ ":" port ] ;
```

Un hôte sans aucune information de port de fin implique le port par défaut, qui est 80. Par exemple, une requête sur le serveur d'origine pour http://www.microlead.fr/pub/WWW/ serait :

```http
GET /pub/WWW/ HTTP/1.1
Host: www.microlead.fr
```

## If-Match

Le champ d'en-tête de demande If-Match est utilisé avec une méthode pour la rendre conditionnelle. Cet en-tête demande au serveur d'exécuter la méthode demandée uniquement si la valeur donnée dans cette balise correspond aux balises d'entité données représentées par **ETag**. La syntaxe générale est la suivante :

```http
If-Match : entity-tag
```

Un astérisque (*) correspond à n'importe quelle entité, et la transaction ne se poursuit que si l'entité existe. Voici quelques exemples possibles :

```http
If-Match: "xyzzy"
If-Match: "xyzzy", "r2d2xxxx", "c3piozzzz"
If-Match: *
```

Si aucune des étiquettes d'entité ne correspond, ou si "*" est donné et qu'aucune entité courante n'existe, le serveur ne doit pas exécuter la méthode demandée et doit renvoyer une réponse 412 (Precondition Failed).

## If-Modified-Since

Le champ d'en-tête de demande If-Modified-Since est utilisé avec une méthode pour le rendre conditionnel. Si l'URL demandée n'a pas été modifiée depuis le temps spécifié dans ce champ, le serveur ne renverra pas d'entité, mais une réponse 304 (non modifiée) sans corps de message. La syntaxe générale de if-modified-since est la suivante :

```http
If-Modified-Since : HTTP-date
```

Un exemple du champ est :

```http
If-Modified-Since: Sat, 29 Oct 1994 19:43:31 GMT
```

Si aucune des étiquettes d'entité ne correspond, ou si "*" est donné et qu'aucune entité courante n'existe, le serveur ne doit pas exécuter la méthode demandée et doit renvoyer une réponse 412 (Precondition Failed).

## If-None-Match

Le champ d'en-tête de demande If-None-Match est utilisé avec une méthode pour la rendre conditionnelle. Cet en-tête demande au serveur d'exécuter la méthode demandée uniquement si l'une des valeurs données dans cette balise correspond aux balises d'entité données représentées par ETag. La syntaxe générale est la suivante :

```http
If-None-Match : entity-tag
```

Un astérisque (*) correspond à n'importe quelle entité, et la transaction ne se poursuit que si l'entité n'existe pas. Voici quelques exemples possibles :

```http
If-None-Match: "xyzzy"
If-None-Match: "xyzzy", "r2d2xxxx", "c3piozzzz"
If-None-Match: *
```

## If-Range

Le champ d'en-tête de requête **If-Range** peut être utilisé avec un GET conditionnel pour demander uniquement la partie de l'entité qui manque, si elle n'a pas été modifiée, et l'entité entière si elle a été modifiée. La syntaxe générale est la suivante :

```http
If-Range : entity-tag | HTTP-date
```

Une étiquette d'entité ou une date peut être utilisée pour identifier l'entité partielle déjà reçue. Par exemple :

```http
If-Range: Sat, 29 Oct 2020 19:43:31 GMT
```

Ici, si le document n'a pas été modifié depuis la date donnée, le serveur renvoie la plage d'octets indiquée par l'en-tête Range, sinon il renvoie la totalité du nouveau document.

## If-Unmodified-Since

Le champ d'en-tête de demande **If-Unmodified-Since** est utilisé avec une méthode pour le rendre conditionnel. La syntaxe générale est la suivante :

```http
If-Unmodified-Since : HTTP-date
```

Si la ressource demandée n'a pas été modifiée depuis le temps spécifié dans ce champ, le serveur doit effectuer l'opération demandée comme si l'en-tête **If-Unmodified-Since** n'était pas présent. Par exemple :

```http
If-Unmodified-Since: Sat, 29 Oct 2020 19:43:31 GMT
```

Si la demande aboutit à un état autre que **2xx** ou **412**, l'en-tête **If-Unmodified-Since** doit être ignoré.

## Max-Forwards

Le champ d'en-tête de demande **Max-Forwards** fournit un mécanisme avec les méthodes TRACE et OPTIONS pour limiter le nombre de proxies ou de passerelles qui peuvent transmettre la demande au prochain serveur entrant. Voici la syntaxe générale :

```http
Max-Forwards : n
```

La valeur **Max-Forwards** est un nombre entier décimal indiquant le nombre restant de fois que ce message de demande peut être transféré. Cette valeur est utile pour le débogage avec la méthode **TRACE**, en évitant les boucles infinies. Par exemple :

```http
Max-Forwards : 5
```

Le champ d'en-tête Max-Forwards peut être ignoré pour toutes les autres méthodes définies dans la spécification HTTP.

## Proxy-Authorization

Le champ d'en-tête de requête **Proxy-Authorization** permet au client de s'identifier (ou d'identifier son utilisateur) auprès d'un proxy qui requiert une authentification. Voici la syntaxe générale :

```http
Proxy-Authorization : credentials
```

La valeur du champ **Proxy-Authorization** consiste en des informations d'identification contenant les informations d'authentification de l'agent utilisateur pour le proxy et/ou le domaine de la ressource demandée.

## Range

Le champ d'en-tête de demande Range spécifie la ou les plages partielles du contenu demandé dans le document. La syntaxe générale est la suivante :

```http
Range: bytes-unit=first-byte-pos "-" [last-byte-pos]
```

La valeur first-byte-pos dans une spécification de plage d'octets donne le décalage d'octet du premier octet dans une plage. La valeur last-byte-pos donne le décalage du dernier octet de la plage, c'est-à-dire que les positions des octets spécifiés sont inclusives. Vous pouvez spécifier une unité d'octet comme des octets. Les décalages d'octets commencent à zéro. Voici quelques exemples simples :

```http
- Les premiers 500 bits
Range: bytes=0-499

- Les deuxièmes 500 bits
Range: bytes=500-999

- Les derniers 500 bits
Range: bytes=-500

- Le premier et le dernier bit seulement
Range: bytes=0-0,-1
```

Plusieurs plages peuvent être énumérées, séparées par des virgules. Si le premier chiffre de la ou des plages d'octets séparées par des virgules est manquant, la plage est supposée compter à partir de la fin du document. Si le deuxième chiffre est manquant, l'intervalle va de l'octet n à la fin du document.

## Referer

Le champ d'en-tête de demande Referer permet au client de spécifier l'adresse (URI) de la ressource à partir de laquelle l'URL a été demandée. La syntaxe générale est la suivante :

```http
Referer : absoluteURI | relativeURI
```

Voici un exemple simple :

```http
Referer: http://www.microlead.fr/http/index.htm
```

Si la valeur du champ est une URI relative, elle doit être interprétée par rapport à la Request-URI.

## TE

Le champ d'en-tête de la demande TE indique le codage de transfert de l'extension qu'il est prêt à accepter dans la réponse et s'il est prêt ou non à accepter les champs de fin dans un codage de transfert par morceaux. La syntaxe générale est la suivante :

```http
TE   : t-codings
```

La présence du mot-clé "trailers" indique que le client est prêt à accepter les champs trailers dans un codage de transfert par morceaux et il est spécifié de l'une ou l'autre des façons suivantes :

```http
TE: deflate
TE:
TE: trailers, deflate;q=0.5
```

Si la valeur du champ TE est vide ou si aucun champ TE n'est présent, seul le codage de transfert est mis en bloc. Un message sans codage de transfert est toujours acceptable.

## User-Agent

Le champ d'en-tête de demande User-Agent contient des informations sur l'agent utilisateur à l'origine de la demande. La syntaxe générale est la suivante :

```http
User-Agent : product | comment
```

Exemple :

```http
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
```