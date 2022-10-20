La gestion des événements est ce qui permet au langage JavaScript de pouvoir dynamiser les pages web. 

En informatique, un événement est quelque chose qui se passe au niveau des éléments HTML, tel qu’un clic de l’utilisateur sur un bouton, par exemple.

Associé au langage HTML, le JavaScript permet de “capturer” ces événements et d'adapter le code en fonction.

## Événements HTML

Un événement HTML peut être quelque chose que l’utilisateur ou le navigateur fait. 

Ci-dessous, une liste d’exemples d'événements :

- Une page HTML a fini de charger
- Un champ HTML de type input a changé d’état
- L’utilisateur a cliqué sur un bouton HTML

Le langage JavaScript permet donc de capturer un événement et d’exécuter un code précis lorsque cet événement est déclenché. Pour cela, il est possible d’insérer du code JavaScript directement au sein d’une balise HTML.

Exemple :

```js
<button onclick="console.log('Hello World!')"></button>
```

## Événements souvent utilisés en HTML

Voici la liste des événements les plus souvent utilisés en HTML et JavaScript :

- ```onchange``` : L’élément HTML a changé
- ```onclick``` : L’utilisateur a cliqué sur un élément HTML
- ```onmouseover``` : L’utilisateur a passé sa souris au-dessus d’un élément HTML
- ```onmouseout``` : L’utilisateur a enlevé la souris ou le curseur d’un élément HTML
- ```onkeydown``` : L’utilisateur a enfoncé une touche du clavier
- ```onload``` : Le navigateur a fini de charger la page

__Remarque__ : Les événements sont traités plus en détails dans les cours sur le DOM en JavaScript.