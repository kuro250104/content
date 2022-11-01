L'élément Status-Code d'une réponse de serveur est un nombre entier à trois chiffres dont le premier définit la classe de la réponse et les deux derniers n'ont aucun rôle de catégorisation. Il existe 5 valeurs pour le premier chiffre :

- **1xx (Informatif)** - Cela signifie que la demande a été reçue et que le processus se poursuit.
- **2xx (Succès)** - Cela signifie que l'action a été reçue, comprise et acceptée avec succès.
- **3xx (Redirection)** - Cela signifie que d'autres actions doivent être entreprises afin de compléter la demande.
- **4xx (Erreur du client)** - Cela signifie que la demande contient une syntaxe incorrecte ou ne peut pas être satisfaite.
- **5xx (Erreur du serveur)** - Cela signifie que le serveur n'a pas réussi à répondre à une demande apparemment valide.

Les codes d'état HTTP sont extensibles et les applications HTTP ne sont pas tenues de comprendre la signification de tous les codes d'état enregistrés. Vous trouverez ci-dessous une liste de tous les codes d'état.

## 1xx: Informatif

- **100 Continue** - Seule une partie de la demande a été reçue par le serveur, mais tant qu'elle n'a pas été rejetée, le client doit poursuivre sa demande.
- **101 Changement de protocole** - Le serveur change de protocole.

## 2xx : Succès

- **200 OK** - La demande est correcte.
- **201 Created** - La demande est complète, et une nouvelle ressource est créée.
- **202 Accepted** - La demande est acceptée pour traitement, mais le traitement n'est pas terminé.
- **203 Non-authoritative Information** - Les informations contenues dans l'en-tête de l'entité proviennent d'une copie locale ou d'une tierce partie, et non du serveur d'origine.
- **204 No Content** - Un code d'état et un en-tête sont donnés dans la réponse, mais il n'y a pas de corps d'entité dans la réponse.
- **205 Reset Content** - Le navigateur doit effacer le formulaire utilisé pour cette transaction afin d'obtenir des données supplémentaires.
- **206 Partial Content** - Le serveur renvoie des données partielles de la taille demandée. Utilisé en réponse à une demande spécifiant un en-tête Range. Le serveur doit préciser la plage incluse dans la réponse avec l'en-tête Content-Range.

## 3xx : Redirection

- **300 Choix multiples** - Une liste de liens. L'utilisateur peut sélectionner un lien et se rendre à cet endroit. Maximum cinq adresses .
- **301 Moved Permanently** - La page demandée a été déplacée vers un nouvel url.
- **302 Found** - La page demandée a été déplacée temporairement vers un nouvel url.
- **303 See Other** - La page demandée peut être trouvée sous une autre URL.
- **304 Not Modified** - Il s'agit du code de réponse à un en-tête If-Modified-Since ou If-None-Match, lorsque l'URL n'a pas été modifiée depuis la date spécifiée.
- **305 Use Proxy** - L'URL demandée doit être accessible via le proxy mentionné dans l'en-tête Location.
- **306 Unused** - Ce code était utilisé dans une version précédente. Il n'est plus utilisé, mais le code est réservé.
- **307 Temporary Redirect** - La page demandée a été déplacée temporairement vers une nouvelle URL.

## 4xx : Erreur du client

- **400 Bad Request** - Le serveur n'a pas compris la demande.
- **401 Unauthorized** - La page demandée nécessite un nom d'utilisateur et un mot de passe.
- **402 Paiement requis** - Vous ne pouvez pas encore utiliser ce code.
- **403 Forbidden** - L'accès à la page demandée est interdit.
- **404 Not Found** - Le serveur ne peut pas trouver la page demandée.
- **405 Method Not Allowed** - La méthode spécifiée dans la demande n'est pas autorisée.
- **406 Not Acceptable** - Le serveur ne peut que générer une réponse qui n'est pas acceptée par le client.
- **407 Authentification du proxy requise** - Vous devez vous authentifier auprès d'un serveur proxy avant que cette requête puisse être servie.
- **408 Request Timeout** - La demande a pris plus de temps que le serveur n'était prêt à attendre.
- **409 Conflit** - La demande n'a pas pu être traitée en raison d'un conflit.
- **410 Gone** - La page demandée n'est plus disponible.
- **411 Longueur requise** - Le "Content-Length" n'est pas défini. Le serveur n'acceptera pas la demande sans cette longueur.
- **412 Precondition Failed** - La condition préalable donnée dans la demande a été évaluée comme fausse par le serveur.
- **413 Request Entity Too Large** - Le serveur n'acceptera pas la demande, car l'entité de la demande est trop grande.
- **414 Request-url Too Long** - Le serveur n'acceptera pas la demande, car l'url est trop longue. Cela se produit lorsque vous convertissez une requête "post" en requête "get" avec des informations de requête longues.
- **415 Unsupported Media Type** - Le serveur n'acceptera pas la demande, car le type de média n'est pas pris en charge.
- **416 Requested Range Not Satisfiable** - La plage d'octets demandée n'est pas disponible et est hors limites.
- **417 Expectation Failed** - L'attente indiquée dans un champ d'en-tête de demande Expect n'a pas pu être satisfaite par ce serveur.

## 5xx : Erreur de serveur

- **500 Internal Server Error** - La requête n'a pas été complétée. Le serveur a rencontré une situation inattendue.
- **501 Not Implemented** - La demande n'a pas abouti. Le serveur n'a pas pris en charge la fonctionnalité requise.
- **502 Bad Gateway** - La demande n'a pas été exécutée. Le serveur a reçu une réponse non valide du serveur en amont.
- **503 Service indisponible** - La demande n'a pas été exécutée. Le serveur est temporairement surchargé ou hors service.
- **504 Gateway Timeout** - La passerelle a expiré.
- **505 Version HTTP non prise en charge** - Le serveur ne prend pas en charge la version du "protocole http".