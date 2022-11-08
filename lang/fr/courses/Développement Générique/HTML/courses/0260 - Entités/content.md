Bien que les entités soient moins utilisées en HTML, surtout lorsque que l’encodage utf-8 est défini dans l’attribut ```charset```, il est des situations où le développeur devra nécessairement les utiliser.

## Les entités HTML

En HTML, une entité est une chaîne de caractères, qui commence avec le signe ```&``` et se termine avec un point-virgule (;).

Les entités se révèlent utiles lorsque le développeur a besoin d’afficher à l’écran un caractère réservé au langage HTML.

Par exemple, si les chevrons (```<>```) doivent être affichés à l’écran, il se peut que le navigateur ne le fasse pas, car ces caractères sont réservés au HTML. C’est typiquement le genre de situation dans laquelle les entités sont utilisées.

## Syntaxe

Deux syntaxes existent pour les entités.

La première ressemble à ceci : ```&nomdelentité;```
La seconde ressemble à ça : ```&#nomdelentité;```

La première syntaxe est la plus utilisée.

__Remarque__ : Ne pas oublier le point virgule à la fin du nom de l’entité, sinon le navigateur ne l'interprète pas.

Ainsi, pour afficher un chevron ouvrant (```<```), l’entité suivante est utilisée : ```&lt;``` ou ```&#60;```

## Espace insécable

Un espace insécable est un espace qui, quoi qu’il arrive au niveau de l’affichage, ne sera pas coupé sur une nouvelle ligne. En d’autres termes, lorsqu’un retour à la ligne se produit à cause des contraintes d’affichage du navigateur, deux mots séparés par un espace insécable iront à la ligne ensemble, il ne seront pas séparés.

C’est l’une des entités les plus utilisées en HTML. Le code pour insérer un espace insécable est le suivant : ```&nbsp;```.

## Tableau d’entités utiles

Ci-dessous, un tableau listant les entités les plus utiles et les plus utilisées en HTML :

| **Résultat** | **Description**      | **Numéro entité** | **Nom entité** |
|----------|----------------------|-------------------|----------------|
| ```  ``` | non-breaking space   | ``` ```           | ```&#160;```   |
| ```<```  | plus petit que       | ```&lt;```        | ```&#60;```    |
| ```>```  | plus grand que       | ```&gt;```        | ```&#62;```    |
| ```&```  | esperluette          | ```&amp;```       | ```&#38;```    |
| ```"```  | guillemet double     | ```&quot;```      | ```&#34;```    |
| ```'```  | guillemet            | ```&apos;```      | ```&#39;```    |
| ```¢```  | cent                 | ```&cent;```      | ```&#162;```   |
| ```£```  | livres               | ```&pound;```     | ```&#163;```   |
| ```¥```  | yen                  | ```&yen;```       | ```&#165;```   |
| ```€```  | euro                 | ```&euro;```      | ```&#8364;```  |
| ```©```  | copyright            | ```&copy;```      | ```&#169;```   |
| ```®```  | registered trademark | ```&reg;```       | ```&#174;```   |

## Combinaison de marques diacritiques

Une marque diacritique est un accent ajouté à une lettre.

Lorsque l’encodage ne comprend pas d’accent et que le développeur doit pourtant en ajouter un sur une des lettres d’un mot, les accents sont rajoutés “à la main” en utilisant les entités correspondantes.

Ci dessous, un tableau listant les principaux accents utilisés :

| **Accent**    | **Caractère** | **Construction** | **Résultat** |
|---------------|---------------|------------------|--------------|
| ```  ̀ . ```  | a             | ```a&#768;```    | ```à```      |
| ```  ́ . ```  | a             | ```a&#769;```    | ```á```      |
| ``` ^ . ```   | a             | ```a&#770;```    | ```â```      |
| ```  ̃ .  ``` | a             | ```a&#771;```    | ```ã```      |
| ```  ̀ . ```  | O             | ```O&#768;```    | ```Ò```      |
| ```  ́ . ```  | O             | ```O&#769;```    | ```Ó```      |
| ``` ^ . ```   | O             | ```O&#770;```    | ```Ô```      |
| ```  ̃ . ```  | O             | ```O&#771;```    | ```Õ```      |