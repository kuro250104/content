Pour des raisons de clarté, il est parfois nécessaire d’organiser des données au sein d’un tableau. Le langage HTML permet de faire cela.

## Créer un tableau simple

En HTML, un tableau est créé ligne par ligne.

Pour commencer, le navigateur doit savoir qu’il s’apprête à afficher un tableau. Pour ce faire, les balises ```<table></table>``` sont utilisées afin de déclarer le tableau.

Ensuite, chaque ligne du tableau est créée avec les balises ```<tr></tr>```.

Enfin, les colonnes sont créées avec les balises ```<td></td>```, entourant le nom de chaque colonne.

Exemple :

``` html
<body>
    <!-- Tableau -->
    <table>
        <!-- Première ligne -->
        <tr>
            <!-- Première colonne -->
            <td>Nom</td>
            <!-- Deuxième colonne -->
            <td>Prenom</td>
            <!-- Troisième colonne -->
            <td>Age</td>
            <!-- Quatrième colonne -->
            <td>Mail</td>
        </tr>
        <!-- Deuxième ligne -->
        <tr>
            <!-- Première colonne -->
            <td>John</td>
            <!-- Deuxième colonne -->
            <td>Doe</td>
            <!-- Troisième colonne -->
            <td>32</td>
            <!-- Quatrième colonne -->
            <td>johndoe@gmail.com</td>
        </tr>
        <!-- Troisième ligne -->
        <tr>
            <!-- Première colonne -->
            <td>John</td>
            <!-- Deuxième colonne -->
            <td>Doe</td>
            <!-- Troisième colonne -->
            <td>32</td>
            <!-- Quatrième colonne -->
            <td>johndoe@gmail.com</td>
        </tr>
    </table>
</body>
```

## Fusionner des cellules sur plusieurs colonnes

Pour fusionner ensemble plusieurs cellules sur plusieurs colonnes, l’attribut ```colspan``` est utilisé et reçoit en valeur le nombre de colonnes sur laquelle la cellule doit s’étendre.

Exemple :

``` html
<table>
    <tr>
        <th>Nom</th>
        <!-- Utilise deux colonnes -->
        <th colspan="2">Téléphone</th>
    </tr>
    <tr>
        <td>John Doe</td>
        <td>0102030405</td>
        <td>0203040506</td>
    </tr>
</table>
```

## Fusionner des cellules sur plusieurs lignes

Pour fusionner des cellules sur plusieurs lignes, l’attribut ```rowspan``` est utilisé. Il reçoit en valeur le nombre de lignes sur lesquelles les cellules sont fusionnées. 

Exemple :

``` html
<table>
    <tr>
        <th>Nom:</th>
        <td>John Doe</td>
    </tr>
    <tr>
        <!-- Utilise plus d'une ligne -->
        <th rowspan="2">Telephone:</th>
        <td>0102030405</td>
    </tr>
    <tr>
        <td>0203040506</td>
    </tr>
</table>
```

## Ajouter une légende

Le langage HTML permet d’ajouter une légende à un tableau grâce à l’élément ```<caption></caption>```.

Exemple :

``` html
<table>
    <!-- Rajoute une légende -->
    <caption>Utilisateur</caption>
    <tr>
        <th>Nom</th>
        <th colspan="2">Téléphone</th>
    </tr>
    <tr>
        <td>John Doe</td>
        <td>0102030405</td>
        <td>0203040506</td>
    </tr>
</table>
```