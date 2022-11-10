## Qu'est-ce que Node.js ?

Node.js est une plateforme côté serveur construite sur le moteur JavaScript de Google Chrome (moteur V8). Node.js a été développé par Ryan Dahl en 2009 et sa dernière version est v0.10.36. La définition de Node.js telle qu'elle est fournie par sa documentation officielle est la suivante.

__Remarque__ : Node.js est une plateforme construite sur le moteur d'exécution JavaScript de Chrome pour créer facilement des applications réseau rapides et évolutives. Node.js utilise un modèle d'E/S non bloquant et piloté par les événements qui le rend léger et efficace, parfait pour les applications en temps réel gourmandes en données qui s'exécutent sur des périphériques distribués.

Node.js est un environnement d'exécution multiplateforme à code source ouvert pour le développement d'applications côté serveur et en réseau. Les applications Node.js sont écrites en JavaScript et peuvent être exécutées dans le runtime Node.js sur OS X, Microsoft Windows et Linux.

Node.js fournit également une riche bibliothèque de divers modules JavaScript qui simplifie dans une large mesure le développement d'applications Web à l'aide de Node.js.

```bash
Node.js = Runtime Environment + JavaScript Library
```
## Caractéristiques de Node.js

Voici quelques-unes des caractéristiques importantes qui font de Node.js le premier choix des architectes de logiciels.

- **Asynchrone et piloté par les événements** - Toutes les API de la bibliothèque Node.js sont asynchrones, c'est-à-dire non bloquantes. Cela signifie essentiellement qu'un serveur basé sur Node.js n'attend jamais qu'une API renvoie des données. Le serveur passe à l'API suivante après l'avoir appelée et un mécanisme de notification des événements de Node.js aide le serveur à obtenir une réponse de l'appel API précédent.
- **Très rapide** - Construite sur le moteur JavaScript V8 de Google Chrome, la bibliothèque Node.js est très rapide dans l'exécution du code.
- **Monofilière mais hautement évolutive** - Node.js utilise un modèle monofilière avec boucle d'événements. Le mécanisme d'événements aide le serveur à répondre de manière non bloquante et rend le serveur hautement évolutif, contrairement aux serveurs traditionnels qui créent un nombre limité de threads pour traiter les demandes. Node.js utilise un programme à fil unique et le même programme peut fournir un service à un nombre beaucoup plus important de demandes que les serveurs traditionnels comme Apache HTTP Server.
- **Pas de mise en mémoire tampon** - Les applications Node.js ne mettent jamais de données en mémoire tampon. Ces applications produisent simplement les données par morceaux.
- **Licence** - Node.js est publié sous la licence MIT.

## Qui utilise Node.js ?

Voici le lien sur github wiki contenant une liste exhaustive de projets, d'applications et d'entreprises qui utilisent Node.js. Cette liste comprend eBay, General Electric, GoDaddy, Microsoft, PayPal, Uber, Wikipins, Yahoo ! et Yammer pour n'en citer que quelques-uns.

<a href="https://github.com/nodejs/node-v0.x-archive/wiki/projects,-applications,-and-companies-using-node" title="Lien github wiki Noedjs" target="_blank">https://github.com/nodejs/node-v0.x-archive/wiki/projects,-applications,-and-companies-using-node</a>

## Concepts

Le diagramme suivant décrit certaines parties importantes de Node.js que nous aborderons en détail dans les chapitres suivants.

![diagramme decrivant les concepts de Nodejs](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Nodejs/0010%20-%20Introduction/images/image1.jpg)

## Où utiliser Node.js ?

Voici les domaines dans lesquels Node.js se révèle être un partenaire technologique parfait.

- Applications liées aux E/S
- Applications de flux de données
- Applications de données intensives en temps réel (DIRT)
- Applications basées sur les API JSON
- Applications à page unique

## Où ne pas utiliser Node.js ?

Il n'est pas conseillé d'utiliser Node.js pour des applications gourmandes en ressources CPU.