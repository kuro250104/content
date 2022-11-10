Dans ce cours, nous allons définir ce qu'est jQuery et comprendre la valeur de l'utilisation de cette bibliothèque JavaScript dans un projet Web.

## Définition de JQuery

jQuery est ce que nous appelons une «librairie» ou «bibliothèque» JavaScript. La fonction de la bibliothèque en informatique est de simplifier l'utilisation d'un certain langage de programmation en fournissant un ensemble de fonctionnalités prêtes à l'emploi.

La bibliothèque jQuery se compose d'un ensemble de blocs de code JavaScripts préconçus, qui sont généralement contenus dans des méthodes. Ainsi il est bien plus simple et rapide en tant que développeur d’utiliser les méthodes de jQuery plutôt que d’utiliser du Javascript natif. Voici un exemple comparatif avec la méthode “hide()” de jQuery qui permet de masquer des éléments sur la page.

```js
$(document).ready(function(){
    $('#texte').hide();
});
```

Et voici l’équivalent en javascript natif :

```js
document.addEventListener("DOMContentLoaded", function (event) {
    let paraph = document.getElementById('paraph');
    paraph.style.display = 'none';
});
```

## Pourquoi l’utiliser ?

JQuery étant une librairie javascript, il nous propose deux principaux avantages à son utilisation. En premier lieu, il nous permet un gain de temps certain dans l’écriture de code informatique fonctionnel. Comme présenté dans l’exemple ci-dessus, le nombre de lignes et de caractères à écrire sur un code simpliste en comparaison à du javascript natif est déjà conséquent. Plus vos scripts seront longs et importants, plus cet écart sera conséquent et donc avantageux pour le développeur. En second plan, et comme toute librairie, son utilisation nous assure de la fonctionnalité du code utilisé.

L’utilisation de cette librairie nous permet également de nous assurer d’une compatibilité complète et entière entre les navigateurs ainsi que de l’interchangeabilité du code.

Attention, il faut bien comprendre que jQuery ne consiste pas en un remplacement de JavaScript, mais bien comme un complément à ce dernier. Aussi, si l’utilisation de jQuery nous permet de faciliter et d’accélérer le développement JavaScript, il ne nous interdit pas de nous servir de JavaScript en parallèle, ni ne nous en dispense. Il est donc courant d’utiliser le JavaScript ET la librairie jQuery ensemble.