Comme tout langage qui se respecte, le langage HTML donne au développeur la possibilité d’écrire des commentaires pour son code.

## Définition et utilité des commentaires en HTML

Les commentaires sont des lignes de texte qui ne sont **pas interprétées** par le navigateur (cela signifie que le navigateur n’affiche pas le commentaires). Ils sont utilisés afin d’expliquer certaines parties de code qui peuvent s’avérer compliqués à comprendre autrement. C’est également utile lorsque le développeur sait qu’il laissera son code de côté pendant un moment. S’il a commenté certains bouts de code, il lui sera ainsi plus facile de comprendre ce qu’il a voulu faire lorsqu’il se replongera dans son code.

Les commentaires peuvent être très utiles dans trois situations principales :

- Pour les projets de grande envergure, afin de comprendre pourquoi une partie d’un code a été écrit et/ou pour expliquer ce qu’elle fait.
- Si plusieurs développeurs travaillent sur un même projet, les commentaires s’avèrent utiles pour comprendre ce que chacun fait. Cela rend également possible la “distribution” du code. Si un autre développeur reprend le projet, il lui est ainsi plus facile de comprendre le code écrit par son prédécesseur
- Il arrive qu’un développeur ait besoin de faire des tests pour comprendre, par exemple, pourquoi un élément ne s’affiche pas correctement. Les commentaires sont alors utilisés afin “d'isoler un” morceau de code et de le rendre ainsi “invisible” pour le navigateur. 

## Écrire des commentaires en HTML

Les commentaires, en HTML comme dans de nombreux autres langages, peuvent être écrits sur une seule ligne ou s’étendre sur plusieurs lignes. Cependant, contrairement à de nombreux autres langages informatiques, en HTML la syntaxe des commentaires est strictement la même que ces commentaires soient écrits sur une seule ligne ou qu’ils s’étendent sur plusieurs lignes.

En HTML, la syntaxe des commentaires est la suivante :

``` html
<!-- Ceci est un commentaire en HTML --> 
```

__Remarque__ : Il est important que la balise fermante du commentaire ne prenne pas de point d’exclamation, contrairement à la balise ouvrante.

Exemple :

``` html
<body>
    <!-- Deux titres -->
    <h1>Titre principal</h1>
    <h2>Titre important</h2>

    <!-- Des paragraphes
    Écrit sur plusieurs lignes -->
    <p>Je suis le premier paragraphe</p>
    <p>Et mois le second</p>
</body>
```

__Remarque__ : En langage HTML, les commentaires sont visibles par tout un chacun. Pour ce faire, il suffit simplement de faire un clic droit sur la page web et de cliquer sur “Afficher le code source de la page”. **Ainsi est-il vital de ne pas mettre d’informations sensibles dans les commentaires**. 