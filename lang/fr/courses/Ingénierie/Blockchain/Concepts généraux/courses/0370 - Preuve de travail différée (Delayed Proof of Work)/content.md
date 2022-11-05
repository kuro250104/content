La preuve de travail différée (*dPoW - Delayed Proof of Work*) est un mécanisme de sécurité conçu par le projet Komodo. Il s'agit essentiellement d'une version modifiée de l'algorithme de consensus Proof of Work (PoW) qui utilise la puissance de la blockchain Bitcoin pour renforcer la sécurité du réseau. En utilisant dPoW, les développeurs de Komodo sont en mesure de sécuriser non seulement leur propre réseau, mais aussi toute chaîne tierce qui finira par rejoindre l'écosystème Komodo à l'avenir. En fait, dPoW peut être mis en œuvre pour tout projet qui développe une blockchain indépendante utilisant un modèle UTXO.

## Comment fonctionne le dPoW ?

Si l'on prend l'exemple de Komodo, le mécanisme de sécurité dPoW a été développé et mis en œuvre dans la base de code Zcash, permettant une confidentialité à connaissance zéro et augmentant la sécurité du réseau en tirant parti du taux de hachage du bitcoin.

À intervalles de dix minutes, le système Komodo prend un instantané de sa propre blockchain. Ensuite, l'instantané est écrit dans un bloc sur le réseau Bitcoin dans un processus appelé notarisation. Fondamentalement, ce processus crée une sauvegarde de l'ensemble du système Komodo, qui est enregistrée dans la blockchain Bitcoin.

Techniquement parlant, les nœuds notaires élus par la communauté de Komodo écrivent un hachage de bloc de chaque blockchain protégée par dPoW sur le grand livre de Komodo, en exécutant une transaction sur la chaîne de Komodo. À l'aide de la commande OP_RETURN, les nœuds notariaux enregistrent un seul hachage de bloc sur la chaîne Komodo.

La raison pour laquelle les nœuds notaires choisissent un hachage de bloc qui date d'environ dix minutes est de s'assurer que l'ensemble du réseau reconnaît la validité du bloc. Le réseau de chaque blockchain parvient toujours à un consensus pour chaque bloc. Les nœuds notaires enregistrent simplement un hachage de bloc à partir d'un bloc précédemment extrait.

Ensuite, les nœuds notaires écrivent un hachage de bloc de la chaîne Komodo sur le grand livre du Bitcoin. Ce processus est également complété par l'exécution d'une transaction BTC et l'utilisation de OP_RETURN pour écrire les données dans un bloc de la chaîne Bitcoin.

Une fois que cette notarisation vers Bitcoin a lieu, les nœuds notaires de Komodo réécrivent les données du bloc de la chaîne BTC sur la chaîne de toutes les autres chaînes protégées. À ce stade, le réseau n'acceptera aucune réorganisation visant à modifier un bloc notarié (ou tout bloc créé avant le bloc notarié le plus récent).

Actuellement, dPoW est utilisé avec Bitcoin, mais il peut être utilisé comme un outil pour tirer parti de la sécurité et des caractéristiques de toute autre blockchain qui utilise un modèle UTXO.

## PoW vs dPoW

L'un des principaux objectifs de l'algorithme de preuve de travail (PoW) est de maintenir la sécurité du réseau, en dissuadant les cyberattaques telles que les attaques par déni de service distribué (DDoS). En quelques mots, l'algorithme PoW est une donnée très coûteuse à produire mais facile à vérifier pour les autres, ce qui constitue un élément crucial du processus de minage.

Le minage dans les blockchains basées sur l'algorithme PoW est très exigeant de par sa conception. Les mineurs doivent résoudre un puzzle cryptographique complexe afin de pouvoir extraire un nouveau bloc. Ce processus implique un travail de calcul intense, qui est très coûteux en termes de matériel et d'électricité. Le processus de minage permet non seulement de protéger le réseau contre les attaques extérieures, mais aussi de vérifier la légitimité des transactions et de générer de nouvelles unités de crypto-monnaie (comme récompense pour le mineur qui résout l'énigme). 

Par conséquent, l'une des raisons pour lesquelles les blockchains Proof of Work sont sécurisées est le fait que le processus de minage implique un investissement financier très élevé et dépend du consensus du réseau. Cependant, il est important de noter que la sécurité des blockchains PoW est directement liée à la quantité de puissance de calcul (taux de hachage) qui leur est consacrée, ce qui signifie que les petits réseaux de blockchains ne sont pas aussi sûrs que les grands.

Contrairement au PoW, le dPoW n'est pas utilisé pour obtenir un consensus sur les nouveaux blocs et n'est donc pas considéré comme un algorithme de consensus. Il s'agit plutôt d'un mécanisme de sécurité qui est mis en œuvre en plus des règles de consensus PoW ordinaires. Le DPoW rend impossible la réorganisation des blocs qui ont été notés, ce qui signifie qu'il rend les blockchains beaucoup plus sûres et résistantes aux attaques de 51 %.

En effet, dPoW "réinitialise" les règles de consensus d'une blockchain chaque fois qu'un bloc est notarié. Par exemple, la plupart des chaînes PoW utilisent la "règle de la chaîne la plus longue". Ainsi, chaque fois que le réseau d'une blockchain reçoit la confirmation que le bloc XXX,XX1 a été notarié, la règle de la chaîne la plus longue recommence au bloc XXX,XX2. Le réseau n'acceptera pas une chaîne qui commence au bloc XXX,XX0 ou avant, même si c'est la plus longue.

## Conclusion

Le mécanisme de sécurité de la preuve de travail différée permet des sauvegardes fréquentes afin de garantir qu'en cas de panne du système ou de piratage réussi, l'ensemble des données peut être rapidement récupéré. Pour qu'un piratage réussisse à causer des dommages durables, il faudrait que l'attaquant mette également hors service le réseau Bitcoin, détruisant ainsi tous les instantanés sauvegardés dans la blockchain Bitcoin.