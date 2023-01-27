## Durée approximative

1 jour

## Prérequis

- <a href="https://microlead.fr/echelles/javascript" title="Prérequis en JavaScript" target="_blank">JavaScript niveau 5</a>

## Énoncé

### Description courte

Recréer le jeu du Morpion sur une page web avec JavaScript.

### Listing de fonctionnalités

Au clic sur l’une des 9 cases de la grille, l’application doit afficher la marque d’un joueur tour à tour. Lorsque 3 cases verticales, horizontales ou diagonales sont marquées par le même joueur, il gagne et le jeu lui fait savoir.

### Éléments donnés

Code de la page HTML :

```html
<!DOCTYPE html>
<html>
<head>
    <title>Morpion</title>
</head>
<body>
    <h1>Morpion</h1>
    <section id="jeu">
        <div class="row-1">
            <div class="col-1" style="width: 100px; height: 100px; display: inline-block; border: 1px solid black;"></div>
            <div class="col-2" style="width: 100px; height: 100px; display: inline-block; border: 1px solid black;"></div>
            <div class="col-3" style="width: 100px; height: 100px; display: inline-block; border: 1px solid black;"></div>
        </div>
        <div class="row-2">
            <div class="col-1" style="width: 100px; height: 100px; display: inline-block; border: 1px solid black;"></div>
            <div class="col-2" style="width: 100px; height: 100px; display: inline-block; border: 1px solid black;"></div>
            <div class="col-3" style="width: 100px; height: 100px; display: inline-block; border: 1px solid black;"></div>
        </div>
        <div class="row-3">
            <div class="col-1" style="width: 100px; height: 100px; display: inline-block; border: 1px solid black;"></div>
            <div class="col-2" style="width: 100px; height: 100px; display: inline-block; border: 1px solid black;"></div>
            <div class="col-3" style="width: 100px; height: 100px; display: inline-block; border: 1px solid black;"></div>
        </div>
    </section>
    <section>
        <div id="resultat">

        </div>
    </section>
</body>
</html>
```

### Contraintes

- Ne pas modifier l’HTML fourni SAUF : 
    - les noms de classes si besoin
    - l'ajout de CSS si besoin
    - La balise de script permettant d'ajouter du javascipt
    - les data-attributes si vous les connaissez
    - La div #resultat qui permet d'afficher le résultat
- Le joueur ne doit pas pouvoir marquer une case déjà marquée.

### Critères de réussite

Le jeu fonctionne. Il est possible de gagner. Le jeu indique correctement la victoire et quel joueur a gagné.

### Astuces

#### Astuce 1

Pour réceptionner l'événement de clic sur une case, il sera nécessaire d’utiliser un « eventListener ».

#### Astuce 2

Pour marquer une case par un joueur ou l’autre, vous pouvez changer la couleur de background d’une case.
