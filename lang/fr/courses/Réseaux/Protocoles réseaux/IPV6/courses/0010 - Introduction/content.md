Le protocole Internet version 6 est un nouveau protocole d'adressage conçu pour intégrer toutes les exigences possibles du futur Internet connu sous le nom d'Internet version 2. Ce protocole, comme son prédécesseur IPv4, fonctionne sur la couche réseau (couche 3). En plus de l'énorme espace d'adressage logique qu'il offre, ce protocole possède de nombreuses fonctionnalités qui permettent de remédier aux lacunes de l'IPv4.

## Pourquoi une nouvelle version d'IP ?

Jusqu'à présent, l'IPv4 a fait ses preuves en tant que protocole d'adressage routable robuste et nous a servi pendant des décennies grâce à son mécanisme de livraison au mieux. Il a été conçu au début des années 80 et n'a pas subi de modifications majeures par la suite. À l'époque de sa naissance, Internet était limité à quelques universités pour leurs recherches et au Ministère de la défense. L'IPv4 comporte 32 bits et offre environ 4 294 967 296 (232) adresses. Cet espace d'adressage était considéré comme plus que suffisant à l'époque. Vous trouverez ci-dessous les principaux points qui ont joué un rôle-clé dans la naissance d'IPv6 :

- Internet a connu une croissance exponentielle et l'espace d'adressage autorisé par IPv4 est en train de saturer. Il est nécessaire de disposer d'un protocole capable de répondre aux besoins des futures adresses Internet, qui devraient croître de manière inattendue.
- L'IPv4 en lui-même ne fournit aucune fonction de sécurité. Les données doivent être cryptées avec une autre application de sécurité avant d'être envoyées sur Internet.
- La hiérarchisation des données dans IPv4 n'est pas à jour. Bien qu'IPv4 ait quelques bits réservés au type de service ou à la qualité de service, ils n'offrent pas beaucoup de fonctionnalités.
- Les clients compatibles IPv4 peuvent être configurés manuellement ou ils ont besoin d'un mécanisme de configuration d'adresse. Il n'existe pas de mécanisme permettant de configurer un appareil pour qu'il ait une adresse IP unique au niveau mondial.

## Pourquoi pas IPv5 ?

Jusqu'à présent, le protocole Internet n'a été reconnu que sous le nom d'IPv4. Les versions 0 à 3 ont été utilisées alors que le protocole était lui-même en cours de développement et de processus expérimental. On peut donc supposer que de nombreuses activités de fond restent actives avant de mettre un protocole en production. De même, la version 5 du protocole a été utilisée lors de l'expérimentation du protocole de flux pour Internet. Il est connu sous le nom d'**Internet Stream Protocol** qui utilise le protocole Internet numéro 5 pour encapsuler son datagramme. Il n'a jamais été mis en service public, mais il était déjà utilisé.

Voici un tableau des versions IP et de leur utilisation :

| **Décimale** | **Mot-clé** | **Version** |
| 0-1 |  | Reserved |
| 2-3 |  | Unassigned |
| 4 | IP | Internet Protocol |
| 5 | ST | Internet Protocol |
| 6 | IPv6 | Internet Protocol version 6 |
| 7 | TP/IX | TP/IX : The next Internet |
| 8 | PIP | The P Internet Protocol |
| 9 | TUBA | TUBA |
| 10-14 |  | Unassigned |
| 15 |  | Reserved |

## Brève histoire

Après le développement d'IPv4 au début des années 80, le pool d'adresses IPv4 disponible a commencé à se réduire rapidement, la demande d'adresses augmentant de façon exponentielle avec Internet. Conscient de la situation qui pourrait se produire, l'IETF a lancé en 1994 le développement d'un protocole d'adressage pour remplacer IPv4. L'évolution d'IPv6 peut être suivie au moyen des RFC publiés :

- *1998* - **RFC 2460** - Protocole de base
- *2003* - **RFC 2553** - API de socket de base
- *2003* - **RFC 3315** - DHCPv6
- *2004* - **RFC 3775** - IPv6 mobile
- *2004* - **RFC 3697** - Spécification d'étiquette de flux
- *2006* - **RFC 4291** - Architecture d'adresse (révision)
- *2006* - **RFC 4294** - Exigences relatives aux nœuds

Le 6 juin 2012, certains des géants de l'Internet ont choisi de mettre leurs serveurs sous IPv6. Actuellement, ils utilisent le mécanisme de double pile pour mettre en œuvre IPv6 en parallèle avec IPv4.