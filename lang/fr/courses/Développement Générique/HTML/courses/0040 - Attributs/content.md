Ce cours traite des attributs et de leur utilité au sein des balises HTML.

## Les attributs

Les attributs sont des valeurs supplémentaires au sein d’une balise HTML, permettant d’apporter des précisions, de modifier leur comportement, etc. Ils sont placés dans les balises ouvrantes et n’ont pas d’ordre particulier. 

Il arrive que certains attributs ne soient pas obligatoires mais fortement conseillés, pour améliorer le référencement, par exemple ; tandis que pour d’autres éléments HTML, l’utilisation de certains attributs spécifiques est obligatoire.
Le rôle des attributs est de compléter un élément, en lui fournissant, par exemple, une identité, ou encore en y ajoutant des informations sur la manière dont l’élément doit s’afficher. 

Un attribut ne contient qu’une seule valeur. Un mot, en général. Si plusieurs mots doivent être écrits au sein de l’attribut, il est possible d’ajouter un tiret entre chacun de ces mots, pour n’en former plus qu’un. 

La syntaxe d’un attribut est simple :

``` html
<element attribut="valeur-de-l-attribut">Contenu</element>
```

Dans le cours précédent, des attributs ont déjà été utilisés avec des balises. Par exemple, pour ajouter une image au sein d’une page web, il faut utiliser le code HTML suivant :

``` html
<img src="logo.png" alt="logo" />
```

Dans cette balise, l’élément ```<img />``` est d’abord complété par l’attribut ```src``` (pour source), permettant de préciser quelle image insérer et où elle se trouve, et également par l’attribut ```alt```, permettant d’afficher un texte alternatif en cas de problème d’affichage de l’image, ou qui peut permettre aux personnes malvoyantes visitant le site de savoir que l’image est en réalité un logo (certains équipements spéciaux permettent la lecture “à voix haute” du contenu de l’attribut ```alt```).

**Remarque** : Les guillemets autour des valeurs données aux attributs ne sont pas obligatoires. Cependant, le W3C, l’organisme chargé de standardiser l’utilisation du langage HTML, recommande de les utiliser. Bien que les guillemets doubles soient les plus utilisés, des guillemets simples peuvent également entourer les valeurs des attributs. Par souci de cohérence et d’habitude, nous vous recommandons d’utiliser systématiquement les guillemets doubles.

Exemple :

``` html
<p style='color:blue'>Je suis un paragraphe</p>
```

## Les attributs de largeur et de hauteur

Les attributs de largeur et de hauteur, *width* et *height* en anglais, permettent de préciser la taille de l’image, mais pas de modifier ces valeurs. En fait, lorsque ces attributs sont renseignés, le navigateur réserve une place avec la largeur et la hauteur spécifiée sur la page pour pouvoir afficher l’image. Cela permet d’éviter un changement de mise en page lors du chargement de la page.

Exemple :

``` html
<img src="logo.jpg" alt="logo" width="300px" height="200px">
```

Dans l’exemple ci-dessus, l’image a une largeur définie à 300 pixels et une hauteur définie à 200 pixels.

## L'attribut de style

Pour changer la couleur de la police d’écriture, par exemple, ou encore pour changer sa taille, ou changer la couleur d’arrière-plan d’un élément, etc., le langage HTML met à disposition l’attribut ```style```. Celui-ci permet d’intégrer du code CSS directement au sein du HTML. Aussi si cette pratique n’est pas conseillée, certains cas de figure entraînent l’obligation de l’utiliser.

Exemple : 

``` html
<p style="color:blue">Je suis un paragraphe</p>
```

Dans cet exemple, la couleur de la police de ce paragraphe est définie à bleu.

## L'attribut lang

Dans les cours précédents, cet attribut à déjà été évoqué. Il s’ajoute à l’intérieur de la balise HTML et permet de préciser la langue de la page HTML, ceci pour aider les moteurs de recherche dans le référencement du site web.

Pour une page HTML en français, l’attribut ```lang``` reçoit la valeur ```fr``` (en minuscule).

Exemple :

``` html
<!DOCTYPE html>
<html lang="fr">
...
</html>
```

Afin d’encore plus améliorer le référencement d’un site web, il est également possible d’ajouter un “code pays” comme valeur à l’attribut lang. Ainsi, pour un site internet créé en france, l’attribut lang ressemble à ceci :

``` html
<!DOCTYPE html>
<html lang="fr-FR">
...
</html>
```

**Remarque** : La langue est écrite en minuscules, tandis que le code pays est écrit en majuscules.

## L’attribut de titre

Le langage HTML permet d’ajouter une info-bulle à afficher lorsque la souris reste un certain temps pointé sur un élément (état de *survol*). Pour ce faire, il faut utiliser l’attribut ```title``` et lui donner en valeur le texte à afficher dans l’info-bulle. Cet attribut est quasiment systématiquement utilisé pour les balises de liens, et même si non obligatoire, tout de même considéré comme tel.

Exemple :

``` html
<a href="index.html" title="Revenir à la page d'accueil">Accueil</a>
```

Dans cet exemple, lorsque la souris reste un certain temps pointée sur le lien, une info-bulle s’affiche, contenant le texte “Revenir à la page d’accueil”.