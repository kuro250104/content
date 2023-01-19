Nous  avons vu précédemment que la PEP1 décrit les PEP, leur validation, les destinataires et intervenants. Mais ça ne s’arrête pas là: cette PEP permet aussi à sa communauté de participer à l’évolution du langage en décrivant le cycle de vie des PEP et leur format.

[https://www.python.org/dev/peps/pep-0001/](https://www.python.org/dev/peps/pep-0001/, "Lien vers la PEP1")

## Cycle de vie des PEP

### Commencer avec une idée pour Python

Le processus PEP commence par une nouvelle idée pour Python. Il est fortement recommandé qu'un seul PEP contienne une seule proposition clé ou une nouvelle idée. Les petites améliorations ou les correctifs n'ont souvent pas besoin d'un PEP et peuvent être injectés dans le flux de développement de Python par la soumission d'un correctif dans le Python Issue Tracker [8]. Plus le PEP est ciblé, plus il a tendance à avoir du succès. Les éditeurs du PEP se réservent le droit de rejeter des propositions de PEP si elles semblent trop peu ciblées ou trop larges. En cas de doute, divisez votre PEP en plusieurs PEP bien ciblés.

Chaque PEP doit avoir un champion - quelqu'un qui rédige le PEP en utilisant le style et le format décrits ci-dessous, dirige les discussions dans les forums appropriés, et tente de construire un consensus de la communauté autour de l'idée. Le champion du PEP (alias l'auteur) doit d'abord essayer de vérifier si l'idée peut faire l'objet d'un PEP. La meilleure façon de procéder est de poster un message au newsgroup comp.lang.python (alias liste de diffusion python-list@python.org) ou à la liste de diffusion python-ideas@python.org.

L'examen public d'une idée avant d'aller jusqu'à l'écriture d'un PEP a pour but de faire gagner du temps à l'auteur potentiel. De nombreuses idées ont été proposées pour modifier Python et ont été rejetées pour diverses raisons. Le fait de demander d'abord à la communauté Python si une idée est originale permet d'éviter de passer trop de temps sur quelque chose qui est garanti d'être rejeté sur la base de discussions antérieures (une recherche sur Internet ne fait pas toujours l'affaire). Cela permet également de s'assurer que l'idée est applicable à l'ensemble de la communauté et pas seulement à l'auteur. Ce n'est pas parce qu'une idée semble bonne pour l'auteur qu'elle fonctionnera pour la plupart des gens dans la plupart des domaines où Python est utilisé.

Une fois que le champion a demandé à la communauté Python si une idée a une chance d'être acceptée, un projet de PEP devrait être présenté à python-ideas. Cela donne à l'auteur la possibilité d'étoffer le projet de PEP pour le rendre correctement formaté, de haute qualité, et de répondre aux préoccupations initiales concernant la proposition.

### Soumettre un PEP

Après une discussion sur python-ideas, le flux de travail varie selon que l'un des co-auteurs du PEP est ou non un développeur principal. Si un ou plusieurs des co-auteurs du PEP sont des développeurs principaux, ils sont responsables de suivre le processus décrit ci-dessous. Dans le cas contraire (c'est-à-dire si aucun des co-auteurs n'est un développeur principal), le ou les auteurs du PEP devront trouver un sponsor pour le PEP.

Idéalement, un sponsor développeur principal est identifié, mais des sponsors non principaux peuvent également être sélectionnés avec l'approbation du Conseil de direction. Les membres de l'équipe "éditeurs PEP" de GitHub sont pré-approuvés pour être sponsors. Le rôle du parrain est de fournir des conseils à l'auteur du PEP pour l'aider à gérer la logistique du processus PEP (il agit en quelque sorte comme un mentor). Le fait d'être parrain n'empêche pas cette personne de devenir co-auteur ou délégué PEP par la suite (mais pas les deux). Le sponsor d'un PEP est enregistré dans le champ "Sponsor :" de l'en-tête.

Une fois que le sponsor ou le(s) développeur(s) principal(aux) co-auteur(s) du PEP estime(nt) que le PEP est prêt à être soumis, la proposition doit être soumise en tant que projet de PEP via une demande de retrait GitHub. Le projet doit être rédigé dans le style PEP tel que décrit ci-dessous, sinon il échouera immédiatement à l'examen (bien que des erreurs mineures puissent être corrigées par les rédacteurs).

### Le processus PEP standard

- Vous, l'auteur du PEP, ouvrez le dépôt PEP, et créez un fichier nommé pep-9999.rst qui contient votre nouveau PEP. Utilisez "9999" comme numéro de projet PEP.
- Dans le champ d'en-tête "Type :", entrez "Standards Track", "Informational", ou "Process" selon le cas, et dans le champ "Status :" entrez "Draft". Pour plus de détails, voir le préambule de l'en-tête PEP.
- Mettez à jour le fichier .github/CODEOWNERS de façon à ce que les co-auteurs ou les sponsors des développeurs principaux soient répertoriés pour votre nouveau fichier, afin que toute demande de retrait future leur soit attribuée.
- Poussez-le vers votre fork GitHub et soumettez une demande de retrait.
- Les rédacteurs PEP examinent votre PR pour vérifier la structure, le formatage et les autres erreurs. Pour un PEP formaté en reST, le PEP 12 est fourni comme modèle. Il fournit également une introduction complète au balisage reST qui est utilisé dans les PEP. Les critères d'approbation sont :
- Il est solide et complet. Les idées doivent avoir un sens technique. Les rédacteurs ne se demandent pas si elles ont des chances d'être acceptées.
- Le titre décrit fidèlement le contenu.
- Le langage du PEP (orthographe, grammaire, structure des phrases, etc.) et le style de code (les exemples doivent correspondre aux PEP 8 & PEP 7) doivent être corrects et conformes. Le formatage du PEP (texte brut ou reStructuredText) sera vérifié par Travis CI, et le PEP ne sera pas approuvé tant qu'il ne sera pas accepté.
- Les éditeurs sont généralement assez indulgents à l'égard de cet examen initial, espérant que les problèmes seront corrigés par le processus de révision. Remarque : l'approbation du PEP ne garantit pas l'absence d'erreurs embarrassantes ! La correction est la responsabilité des auteurs et des réviseurs, et non des éditeurs.
- Si le PEP n'est pas prêt à être approuvé, un éditeur le renverra à l'auteur pour révision, avec des instructions spécifiques.
- Une fois approuvé, il attribuera un numéro à votre PEP.
- Une fois que le processus de révision est terminé, et que les éditeurs PEP l'approuvent (notez que ce n'est pas la même chose que d'accepter votre PEP !), ils commettent votre pull request sur main.
- Les éditeurs PEP ne refuseront pas sans raison la publication d'un PEP. Les raisons de refuser le statut de PEP incluent la duplication d'efforts, le manque de solidité technique, l'absence de motivation appropriée ou de compatibilité ascendante, ou le non-respect de la philosophie Python. Le conseil de direction peut être consulté pendant la phase d'approbation et est l'arbitre final de l'aptitude d'un projet à devenir PEP.
- Les développeurs ayant des privilèges git push pour le dépôt PEP peuvent réclamer des numéros PEP directement en créant et en soumettant un nouveau PEP. Ce faisant, le développeur doit s'occuper des tâches qui seraient normalement prises en charge par les éditeurs PEP (voir Responsabilités et flux de travail des éditeurs PEP). Il doit notamment s'assurer que la version initiale répond aux normes attendues pour la soumission d'un PEP. Alternativement, même les développeurs devraient soumettre les PEP par pull request. Si vous avez besoin de l'aide des éditeurs PEP, mentionnez @python/pep-editors sur GitHub.
- Lorsque des mises à jour sont nécessaires, l'auteur du PEP peut enregistrer les nouvelles versions s'il (ou un développeur collaborateur) dispose de privilèges git push.
- Après l'attribution d'un numéro PEP, un projet de PEP peut faire l'objet d'une discussion plus approfondie sur python-ideas (l'attribution précoce d'un numéro PEP peut être utile pour faciliter les références, en particulier lorsque plusieurs projets PEP sont examinés en même temps). Finalement, tous les PEP de la piste des standards doivent être envoyés à la liste python-dev pour révision, comme décrit dans la section suivante.
- Les Standards Track PEPs sont constitués de deux parties, un document de conception et une implémentation de référence. Il est généralement recommandé qu'au moins un prototype d'implémentation soit co-développé avec le PEP, car les idées qui semblent bonnes en principe se révèlent parfois peu pratiques lorsqu'elles sont soumises au test de l'implémentation.
- Les auteurs de PEP sont responsables de la collecte des commentaires de la communauté sur un PEP avant de le soumettre à l'examen. Toutefois, dans la mesure du possible, il convient d'éviter les longues discussions ouvertes sur les listes de diffusion publiques. Les stratégies pour maintenir l'efficacité des discussions comprennent : la création d'une liste de diffusion SIG distincte pour le sujet, l'acceptation par l'auteur du PEP de commentaires privés dans les premières phases de conception, la création d'une page wiki, etc. Les auteurs de PEP doivent faire preuve de discrétion à cet égard.

## Révision et résolution des PEP

Une fois que les auteurs ont terminé un PEP, ils peuvent demander une révision du style et de la cohérence aux éditeurs du PEP.

Cependant, la révision du contenu et l'acceptation finale du PEP doivent être demandées aux développeurs du noyau, généralement par le biais d'un courriel à la liste de diffusion python-dev.

Pour accélérer le processus dans certains cas (par exemple, lorsqu'une modification est clairement bénéfique et prête à être acceptée, mais que le PEP n'a pas encore été officiellement soumis à l'examen), le conseil de direction peut également initier une révision du PEP, en informant d'abord l'auteur ou les auteurs du PEP et en leur donnant une chance de faire des révisions.

L'autorité finale pour l'approbation du PEP est le Conseil de direction. Cependant, chaque fois qu'un nouveau PEP est proposé, tout développeur du noyau qui estime avoir l'expérience nécessaire pour prendre la décision finale sur ce PEP peut proposer de servir de délégué PEP pour ce PEP, et il aura alors l'autorité d'approuver (ou de rejeter) ce PEP. Les personnes assumant cette responsabilité sont libres de demander des conseils supplémentaires au Conseil de pilotage à tout moment, et sont également censées prendre en compte les conseils et les perspectives des autres développeurs principaux.

Le décideur désigné pour chaque PEP est enregistré dans l'en-tête "PEP-Delegate" du PEP.

Ces auto-nominations sont acceptées par défaut, mais peuvent être explicitement refusées par le Conseil de direction. Les raisons possibles pour lesquelles le conseil de direction refuse une nomination en tant que PEP-Delegate incluent, mais ne sont pas limitées à, la perception d'un conflit d'intérêts potentiel (par exemple, travailler pour la même organisation que l'auteur du PEP), ou simplement considérer qu'un autre PEP-Delegate potentiel est plus approprié. Si les développeurs principaux (ou d'autres membres de la communauté) ont des doutes quant à l'adéquation d'un délégué PEP pour un PEP donné, ils peuvent demander au conseil de pilotage de revoir la délégation.

Si aucun volontaire ne se manifeste, le conseil de pilotage contactera les principaux développeurs (et potentiellement d'autres membres de la communauté Python) ayant une expertise pertinente, afin d'identifier un candidat prêt à servir de délégué PEP pour ce PEP. Si aucun candidat approprié ne peut être trouvé, le PEP sera marqué comme différé jusqu'à ce qu'un candidat soit disponible.

Les délégués PEP précédemment nommés peuvent choisir de se retirer ou être invités à le faire par le Conseil, auquel cas un nouveau délégué PEP sera nommé de la même manière que pour un nouveau PEP (y compris le report du PEP si aucun remplaçant approprié ne peut être trouvé). Dans le cas où il est demandé à un Délégué PEP de se retirer, cela annulera toute acceptation ou rejet préalable du PEP, et celui-ci reprendra le statut de projet.

Avec l'approbation du conseil de direction, l'examen et la résolution des PEP peuvent également avoir lieu sur une liste autre que python-dev (par exemple, distutils-sig pour les PEP liés au packaging qui n'affectent pas immédiatement la bibliothèque standard). Dans ces cas, la rubrique "Discussions-To" du PEP identifiera la liste alternative appropriée où la discussion, l'examen et la prise de position sur le PEP auront lieu.

Lorsque de telles délégations permanentes sont mises en place, le conseil de direction conservera suffisamment de documents publics pour permettre aux conseils suivants, aux développeurs du noyau et à la communauté Python au sens large de comprendre les délégations qui existent actuellement, les raisons pour lesquelles elles ont été mises en place et les circonstances dans lesquelles elles peuvent ne plus être nécessaires.

Pour qu'un PEP soit accepté, il doit répondre à certains critères minimums. Il doit s'agir d'une description claire et complète de l'amélioration proposée. L'amélioration doit représenter une amélioration nette. La mise en œuvre proposée, le cas échéant, doit être solide et ne doit pas compliquer indûment la tâche de l'interprète. Enfin, une amélioration proposée doit être "pythonique" pour être acceptée par le Conseil directeur. (Cependant, "pythonique" est un terme imprécis ; il peut être défini comme tout ce qui est acceptable pour le Conseil directeur. Cette logique est intentionnellement circulaire). Voir PEP 2 pour les critères d'acceptation des modules de bibliothèque standard.

Une fois qu'un PEP a été accepté, la mise en œuvre de référence doit être achevée. Lorsque l'implémentation de référence est terminée et incorporée dans le dépôt de code source principal, le statut sera changé en "Final".

Pour permettre de recueillir des commentaires supplémentaires sur la conception et l'interface avant de s'engager à assurer la stabilité à long terme d'une fonctionnalité du langage ou d'une API de bibliothèque standard, un PEP peut également être marqué comme "provisoire". Cette mention est l'abréviation de "Provisionally Accepted", et indique que la proposition a été acceptée pour être incluse dans l'implémentation de référence, mais que des commentaires supplémentaires de la part des utilisateurs sont nécessaires avant que la conception complète puisse être considérée comme "Finale". Contrairement aux PEPs acceptés régulièrement, les PEPs acceptés provisoirement peuvent encore être rejetés ou retirés même après que les changements associés aient été inclus dans une version de Python.

Dans la mesure du possible, il est considéré comme préférable de réduire la portée d'une proposition afin d'éviter de devoir compter sur le statut "Provisional" (par exemple en reportant certaines fonctionnalités à des PEP ultérieures), car ce statut peut entraîner des problèmes de compatibilité de version dans l'écosystème Python au sens large. Le PEP 411 fournit des détails supplémentaires sur les cas d'utilisation potentiels du statut "Provisional".

Un PEP peut également se voir attribuer le statut "Deferred". L'auteur du PEP ou un éditeur peut attribuer ce statut au PEP lorsqu'aucun progrès n'est réalisé sur le PEP. Une fois qu'un PEP est différé, le rédacteur du PEP peut le réaffecter au statut de projet.

Un PEP peut également être "rejeté". Peut-être qu'après tout ce qui a été dit et fait, ce n'était pas une bonne idée. Il est néanmoins important d'avoir une trace de ce fait. Le statut "Withdrawn" est similaire - il signifie que l'auteur du PEP lui-même a décidé que le PEP était en fait une mauvaise idée, ou a accepté qu'une proposition concurrente soit une meilleure alternative.

Lorsqu'un PEP est Accepté, Rejeté ou Retiré, le PEP doit être mis à jour en conséquence. En plus de la mise à jour du champ de statut, il faut au moins ajouter l'en-tête Resolution avec un lien vers le message correspondant dans les archives de la liste de diffusion python-dev.

Les PEP peuvent également être remplacés par un autre PEP, rendant l'original obsolète. Ceci est prévu pour les PEP informationnels, où la version 2 d'une API peut remplacer la version 1.

## Les chemins possibles de l'état des PEP

### Diagramme du processus PEP

Bien que cela n'apparaisse pas dans le diagramme, les PEP "acceptés" peuvent techniquement passer à "rejetés" ou "retirés" même après leur acceptation. Cela ne se produira que si le processus de mise en œuvre révèle des défauts fondamentaux dans la conception qui n'ont pas été remarqués avant l'acceptation du PEP. Contrairement aux PEP provisoires, ces transitions ne sont permises que si la proposition acceptée n'a pas été incluse dans une version de Python - les changements publiés doivent plutôt passer par le processus régulier de dépréciation (qui peut nécessiter un nouveau PEP fournissant la justification de la dépréciation).

Certains PEP informationnels et de processus peuvent aussi avoir un statut "actif" s'ils ne sont jamais destinés à être complétés. Par exemple, le PEP 1 (ce PEP).

### Maintenance des PEP

En général, les PEP de la voie des normes ne sont plus modifiés après avoir atteint l'état final. Une fois qu'un PEP a été achevé, les références du langage et de la bibliothèque standard deviennent la documentation formelle du comportement attendu.

Si des modifications basées sur l'expérience de mise en œuvre et les commentaires des utilisateurs sont apportées aux PEP de la filière Normes alors qu'ils sont dans l'état Accepté ou Provisoire, ces modifications doivent être notées dans le PEP, de sorte que le PEP décrive précisément l'état de la mise en œuvre au moment où il est marqué Final.

Les PEP informationnels et de processus peuvent être mis à jour au fil du temps pour refléter les changements dans les pratiques de développement et d'autres détails. Le processus précis suivi dans ces cas dépendra de la nature et de l'objectif du PEP mis à jour.

### Que doit contenir un PEP réussi ?

Chaque PEP devrait comporter les parties/sections suivantes :

- **Préambule** - En-têtes de style RFC 822 contenant des méta-données sur le PEP, y compris le numéro du PEP, un court titre descriptif (limité à un maximum de 44 caractères), les noms, et éventuellement les coordonnées de chaque auteur, etc.
- **Résumé** - une brève description (~200 mots) de la question technique abordée.
- **Motivation** - La motivation est essentielle pour les PEP qui veulent changer le langage, la bibliothèque ou l'écosystème Python. Elle doit expliquer clairement pourquoi la spécification existante du langage est inadéquate pour répondre au problème que le PEP résout. Cela peut inclure la collecte d'un soutien documenté pour le PEP auprès de projets importants dans l'écosystème Python. Les soumissions de PEP sans motivation suffisante peuvent être rejetées.
- **Justification** - La justification étoffe la spécification en décrivant pourquoi certaines décisions de conception ont été prises. Elle doit décrire les autres conceptions envisagées et les travaux connexes, par exemple la manière dont la fonctionnalité est prise en charge dans d'autres langages.
La justification doit fournir la preuve du consensus au sein de la communauté et discuter des objections ou des préoccupations importantes soulevées au cours de la discussion.
- **Spécification** - La spécification technique doit décrire la syntaxe et la sémantique de toute nouvelle fonctionnalité du langage. La spécification doit être suffisamment détaillée pour permettre des implémentations concurrentes et interopérables pour au moins les principales plateformes Python actuelles (CPython, Jython, IronPython, PyPy).
- **Compatibilité rétroactive** - Tous les PEP qui introduisent des incompatibilités rétroactives doivent inclure une section décrivant ces incompatibilités et leur gravité. Le PEP doit expliquer comment l'auteur propose de traiter ces incompatibilités. Les PEP soumis sans un traité de rétrocompatibilité suffisant peuvent être rejetés d'emblée.
- **Implications en matière de sécurité** - S'il y a des problèmes de sécurité en relation avec le PEP, ces problèmes doivent être explicitement écrits pour s'assurer que les réviseurs du PEP en sont conscients.
- **Comment l'enseigner** - Pour un PEP qui ajoute une nouvelle fonctionnalité ou change le comportement du langage, il est utile d'inclure une section sur la façon d'enseigner aux utilisateurs, nouveaux et expérimentés, comment appliquer le PEP à leur travail.
Cette section peut inclure les points clés et les changements recommandés dans la documentation qui aideraient les utilisateurs à adopter une nouvelle fonctionnalité ou à migrer leur code pour utiliser un changement de langage.
- **Mise en œuvre de référence** - La mise en œuvre de référence doit être achevée avant qu'un PEP ne reçoive le statut "Final", mais elle ne doit pas nécessairement être achevée avant que le PEP ne soit accepté. Bien que l'approche consistant à atteindre un consensus sur la spécification et le raisonnement avant d'écrire le code présente des avantages, le principe du "consensus approximatif et de l'exécution du code" est toujours utile lorsqu'il s'agit de résoudre de nombreuses discussions sur les détails de l'API.
L'implémentation finale doit inclure du code de test et une documentation appropriée pour la référence du langage Python ou la référence de la bibliothèque standard.
- **Idées rejetées** - Tout au long de la discussion d'un PEP, diverses idées seront proposées qui ne seront pas acceptées. Ces idées rejetées doivent être enregistrées avec les raisons de leur rejet. Cela permet à la fois d'enregistrer le processus de réflexion qui sous-tend la version finale du PEP et d'éviter que des personnes ne remettent sur le tapis la même idée rejetée lors de discussions ultérieures.
D'une certaine manière, cette section peut être considérée comme une section secondaire de la section Rationale qui se concentre spécifiquement sur les raisons pour lesquelles certaines idées n'ont pas été retenues.
- **Questions en suspens** - Lorsqu'un PEP est à l'état de projet, des idées peuvent surgir et justifier une discussion plus approfondie. Ces idées doivent être consignées afin que les gens sachent qu'elles font l'objet d'une réflexion mais n'ont pas de résolution concrète. Cela permet de s'assurer que toutes les questions requises pour que le PEP soit prêt à être examiné sont complètes et d'éviter que des personnes ne répètent des discussions antérieures.
- **Références** - Une collection d'URLs utilisés comme références à travers le PEP.
- **Copyright/licence** - Chaque nouveau PEP doit être placé sous une double licence de domaine public et CC0-1.0-Universal (voir ce PEP pour un exemple).

## Formats et modèles de PEP

Les PEP sont des fichiers texte codés UTF-8 utilisant le format reStructuredText. ReStructuredText permet un balisage riche qui reste assez facile à lire, mais donne également un HTML fonctionnel et de bonne qualité. Le PEP 12 contient des instructions et un modèle pour les PEP reStructuredText.

Les fichiers texte PEP sont automatiquement convertis en HTML pour faciliter la lecture en ligne.

### Préambule de l'en-tête du PEP

Chaque PEP doit commencer par un préambule d'en-tête de style RFC 822. Les en-têtes doivent apparaître dans l'ordre suivant. Les en-têtes marqués d'un "*" sont facultatifs et sont décrits ci-dessous. Tous les autres en-têtes sont obligatoires.

```txt
PEP: <pep number>
Title: <pep title>
Author: <list of authors' real names and optionally, email addrs>
* Sponsor: <real name of sponsor>
* PEP-Delegate: <PEP delegate's real name>
* Discussions-To: <email address or URL>
Status: <Draft | Active | Accepted | Provisional | Deferred | Rejected |
            Withdrawn | Final | Superseded>
Type: <Standards Track | Informational | Process>
* Content-Type: <text/x-rst | text/plain>
* Requires: <pep numbers>
Created: <date created on, in dd-mmm-yyyy format>
* Python-Version: <version number>
Post-History: <dates of postings to python-ideas and/or python-dev>
* Replaces: <pep number>
* Superseded-By: <pep number>
* Resolution: <url>
```

L'en-tête Author liste les noms, et éventuellement les adresses électroniques de tous les auteurs/propriétaires du PEP. Le format de la valeur de l'en-tête Author doit être le suivant: ```Random J. User <address@dom.ain>``` si l'adresse électronique est incluse, et simplement: ```Random J. User``` si l'adresse n'est pas indiquée. Pour des raisons historiques, le format "address@dom.ain (Random J. User)" peut apparaître dans un PEP, mais les nouveaux PEP doivent utiliser le format obligatoire ci-dessus, et il est acceptable de passer à ce format lorsque les PEP sont mis à jour.

S'il y a plusieurs auteurs, chacun d'entre eux doit être sur une ligne séparée en suivant les conventions de la ligne de continuation de la RFC 2822. Notez que les adresses électroniques personnelles dans les PEP seront masquées afin de se défendre contre les collecteurs de spam.

Le champ Sponsor enregistre le développeur (noyau, ou autrement approuvé par le Conseil de direction) qui sponsorise le PEP. Si l'un des auteurs du PEP est un développeur principal, aucun sponsor n'est nécessaire et ce champ ne doit pas être rempli.

Le champ PEP-Délégué est utilisé pour enregistrer la personne désignée par le conseil de direction pour prendre la décision finale d'approuver ou de rejeter un PEP. (L'adresse électronique du délégué est actuellement omise en raison d'une limitation du masquage des adresses électroniques pour les PEP en texte reStructuré).

__Remarque__ : L'en-tête Resolution est requis uniquement pour les PEP de type "Standards Track". Il contient une URL qui doit pointer vers un message électronique ou une autre ressource web où la déclaration concernant le PEP est faite.

Pour un PEP dont la déclaration finale sera faite sur une liste autre que python-dev, un en-tête Discussions-To indiquera la liste de diffusion ou l'URL où la déclaration aura lieu. Un en-tête Discussions-To temporaire peut également être utilisé lorsqu'un projet de PEP fait l'objet de discussions avant d'être soumis à la décision finale. Aucun en-tête Discussions-To n'est nécessaire si le PEP est discuté en privé avec l'auteur, ou sur les listes de diffusion python-list, python-ideas ou python-dev. Notez que les adresses électroniques figurant dans l'en-tête Discussions-To ne seront pas masquées.

L'en-tête Type spécifie le type de PEP : Standards Track, Informational, ou Process.

Le format d'un PEP est spécifié par l'en-tête Content-Type. Les valeurs acceptables sont "text/plain" pour les PEP en texte clair (voir PEP 9) et "text/x-rst" pour les PEP en reStructuredText (voir PEP 12). reStructuredText est fortement préféré, mais pour des raisons de compatibilité ascendante, le texte clair reste actuellement la valeur par défaut si aucun en-tête Content-Type n'est présent.

L'en-tête Created enregistre la date à laquelle un numéro a été attribué au PEP, tandis que Post-History est utilisé pour enregistrer les dates auxquelles de nouvelles versions du PEP sont publiées sur python-ideas et/ou python-dev. Les deux en-têtes doivent être au format jj-mmm-aaaa, par exemple 14 août 2001.

Les Standards Track PEPs ont généralement un en-tête Python-Version qui indique la version de Python avec laquelle la fonctionnalité sera publiée. Les Standards Track PEPs sans en-tête Python-Version indiquent des standards d'interopérabilité qui seront initialement supportés par des bibliothèques et des outils externes, et qui seront éventuellement complétés par un PEP ultérieur pour ajouter le support à la bibliothèque standard. Les PEP informationnels et de processus n'ont pas besoin d'un en-tête Python-Version.

Les PEP peuvent avoir un en-tête Requires, indiquant les numéros des PEP dont elles dépendent.

Les PEP peuvent aussi avoir un en-tête Superseded-By indiquant qu'un PEP a été rendu obsolète par un document ultérieur ; la valeur est le numéro du PEP qui remplace le document actuel. Le PEP le plus récent doit avoir un en-tête Replaces contenant le numéro du PEP qu'il a rendu obsolète.

### Fichiers auxiliaires

Les PEP peuvent inclure des fichiers auxiliaires tels que des diagrammes. Ces fichiers doivent être nommés pep-XXXX-Y.ext, où "XXXX" est le numéro du PEP, "Y" est un numéro de série (commençant à 1), et "ext" est remplacé par l'extension réelle du fichier (par exemple "png").

Il est également possible de placer tous les fichiers de support dans un sous-répertoire appelé pep-XXXX, où "XXXX" est le numéro PEP. Lorsqu'on utilise un sous-répertoire, il n'y a aucune contrainte sur les noms utilisés dans les fichiers.

### Signaler des bogues PEP ou soumettre des mises à jour PEP

La manière de signaler un bug ou de soumettre une mise à jour PEP dépend de plusieurs facteurs, tels que la maturité du PEP, les préférences de l'auteur du PEP et la nature de vos commentaires. Pour les premières étapes du PEP, il est probablement préférable d'envoyer vos commentaires et modifications directement à l'auteur du PEP. Pour les PEP plus matures ou terminés, vous pouvez soumettre les corrections sous forme de problème GitHub ou de demande de retrait GitHub afin que vos modifications ne se perdent pas.

En cas de doute sur l'endroit où envoyer vos modifications, vérifiez d'abord avec l'auteur du PEP et/ou un éditeur du PEP.

Les auteurs PEP ayant des privilèges git push pour le dépôt PEP peuvent mettre à jour les PEP eux-mêmes en utilisant "git push" ou l'interface GitHub PR pour soumettre leurs changements.

### Transfert de propriété des PEP

Il est parfois nécessaire de transférer la propriété des PEP à un nouveau champion. En général, il est préférable de garder l'auteur original comme co-auteur du PEP transféré, mais c'est à l'auteur original d'en décider. Une bonne raison de transférer la propriété est que l'auteur original n'a plus le temps ou l'intérêt de le mettre à jour ou de suivre le processus PEP, ou qu'il a disparu de la surface du net (c'est-à-dire qu'il est injoignable ou ne répond pas aux e-mails). Une mauvaise raison de transférer la propriété est que l'auteur n'est pas d'accord avec l'orientation du PEP. Un des objectifs du processus PEP est d'essayer de construire un consensus autour d'un PEP, mais si ce n'est pas possible, un auteur peut toujours soumettre un PEP concurrent.

Si vous souhaitez vous approprier un PEP, vous pouvez également le faire par le biais d'une pull request. Forkez le dépôt PEP, faites votre modification de propriété, et soumettez une pull request. Vous devez mentionner l'auteur original et @python/pep-editors dans un commentaire sur la demande de téléchargement. (Si le nom d'utilisateur GitHub de l'auteur original est inconnu, utilisez l'email). Si l'auteur original ne répond pas en temps voulu, les éditeurs PEP prendront une décision unilatérale (ce n'est pas comme si de telles décisions ne pouvaient pas être inversées :).

### Responsabilités de l'éditeur PEP et déroulement des opérations

Un éditeur PEP doit être ajouté au groupe @python/pep-editors sur GitHub et doit surveiller le dépôt PEP.

Notez que les développeurs ayant des privilèges git push pour le dépôt PEP peuvent s'occuper des tâches qui seraient normalement prises en charge par les éditeurs PEP. Alternativement, même les développeurs peuvent demander l'aide des éditeurs PEP en mentionnant @python/pep-editors sur GitHub.

Pour chaque nouveau PEP qui arrive, un éditeur fait ce qui suit :

- S'assurer que le PEP est soit co-écrit par un développeur principal, qu'il a un développeur principal comme parrain, ou qu'il a un parrain spécifiquement approuvé pour ce PEP par le Conseil de pilotage.
- Lisez le PEP pour vérifier s'il est prêt : solide et complet. Les idées doivent avoir un sens technique, même si elles ne semblent pas avoir de chances d'être acceptées.
- Le titre doit décrire avec précision le contenu.
- L'extension du nom de fichier est correcte (c'est-à-dire .rst).
- Assurez-vous que le ou les développeurs principaux appropriés sont ajoutés à .github/CODEOWNERS.
- Parcourez le PEP à la recherche de défauts évidents dans la langue (orthographe, grammaire, structure des phrases, etc.) et dans le style du code (les exemples doivent être conformes aux PEP 8 et PEP 7). Les rédacteurs peuvent corriger eux-mêmes les problèmes, mais ne sont pas tenus de le faire. (Le format du texte est vérifié par Travis CI).
- Si un projet est présenté comme bénéficiant de la PEP ou la soutenant, assurez-vous qu'il y a une indication directe du projet inclus pour rendre le soutien clair. Ceci afin d'éviter qu'un PEP ne présente accidentellement un projet comme soutenant un PEP alors qu'en fait ce soutien est basé sur des conjectures.
- Si le PEP n'est pas prêt, un éditeur le renverra à l'auteur pour révision, avec des instructions spécifiques. Si le formatage du PEP pose problème, demandez à l'auteur d'utiliser le PEP 12 comme modèle et de le soumettre à nouveau.

Une fois que le PEP est prêt pour le dépôt, un rédacteur PEP va :

- Attribuer un numéro PEP (presque toujours le prochain numéro disponible, mais parfois c'est un numéro spécial/de plaisanterie, comme 666 ou 3141). (Clarification : Pour Python 3, les numéros dans les 3000s étaient utilisés pour les propositions spécifiques à Py3k. Mais maintenant que toutes les nouvelles fonctionnalités ne sont intégrées qu'à Python 3, le processus revient à l'utilisation de nombres dans les 100. N'oubliez pas que les nombres inférieurs à 100 sont des méta-PEPs).
- Vérifiez que l'auteur a correctement étiqueté le type du PEP ("Standards Track", "Informational", ou "Process"), et marqué son statut comme "Draft".
- Ajoutez le PEP à un fork local du dépôt PEP. Pour des instructions sur le flux de travail, suivez The Python Developers Guide.

Le dépôt git pour les PEP est : [https://github.com/python/peps](https://github.com/python/peps, "dépôt git pour les PEP")

Exécutez ```./genpepindex.py``` et ```./pep2html.py <numéro PEP>``` pour vous assurer qu'ils sont générés sans erreur. Si l'un ou l'autre déclenche des erreurs, alors le site web ne sera pas mis à jour pour refléter les changements PEP.

Commit et push du nouveau PEP (ou de la mise à jour)

Surveillez python.org pour vous assurer que le PEP est ajouté au site correctement. S'il n'apparaît pas, lancer make pour construire tous les PEP actuels. Si l'un d'entre eux déclenche des erreurs, il doit être corrigé avant que le PEP ne soit mis à jour sur le site.

Envoyez un email à l'auteur du PEP avec les prochaines étapes (postez sur python-list & -dev).

Les mises à jour des PEP existants doivent être soumises sous forme de pull request GitHub.

De nombreux PEP sont écrits et maintenus par des développeurs ayant un accès en écriture au code source de Python. Les éditeurs de PEP surveillent les modifications apportées au dépôt PEP et corrigent les erreurs de structure, de grammaire, d'orthographe ou de balisage qu'ils voient.

Les éditeurs PEP ne portent pas de jugement sur les PEP. Ils s'occupent simplement de la partie administrative et éditoriale (qui est généralement une tâche de faible volume).
