Une URL est composée d’un nom de domaine (microlead, par exemple), suivi de l’extension (.fr, .com, .tv, etc.). Cependant, derrière le nom de domaine se cache simplement une adresse IP telle que : 192.168.1.1.

D’ailleurs, si un utilisateur tape simplement l’adresse IP du serveur sur lequel un site est hébergé, il pourrait également accéder au site en question. Cependant, les mots étant plus simples à retenir que les chiffres, car plus descriptifs, les développeurs ont créé le principe de l’URL.

## URL - Uniform Resource Locator

Lorsqu’un utilisateur tape le nom d’un site internet dans la barre d’adresse d’un navigateur, celui-ci va simplement aller chercher l’adresse IP correspondant au nom de l’URL renseignée par l’utilisateur, accéder au serveur et afficher la page web demandée. 

Une URL suit les règles suivantes :

```schema://prefix.domaine:port/chemin/nomdefichier```

- **Schéma** définit le type de requête adressée au serveur (les plus courantes sont http et https).
- **Prefix** définit un préfixe de domaine. Le préfixe le plus connu, et qui est rattaché directement au protocole HTTP(S) est : **www**.
- **Domaine** correspond au nom du site web recherché (microLead, par exemple)
- **Port** définit le numéro de port sur l'hôte (la valeur par défaut pour http est 80). Cette valeur est facultative lorsque l’utilisateur tape le nom du site dans la barre de recherche d’un navigateur internet.
- **Chemin** définit un chemin d’accès aux fichiers sur le serveur. Si aucun chemin n’est précisé, le répertoire racine sera sélectionné par défaut.
- **Nomdefichier** concerne le nom du fichier à afficher à l’écran. Dans le cas d’un fichier HTML, si aucun nom de fichier n’est précisé, le navigateur affichera par défaut le fichier index.html.

## Schémas d'URL courants

Ci-dessous, un tableau listant les schémas d’URL les plus couramment utilisés :

| **Schéma** | **Description** | **Utilisé pour** |
| --- | --- | --- |
| http | HyperText Transfer Protocol | Pages Web communes. Non chiffré |
| https | Secure HyperText Transfer Protocol | Pages Web communes. Chiffré |
| ftp | File Transfer Protocol | Téléchargement de fichiers |
| file |  | Un fichier se trouvant sur l’ordinateur de l’utilisateur |

## Encodage d'URL

Les URL ne peuvent comporter que des caractères définis dans la norme ASCII. Si tel n’est pas le cas, l’URL est convertie afin de correspondre à ce standard. 

Lors de ce processus de conversion (appelé codage d’URL), les caractères non-ASCII sont remplacés par le signe pourcentage (**%**) suivi de la valeur hexadécimale du caractère en question.

Les URL ne peuvent pas contenir d'espaces. L’encodage d'URL remplace les espaces soit par un signe plus (**+**), soit par **%20**.