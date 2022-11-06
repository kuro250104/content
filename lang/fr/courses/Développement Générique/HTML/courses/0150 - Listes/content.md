Le langage HTML permet de créer des listes à puce (appelées listes non ordonnées) et des listes numérotées (appelées listes ordonnées).

## Les listes non ordonnées

Les listes non ordonnées sont utilisées pour répertorier des éléments qui n’ont pas besoin d’être ordonnés, qui n’ont pas de rapport particulier entre eux ou qui ne souffrent pas de hiérarchie. 

Une liste non ordonnée est définie grâce aux balises ```<ul></ul>``` (pour *unordered list*, liste non ordonnée, en anglais). Ensuite, chaque item de la liste est entouré des balises ```<li></li>``` (pour *list item*, item de liste, en anglais).

Exemple :

```html
<body>
    <!-- Liste non ordonnée -->
    <ul>
        <!-- Element -->
        <li>Ski</li>
        <!-- Element -->
        <li>Pomme</li>
        <!-- Element -->
        <li>Stylo</li>
    </ul>
</body>
```

## Les listes ordonnées

Les listes ordonnées sont utilisées pour des items liés entre eux ou qui souffrent d’une hiérarchie. Les items d’une liste ordonnée sont affichés avec des numéros devant, représentant leur importance dans la hiérarchie.

Une liste ordonnée est entourée des éléments ```<ol></ol>``` (pour *ordered list*, liste ordonnée, en anglais). Ici aussi, chaque item de la liste est entouré des balises ```<li></li>```.

Exemple :

```html
<body>
    <!-- Liste ordonnée -->
    <ol>
        <!-- Element -->
        <li>Introduction</li>
        <!-- Element -->
        <li>Partie I</li>
        <!-- Element -->
        <li>Partie II</li>
        <!-- Element -->
        <li>Partie III</li>
    </ol>
</body>
```

## Listes de description

Le HTML permet également de dresser une liste de descriptions. Ce genre de liste est généralement utilisé pour des définitions ou pour décrire des articles.

Une liste de descriptions est entourée des balises ```<dl></dl>```. Ensuite, chaque item de la liste est entouré des éléments ```<dt></dt>```. La description ou la définition, quant à elle, est entourée des balises ```<dd></dd>```.

Exemple :

```html
<!-- Liste de description -->
<dl>
    <!-- Premier terme -->
    <dt>Ski</dt>
    <!-- Description du terme ski -->
    <dd>- freerando pas de fond</dd>
    <!-- Deuxième terme -->
    <dt>Lunettes</dt>
    <!-- Description du terme lunettes -->
    <dd>- Des lunettes pas un masque</dd>
</dl>
```