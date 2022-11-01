HTTP est basé sur le modèle d'architecture client-serveur et sur un protocole de demande/réponse sans état qui fonctionne par l'échange de messages sur une connexion TCP/IP fiable.

Un "client" HTTP est un programme (navigateur Web ou tout autre client) qui établit une connexion avec un serveur dans le but d'envoyer un ou plusieurs messages de demande HTTP. Un "serveur" HTTP est un programme (généralement un serveur web comme le serveur web Apache ou les services d'information Internet IIS, etc. ) qui accepte les connexions afin de répondre aux demandes HTTP en envoyant des messages de réponse HTTP.

Le protocole HTTP utilise l'identificateur de ressources uniformes (URI) pour identifier une ressource donnée et établir une connexion. Une fois la connexion établie, les **messages HTTP** sont transmis dans un format similaire à celui utilisé par le courrier Internet ```[RFC5322]``` et les Multipurpose Internet Mail Extensions (MIME) ```[RFC2045]```. Ces messages comprennent des **requêtes** du client au serveur et des **réponses** du serveur au client qui auront le format suivant :

```http
HTTP-message   = <Request> | <Response> ; HTTP/1.1 messages
```

Les demandes HTTP et les réponses HTTP utilisent un format de message générique de la RFC 822 pour transférer les données requises. Ce format de message générique se compose des quatre éléments suivants.

- Une ligne de début
- zéro ou plusieurs champs d'en-tête suivis d'un CRLF
- Une ligne vide (c'est-à-dire une ligne où rien ne précède le CRLF) indiquant la fin des champs d'en-tête
- éventuellement, un corps de message

Dans les sections suivantes, nous allons expliquer chacune des entités utilisées dans un message HTTP.

## Ligne de début de message

Une ligne de départ aura la syntaxe générique suivante :

```http
start-line = Request-Line | Status-Line
```

Nous parlerons de Request-Line et de Status-Line en abordant les messages HTTP Request et HTTP Response respectivement. Pour l'instant, voyons les exemples de ligne de départ dans le cas d'une demande et d'une réponse :

```http
GET /hello.htm HTTP/1.1     (This is Request-Line sent by the client)

HTTP/1.1 200 OK             (This is Status-Line sent by the server)
```

## Champs d'en-tête

Les champs d'en-tête HTTP fournissent des informations obligatoires sur la demande ou la réponse, ou sur l'objet envoyé dans le corps du message. Il existe quatre types d'en-têtes de message HTTP :

- **General-header** (*en-tête général*) : Ces champs d'en-tête ont une applicabilité générale pour les messages de demande et de réponse.
- **En-tête de demande** : Ces champs d'en-tête ne s'appliquent qu'aux messages de demande.
- **Response-header** (*en-tête de réponse*) : Ces champs d'en-tête ne s'appliquent qu'aux messages de réponse.
- **Entity-header** : Ces champs d'en-tête définissent des méta-informations sur le corps de l'entité ou, si aucun corps n'est présent, sur la ressource identifiée par la demande.

Tous les en-têtes mentionnés ci-dessus suivent le même format générique et chacun des champs d'en-tête se compose d'un nom suivi de deux points ( :) et de la valeur du champ comme suit :

```http
message-header = field-name ":" [ field-value ]
```

Voici des exemples de différents champs d'en-tête :

```http
User-Agent: curl/7.16.3 libcurl/7.16.3 OpenSSL/0.9.7l zlib/1.2.3
Host: www.example.com
Accept-Language: en, mi
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
ETag: "34aa387-d-1568eb00"
Accept-Ranges: bytes
Content-Length: 51
Vary: Accept-Encoding
Content-Type: text/plain
```

## Corps du message

La partie corps du message est facultative pour un message HTTP mais si elle est disponible, elle est utilisée pour transporter le corps de l'entité associé à la demande ou à la réponse. Si le corps de l'entité est associé, alors les lignes d'en-tête Content-Type et Content-Length précisent généralement la nature du corps associé.

Un corps de message est celui qui transporte les données réelles de la demande HTTP (y compris les données de formulaire et les données téléchargées, etc.) et les données de la réponse HTTP du serveur ( y compris les fichiers, les images, etc.). Le contenu simple d'un corps de message est illustré ci-dessous :

```html
<html>
   <body>
   
        <h1>Hello, World!</h1>
   
   </body>
</html>
```

Les deux chapitres suivants utilisent les concepts expliqués ci-dessus pour préparer les requêtes HTTP et les réponses HTTP.