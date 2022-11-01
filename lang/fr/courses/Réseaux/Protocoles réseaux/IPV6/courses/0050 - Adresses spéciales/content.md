La version 6 a une structure d'adresse IP légèrement plus complexe que celle de l'IPv4. IPv6 a réservé quelques adresses et notations d'adresses à des fins spéciales. Voir le tableau ci-dessous :

| **Adresses IPv6** | **Description** |
| --- | --- |
| ```::/128``` | Adresse non certifiée |
| ```::/0``` | Route par défaut |
| ```::1/128``` | Adresse de renvoi |

- Comme le montre le tableau, l'adresse 0:0:0:0:0:0:0/128 ne spécifie rien et est considérée comme une adresse non spécifiée. Après simplification, tous les 0 sont compactés en ::/128.
- En IPv4, l'adresse 0.0.0.0 avec le masque de réseau 0.0.0.0 représente la route par défaut. Le même concept est appliqué à IPv6, l'adresse 0:0:0:0:0:0:0:0 avec le masque de réseau tous les 0s représente la route par défaut. Après avoir appliqué la règle IPv6, cette adresse est compressée en ::/0.
- Les adresses de bouclage en IPv4 sont représentées par les séries 127.0.0.1 à 127.255.255.255. Mais en IPv6, seule l'adresse de bouclage est représentée par 0:0:0:0:0:0:1/128. Après l'adresse de bouclage, elle peut être représentée par ::1/128.

## Adresse multicast réservée pour les protocoles de routage

| **Adresses IPv6** | **Protocole de routage** |
| --- | --- |
| ```FF02::5``` | OSPFv3 |
| ```FF02::6``` | OSPFv3 Designated Routers |
| ```FF02::9``` | RIPng |
| ```FF02::A``` | EIGRP |

- Le tableau ci-dessus montre les adresses multicast réservées utilisées par le protocole de routage intérieur.
- Les adresses sont réservées selon les mêmes règles que pour IPv4.

## Adresse multicast réservée pour les routeurs/noeuds

| **Adresses IPv6** | **Portée** |
| --- | --- |
| ```FF01::1``` | Tous les noeuds de l'interface locale |
| ```FF01::2``` | Tous les routeurs de l'interface locale |
| ```FF02::1``` | Tous les noeuds de la liaison locale |
| ```FF02::2``` | Tous les routeurs de la liaison locale |
| ```FF05::2``` | Tous les routeurs du site local |

Ces adresses permettent aux routeurs et aux hôtes de parler aux routeurs et aux hôtes disponibles sur un segment sans être configurés avec une adresse IPv6. Les hôtes utilisent l'autoconfiguration basée sur EUI-64 pour auto-configurer une adresse IPv6 et ensuite parler aux hôtes/routeurs disponibles sur le segment au moyen de ces adresses.