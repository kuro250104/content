Les titres, en HTML, sont définis sur 6 niveaux. Cette notion est abordée dans ce cours.

## Définition de titres en HTML

Les titres (*headings*, en anglais), sont définis avec la double balise ```<hn></hn>```. Il existe 6 niveaux de titres, en HTML - le niveau 1 étant le plus important et le niveau 6 le moins important - et ces niveaux permettent d’organiser et de hiérarchiser les contenus.

```html
<body>
    <!--Un titre très important-->
    <h1>Titre principal</h1>

    <!--Un titre important-->
    <h2>Titre important</h2>

    <!--Un autre titre important-->
    <h2>Titre important</h2>

    <!--Un titre un peu moins important-->
    <h3>Titre d'importance moyenne</h3>

    <!--Etc, etc.-->
    <h4>Un titre pas très important</h4>
    <h5>Un titre peu important</h5>
    <h6>Un titre vraiment peu important</h6>
</body>
```

**Remarque** : bien que conventionnellement seuls 6 niveaux de titres sont utilisés, le HTML ne présente aucune limite quant au nombre de niveaux de titre. Ainsi il est possible d’aller plus loin que ```<h6>```, et d’utiliser par exemple ```<h7>```, ```<h8>```, ```<h9>```, etc…