Les champs d'en-tête HTTP fournissent des informations obligatoires sur la demande ou la réponse, ou sur l'objet envoyé dans le corps du message. Il existe quatre types d'en-têtes de message HTTP :

- **General-header (en-tête général)** : Ces champs d'en-tête ont une applicabilité générale pour les messages de demande et de réponse.
- **En-tête de demande du client** : Ces champs d'en-tête ne s'appliquent qu'aux messages de demande.
- **En-tête de réponse du serveur** : Ces champs d'en-tête ne s'appliquent qu'aux messages de réponse.
- **Entity-header (en-tête d'entité)** : Ces champs d'en-tête définissent des méta-informations sur le corps de l'entité ou, si aucun corps n'est présent, sur la ressource identifiée par la demande.

## Allow

Le champ d'en-tête d'entité **Allow** énumère l'ensemble des méthodes prises en charge par la ressource identifiée par le Request-URI. La syntaxe générale est la suivante :

```http
Allow : Method
```

Vous pouvez spécifier plusieurs méthodes séparées par des virgules. Voici un exemple simple :

```http
Allow: GET, HEAD, PUT
```

Ce champ ne peut pas empêcher un client d'essayer d'autres méthodes.

## Content-Encoding

Le champ d'en-tête d'entité **Content-Encoding** est utilisé comme modificateur du media-type. La syntaxe générale est la suivante :

```http
Content-Encoding : content-coding
```

Le codage du contenu est une caractéristique de l'entité identifiée par le Request-URI. Voici un exemple simple :

```http
Content-Encoding: gzip
```

Si le codage du contenu d'une entité dans un message de demande n'est pas acceptable pour le serveur d'origine, ce dernier doit répondre par un code d'état 415 (Unsupported Media Type).

## Content-Language

Le champ d'en-tête d'entité **Content-Language** décrit le(s) langage(s) naturel(s) du public visé par l'entité jointe. La syntaxe générale est la suivante :

```http
Content-Language : language-tag
```

Plusieurs langues peuvent être répertoriées pour un contenu destiné à plusieurs publics. Voici un exemple simple :

```http
Content-Language: mi, en
```

L'objectif principal de Content-Language est de permettre à un utilisateur d'identifier et de différencier les entités en fonction de sa propre langue préférée.

## Content-Length
Le champ d'en-tête d'entité Content-Length indique la taille du corps d'entité, en nombre décimal d'OCTET, envoyé au destinataire ou, dans le cas de la méthode HEAD, la taille du corps d'entité qui aurait été envoyé, si la demande avait été un GET. La syntaxe générale est la suivante :

```http
Content-Length : DIGITS
```

Voici un exemple simple :

```http
Content-Length: 3495
```

Toute longueur de contenu supérieure ou égale à zéro est une valeur valide.

## Content-Location

Le champ d'en-tête **Content-Location** peut être utilisé pour fournir l'emplacement de la ressource pour l'entité contenue dans le message lorsque cette entité est accessible à partir d'un emplacement distinct de l'URI de la ressource demandée. La syntaxe générale est la suivante :

```http
Content-Location:  absoluteURI | relativeURI 
```

Voici un exemple simple :

```http
Content-Location: http://www.microlead.fr/http/index.htm
```

La valeur de Content-Location définit également l'URI de base pour l'entité.

## Content-MD5

Le champ d'en-tête d'entité **Content-MD5** peut être utilisé pour fournir un condensé MD5 de l'entité afin de vérifier l'intégrité du message à sa réception. La syntaxe générale est la suivante :

```http
Content-MD5  : md5-digest using base64 of 128 bit MD5 digest as per RFC 1864
```

Voici un exemple simple :

```http
Content-MD5  : 8c2d46911f3f5a326455f0ed7a8ed3b3
```

Le condensé MD5 est calculé sur la base du contenu du corps de l'entité, y compris tout codage de contenu qui a été appliqué, mais sans inclure tout codage de transfert appliqué au corps du message.

## Content-Range

Le champ d'en-tête d'entité Content-Range est envoyé avec un corps d'entité partiel pour spécifier où, dans le corps d'entité complet, le corps partiel doit être appliqué. La syntaxe générale est la suivante :

```http
Content-Range : bytes-unit SP first-byte-pos "-" last-byte-pos
```

Exemples de valeurs de spécification de plage de contenu d'octet, en supposant que l'entité contient un total de 1234 octets :

```http
- Les premiers 500 bits
Content-Range : bytes 0-499/1234

-Les seconds 500 bits
Content-Range : bytes 500-999/1234

- Tous à l’exception des premiers 500 bits
Content-Range : bytes 500-1233/1234

- Les derniers 500 bits
Content-Range : bytes 734-1233/1234
```

Lorsqu'un message HTTP comprend le contenu d'une seule plage, ce contenu est transmis avec un en-tête Content-Range, et un en-tête Content-Length indiquant le nombre d'octets effectivement transférés. Par exemple :

```http
HTTP/1.1 206 Partial content
Date: Wed, 15 Nov 2020 06:25:24 GMT
Last-Modified: Wed, 15 Nov 2020 04:58:08 GMT
Content-Range: bytes 21010-47021/47022
Content-Length: 26012
Content-Type: image/gif
```

## Content-Type

Le champ d'en-tête d'entité Content-Type indique le type de média du corps d'entité envoyé au destinataire ou, dans le cas de la méthode HEAD, le type de média qui aurait été envoyé, si la demande avait été un GET. La syntaxe générale est la suivante :

```http
Content-Type : media-type
```

Voici un exemple :

```http
Content-Type: text/html; charset=ISO-8859-4
```

## Expires

Le champ d'en-tête d'entité Expires indique la date et l'heure après lesquelles la réponse est considérée comme périmée. La syntaxe générale est la suivante :

```http
Expires : HTTP-date
```

Voici un exemple :

```http
Expires: Thu, 01 Dec 2020 16:00:00 GMT
```

## Last-Modified

Le champ d'en-tête d'entité Last-Modified indique la date et l'heure auxquelles le serveur d'origine pense que la variante a été modifiée pour la dernière fois. La syntaxe générale est la suivante :

```http
Last-Modified: HTTP-date
```

Voici un exemple :

```http
Last-Modified: Tue, 15 Nov 2020 12:45:26 GMT
```