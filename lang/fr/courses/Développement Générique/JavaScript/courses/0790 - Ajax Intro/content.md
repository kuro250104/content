AJAX est l’acronyme de Asynchronous JavaScript and XML - JavaScript et XML asynchrone, en français. 

L’AJAX est en fait le rêve de tout développeur, car il permet de lire des données depuis un serveur, une fois que la page est chargée, mettre à jour une page web sans besoin de la recharger, ou encore envoyer des données à un serveur en arrière-plan.

## Qu’est-ce que l’AJAX ?

L’AJAX n’est pas un langage de programmation. Il s’agit plutôt d’une combinaison de l’objet XMLHttpRequest - permettant de récupérer des données sur un serveur - et de JavaScript utilisant le DOM HTML, pour pouvoir afficher les données à l’écran.

__Remarque__ : AJAX est un nom trompeur. En effet, bien qu’il permette de récupérer des données au format XML, il peut également les récupérer au format texte normal ou bien au format JSON.

En d’autres termes, AJAX permet de mettre à jour des pages web de manière asynchrone. Tout se passe en arrière-plan. Cela signifie qu’il est possible de mettre à jour certaines parties d’une page web sans avoir besoin de la recharger entièrement.

## Comment fonctionne l’AJAX

![Schématisation du fonctionnement de l'AJAX](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/JavaScript/courses/0790%20-%20Ajax%20Intro/images/image1.jpg)

## Navigateurs internet modernes

Les navigateurs modernes peuvent utiliser ```fetch API``` plutôt que la requête ```XMLHttpRequest``` classique.

Cette API donne la possibilité aux navigateurs d’effectuer des requêtes HTTP sur les serveurs web.

En résumé, ```fetch API``` fait strictement la même chose que l’objet ```XMLHttpRequest```, mais d’une manière beaucoup plus simple.