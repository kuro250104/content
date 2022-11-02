## Qu'est-ce que les PEP ?

Pour répondre à  cette question, il faut se référer au PEP1:

<a href="https://www.python.org/dev/peps/pep-0001/" target="_blank" title="PEP 1 Python">https://www.python.org/dev/peps/pep-0001/</a>

En voici la traduction:

> PEP est l'abréviation de Python Enhancement Proposal. Un PEP est un document de conception fournissant des informations à la communauté Python, ou décrivant une nouvelle fonctionnalité pour Python, ses processus ou son environnement. Le PEP doit fournir une spécification technique concise de la fonctionnalité et une justification de cette dernière.
> Nous souhaitons que les PEP soient les principaux mécanismes permettant de proposer de nouvelles fonctionnalités majeures, de recueillir les commentaires de la communauté sur une question et de documenter les décisions de conception prises pour Python. L'auteur du PEP est chargé d'établir un consensus au sein de la communauté et de documenter les opinions divergentes.
> Étant donné que les PEP sont conservés sous forme de fichiers texte dans un dépôt de versions, l'historique de leurs révisions constitue l'enregistrement historique de la proposition de fonctionnalité.

Cette explication sur les PEP nous permet de souligner l’importance de la communauté Python. Elle est ce qui fait vivre et évoluer ce langage. Cette communauté est grande et répandue. Il est donc aisé de trouver des développeurs susceptibles de vous aider si vous rencontrez des difficultés.

## Qui sont les destinataires des PEP ?

Encore une fois, référons-nous à la PEP1: 

> Les principaux destinataires des PEP sont généralement les développeurs de l'interpréteur de référence CPython et leur conseil de direction élu, ainsi que les développeurs d'autres implémentations de la spécification du langage Python.
> Cependant, d'autres parties de la communauté Python peuvent également choisir d'utiliser le processus (en particulier pour les PEP informationnels) pour documenter les conventions d'API attendues et pour gérer les problèmes complexes de coordination de la conception qui nécessitent une collaboration entre plusieurs projets.

## Quels sont les différents types de PEP ?

Vous l’aurez deviné, toutes les réponses aux questions qu’on peut se poser sur les PEP sont contenues dans la PEP1:

> Il existe trois types de PEP :
> - Un **Standards Track PEP** décrit une nouvelle fonctionnalité ou une nouvelle implémentation pour Python. Il peut également décrire un standard d'interopérabilité qui sera supporté en dehors de la bibliothèque standard pour les versions actuelles de Python avant qu'un PEP ultérieur n'ajoute le support de la bibliothèque standard dans une version future.
> - Une **PEP informationnelle** décrit un problème de conception de Python, ou fournit des directives ou des informations générales à la communauté Python, mais ne propose pas de nouvelle fonctionnalité. Les Informational PEP ne représentent pas nécessairement un consensus ou une recommandation de la communauté Python. Les utilisateurs et les implémenteurs sont donc libres d'ignorer les Informational PEP ou de suivre leurs conseils.
> - Un **Process PEP** décrit un processus autour de Python, ou propose un changement à (ou un événement dans) un processus. Les Process PEP sont comme les Standards Track PEP mais s'appliquent à d'autres domaines que le langage Python lui-même. Elles peuvent proposer une implémentation, mais pas au codebase de Python ; elles requièrent souvent un consensus de la communauté ; contrairement aux PEP informationnelles, elles sont plus que des recommandations, et les utilisateurs ne sont généralement pas libres de les ignorer. Les exemples incluent les procédures, les directives, les changements dans le processus de prise de décision, et les changements dans les outils ou l'environnement utilisés dans le développement de Python. Toute méta-PEP est également considérée comme une Process PEP.

Ainsi, la PEP1 est une PEP informationnelle.

## Le conseil de pilotage de Python

> Il y a plusieurs références dans ce PEP au "Conseil de pilotage" ou "Conseil". Il s'agit des membres actuels du conseil de direction élu décrit dans le PEP 13, dans leur rôle d'autorité finale pour l'acceptation ou le rejet des PEP.

## Les développeurs principaux de Python

> Il est fait référence à plusieurs reprises dans ce PEP aux "core developers". Il s'agit des membres actifs de l'équipe centrale de Python décrits dans le PEP 13.

## La BDFL de Python

> Les versions précédentes de ce PEP utilisaient le titre "BDFL-Delegate" pour les décideurs du PEP. Il s'agissait d'une référence historique au modèle de gouvernance précédent de Python, où toute l'autorité de conception provenait en fin de compte de Guido van Rossum, le créateur original du langage de programmation Python. En revanche, l'autorité de conception du conseil de direction découle de son élection par les développeurs principaux actuellement actifs. Désormais, le délégué PEP est utilisé à la place du délégué BDFL.

## Rédacteurs PEP

> Les éditeurs PEP sont des personnes responsables de la gestion des aspects administratifs et éditoriaux du flux de travail PEP (par exemple, l'attribution de numéros PEP et la modification de leur statut). Voir Responsabilités et flux de travail des éditeurs PEP pour plus de détails.
> Les éditeurs PEP sont invités par les éditeurs actuels, et ils peuvent être contactés en mentionnant ```@python/pep-editors``` sur GitHub. L'ensemble du flux de travail PEP peut être réalisé via les questions et les demandes de retrait du dépôt PEP de GitHub.

## Autres informations à retenir

Cette PEP a aussi pour but de décrire à la communauté le cycle  de vie des PEP ainsi que la façon de créer des PEP pour faire évoluer le langage.