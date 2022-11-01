Un client HTTP envoie une requête HTTP à un serveur sous la forme d'un message de requête qui comprend le format suivant :

- Une ligne de demande
- Zéro ou plusieurs champs d'en-tête (Général|Requête|Entité) suivis d'un CRLF.
- Une ligne vide (c'est-à-dire une ligne où rien ne précède le CRLF) indiquant la fin des champs d'en-tête
- éventuellement, un corps de message.

Les sections suivantes expliquent chacune des entités utilisées dans un message de requête HTTP.

## Request-Line

La Request-Line commence par un jeton de méthode, suivi de la Request-URI et de la version du protocole, et se termine par CRLF. Les éléments sont séparés par des caractères d'espacement SP.

```http
Request-Line = Method SP Request-URI SP HTTP-Version CRLF
```

Examinons chacune des parties mentionnées dans la Request-Line.

### Méthode de demande

La méthode “**request**” indique la méthode à exécuter sur la ressource identifiée par la Request-URI donnée. La méthode est sensible à la casse et doit toujours être mentionnée en majuscules. Le tableau suivant énumère toutes les méthodes prises en charge dans le protocole HTTP/1.1.

Voici la liste des méthodes utilisées : 

- **GET** : La méthode **GET** est utilisée pour récupérer des informations sur un serveur donné à l'aide d'un URI donné. Les requêtes utilisant **GET** doivent uniquement récupérer des données et ne doivent avoir aucun autre effet sur les données.
- **HEAD** : Identique à la méthode **GET**, mais elle transfère uniquement la ligne d'état et la section d'en-tête.
- **POST** : Une requête **POST** est utilisée pour envoyer des données au serveur, par exemple, des informations sur les clients, le téléchargement de fichiers, etc. à l'aide de formulaires HTML.
- **PUT** : Remplace toutes les représentations actuelles de la ressource cible par le contenu téléchargé.
- **DELETE** : Supprime toutes les représentations actuelles de la ressource cible indiquée par l'URI.
- **CONNECT** : Établit un tunnel vers le serveur identifié par un URI donné.
- **OPTIONS** : Décrit les options de communication pour la ressource cible.
- **TRACE** : Effectue un test de retour en boucle des messages ainsi que le chemin vers la ressource cible.

### Request-URI

Le Request-URI est un identificateur de ressources uniformes (URI) et identifie la ressource à laquelle s'applique la demande. Voici les formes les plus couramment utilisées pour spécifier un URI :

```http
Request-URI = "*" | absoluteURI | abs_path | authority
```

- ```*``` : L'astérisque ```*``` est utilisé lorsqu'une requête HTTP ne s'applique pas à une ressource particulière, mais au serveur lui-même. Il n'est autorisé que lorsque la méthode utilisée ne s'applique pas nécessairement à une ressource. Par exemple : ```OPTIONS * HTTP/1.1```
- ```absoluteURI``` : L'absoluteURI est utilisé lorsqu'une requête HTTP est adressée à un proxy. On demande au proxy de transmettre la requête ou le service à partir d'un cache valide, et de renvoyer la réponse. Par exemple : ```GET http://www.microlead.fr/ HTTP/1.1```
- La forme la plus courante de Request-URI est celle utilisée pour identifier une ressource sur un serveur d'origine ou une passerelle. Par exemple, un client souhaitant récupérer une ressource directement sur le serveur d'origine créera une connexion TCP au port 80 de l'hôte "www.w3.org" et enverra les lignes suivantes : ```GET /pub/WWW/TheProject.html HTTP/1.1 Host: www.microlead.fr```. Notez que le chemin absolu ne peut pas être vide ; si aucun chemin n'est présent dans l'URI d'origine, il DOIT être donné sous la forme "/" (la racine du serveur).

### Champs d'en-tête de la demande

Nous étudierons **General-header** et **Entity-header** dans un chapitre séparé lorsque nous apprendrons les champs d'en-tête HTTP. Pour l'instant, vérifions ce que sont les champs d'en-tête de requête.

Les champs d'en-tête de requête permettent au client de transmettre au serveur des informations supplémentaires sur la requête, et sur le client lui-même. Ces champs agissent comme des modificateurs de requête. Voici une liste de quelques champs d'en-tête de requête importants qui peuvent être utilisés en fonction des besoins :

- Accept-Charset
- Accept-Encoding
- Accept-Language
- Authorization
- Expect
- From
- Host
- If-Match
- If-Modified-Since
- If-None-Match
- If-Range
- If-Unmodified-Since
- Max-Forwards
- Proxy-Authorization
- Range
- Referer
- TE
- User-Agent

Vous pouvez introduire vos champs personnalisés dans le cas où vous allez écrire votre propre client et serveur Web personnalisés.

### Exemples de message de demande

Maintenant, assemblons tout cela pour former une requête HTTP afin de récupérer la page ```hello.htm``` sur le serveur web de microlead.fr.

```http
GET /hello.htm HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.microlead.fr
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive
```

Ici, nous n'envoyons pas de données de requête au serveur car nous récupérons une page HTML simple depuis le serveur. Connection est un en-tête général, et le reste des en-têtes sont des en-têtes de requête. L'exemple suivant montre comment envoyer des données de formulaire au serveur en utilisant le corps du message de la requête :

```http
POST /cgi-bin/process.cgi HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.microlead.fr
Content-Type: application/x-www-form-urlencoded
Content-Length: length
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive

licenseID=string&content=string&/paramsXML=string
```

Ici, l'URL donnée ```/cgi-bin/process.cgi``` sera utilisée pour traiter les données transmises et, en conséquence, une réponse sera renvoyée. Ici, **content-type** indique au serveur que les données transmises sont de simples données de formulaire web et **length** sera la longueur réelle des données placées dans le corps du message. L'exemple suivant montre comment vous pouvez transmettre des données XML simples à votre serveur Web :

```http
POST /cgi-bin/process.cgi HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.microlead.fr
Content-Type: text/xml; charset=utf-8
Content-Length: length
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive

<?xml version="1.0" encoding="utf-8"?>
<string xmlns="http://clearforest.com/">string</string>
```