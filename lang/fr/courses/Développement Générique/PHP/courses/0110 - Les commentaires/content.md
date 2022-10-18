Les commentaires sont en programmation un moyen de laisser des explications ou des informations dans votre code. La particularité du commentaire est qu’il n’est pas utilisé de la même manière que le reste de votre code étant donné que la machine ne l’interprète pas. La cible d’un commentaire est donc le développeur ou le lecteur d’un code.

Les commentaires sont souvent sujets à débats, surtout durant les premiers pas en développement, et il n’est pas rare d’entendre différentes phrases sur le sujet : 

- “Quel est l’intérêt ? C’est mon code, je le connais !”
- “Trop de lignes à écrire, mon code est moins lisible”
- “Pourquoi écrire des choses inutiles pour l’ordinateur ?”

En réalité, il existe autant d’interrogations qu’il existe de mauvaises explications… Les commentaires doivent faire partie intégrante du code. L’idée ici n’est pas de commenter la moindre ligne écrite, mais bien de rajouter des notes, explications ou informations sur telle ou telle partie de code. Le fait qu’ils semblent parfois inutiles est souvent lié au fait qu’il est rédigé par le créateur même du code, et donc que celui-ci sait ce qu’il contient et ce qu’il fait. Cependant, si une autre personne est amenée à modifier ce code, alors peut-être que celle-ci ne comprendra pas correctement ce que fait le code, ni même la logique appliquée. Par ailleurs, travailler sur un code complexe et devoir le modifier 6 mois plus tard entraîne généralement des problèmes, même au développeur ayant rédigé le code initial. Il n’est en effet pas rare dans ces conditions que les détails du code initial aient été oubliés, ce qui entraîne indéniablement une complexification des modifications à apporter.

Il faut ainsi garder en tête qu’un code professionnel est généralement apparenté à un code bien commenté. C’est d’ailleurs pourquoi certaines “normes” de codages incluent obligatoirement l’utilisation de commentaires, et PHP ne fait pas exception à cette règle…

De manière générale, le code écrit doit être rédigé en anglais, les commentaires également. C’est une convention internationale et la majorité des entreprises suivent ce chemin. Ainsi est recommandé de prendre rapidement l’habitude d’écrire l’ensemble de vos commentaires en anglais, afin de gagner en rapidité de travail par la suite.

Les commentaires peuvent par ailleurs servir à générer automatiquement des documentations de code. Ce n’est pas le moindre des arguments pour vous encourager à les utiliser, mais cela implique néanmoins de se conformer à une certaine nomenclature dans leur écriture. Il existe plusieurs outils permettant de générer des documentations à partir de commentaires, l’un des plus utilisés en PHP est “PHP Documentor”.

## Insérer des commentaires en PHP

Il existe deux moyens d’écrire des commentaires dans du code PHP. L’un permet de n’en écrire que sur une seule ligne, alors que l’autre vous permet d’en écrire sur plusieurs lignes.

### Sur une seule ligne

Deux symboles permettent de déclarer un commentaire sur une ligne : le “dièse” aussi appelé “hashtag” (**#**), ou bien le “double slash” (**//**).

À partir du moment où l’un de ces symboles est utilisé, alors la suite de la ligne est considérée comme étant un commentaire. Par exemple :

``` php
// Ceci est un commentaire sur une ligne complète
mais ici ce n'est plus un commentaire
echo('coucou'); // et ici encore un commentaire qui ne sera pas interprété

# Ceci est également un commentaire sur une ligne
echo('au revoir'); # et un dernier commentaire non interprété.
```

Quelques explications détaillées sur l'exemple ci-dessus : 

- **ligne 1** : La ligne est un commentaire, car débute par “ **//** “.
- **ligne 2** : La ligne ne commence ni par “ **//** “ ni par “ **#** “. PHP ne prendra donc pas cette ligne pour un commentaire et créera une erreur, parce qu'il va essayer d’interpréter la phrase comme du code.
- **ligne 3** : le commentaire commence à partir du symbole “ **//** “. Tout ce qui est placé avant va ainsi être interprété : la page affichera ici “coucou” à l’écran.
- **ligne 4** : La ligne est un commentaire, car débute par “ **#** “.
- **ligne 5** : Le commentaire commence par le symbole “ **#** “. Tout ce qui est placé avant va ainsi être interprété : la page affichera ici “au revoir”.

### Sur plusieurs lignes

Les commentaires écrivent sur plusieurs lignes commencent par les symboles “ /* “ (slash étoile), et se terminent par le symbole “ */ “ (étoile slash). Voici un exemple de commentaire sur plusieurs lignes : 

``` php
/*
Ceci est 
un commentaire
sur plusieurs
lignes
*/
```

Dans l’ensemble du code présenté ci-dessus, aucune ligne ne sera interprétée par PHP étant donné que tout est placé entre les symboles de début et de fin de commentaire multiligne.

#### Astuce

Il peut, certaines fois, arriver de vouloir supprimer une partie d’un code. Une astuce consiste à commenter ce code grâce aux commentaires plutôt que de l’effacer. Vous pourrez de la sorte aisément revenir en arrière si besoin. Attention tout de même à ne pas laisser de code commenté une fois finalisé : il est important de garder un code propre et professionnel, et donc de supprimer tout code inutile et non fonctionnel régulièrement.