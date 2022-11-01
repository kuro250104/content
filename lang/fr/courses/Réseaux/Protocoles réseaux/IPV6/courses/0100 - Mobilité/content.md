Lorsqu'un hôte est connecté à une liaison ou un réseau, il acquiert une adresse IP et toutes les communications ont lieu en utilisant cette adresse IP sur cette liaison. Dès que le même hôte change d'emplacement physique, c'est-à-dire qu'il se déplace dans une autre zone / sous-réseau / réseau / liaison, son adresse IP change en conséquence, et toutes les communications qui ont lieu sur l'hôte utilisant l'ancienne adresse IP disparaissent.

La mobilité IPv6 fournit un mécanisme permettant à l'hôte de se déplacer sur différents liens sans perdre aucune communication/connexion et son adresse IP.

Plusieurs entités sont impliquées dans cette technologie :

- **Mobile Node** (*Nœud mobile*) : Le dispositif qui a besoin de la mobilité IPv6.
- **Home Link** (*Lien d'origine*) : Cette liaison est configurée avec le préfixe du sous-réseau domestique et c'est là que le dispositif mobile IPv6 obtient son adresse de rattachement.
- **Home Address** (*Adresse de rattachement*) : Il s'agit de l'adresse que le nœud mobile acquiert à partir du lien d'origine. Il s'agit de l'adresse permanente du nœud mobile. Si le nœud mobile reste dans la même liaison d'origine, la communication entre les diverses entités se déroule comme d'habitude.
- **Home Agent** (*Agent d'origine*) : Il s'agit d'un routeur qui joue le rôle d'agent d'enregistrement pour les nœuds mobiles. L'agent d'origine est connecté à la liaison d'origine et maintient des informations sur tous les nœuds mobiles, leurs adresses d'origine et leurs adresses IP actuelles.
- **Foreign Link** (*Lien étranger*) : Tout autre lien qui n'est pas le lien d'origine du nœud mobile.
- **Care-of Address** (*Adresse de prise en charge*) : Lorsqu'un nœud mobile est rattaché à un lien étranger, il acquiert une nouvelle adresse IP du sous-réseau de ce lien étranger. L'agent d'origine conserve les informations relatives à l'adresse d'origine et à l'adresse de prise en charge. Plusieurs adresses de prise en charge peuvent être attribuées à un nœud mobile, mais à tout moment, une seule adresse de prise en charge est liée à l'adresse de rattachement.
- **Correspondent Node** (*Nœud correspondant*) : Tout dispositif IPv6 qui a l'intention de communiquer avec le nœud mobile.

## Fonctionnement de la mobilité

Lorsque le nœud mobile reste dans sa liaison d'origine, toutes les communications ont lieu sur son adresse d'origine, comme indiqué ci-dessous :

![Noeud mobile restant dans sa liaison d'origine](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0100%20-%20Mobilit%C3%A9/images/image1.jpg)

Lorsqu'un nœud mobile quitte sa liaison d'origine et est connecté à une liaison étrangère, la fonction de mobilité d'IPv6 entre en jeu. Après s'être connecté à une liaison étrangère, le nœud mobile acquiert une adresse IPv6 auprès de la liaison étrangère. Cette adresse est appelée Care-of Address. Le Mobile Node envoie une demande de liaison à son Home Agent avec la nouvelle Care-of Address. L'agent d'origine lie l'adresse d'origine du nœud mobile avec l'adresse de prise en charge, établissant un tunnel entre les deux.

Lorsqu'un nœud correspondant tente d'établir une connexion avec le nœud mobile (sur son adresse de rattachement), l'agent d'origine intercepte le paquet et le transmet à l'adresse de rattachement du nœud mobile par le tunnel déjà établi.

![Noeud etablissant une connexion avec un noeud mobile](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0100%20-%20Mobilit%C3%A9/images/image2.jpg)

## Optimisation des routes

Lorsqu'un nœud correspondant initie une communication en envoyant des paquets au nœud mobile sur l'adresse de rattachement, ces paquets sont acheminés vers le nœud mobile par l'agent de rattachement. En mode d'optimisation de la route, lorsque le nœud mobile reçoit un paquet du nœud correspondant, il ne transmet pas les réponses à l'agent d'origine. Il envoie plutôt son paquet directement au nœud correspondant en utilisant l'adresse de rattachement comme adresse source. Ce mode est facultatif et n'est pas utilisé par défaut.