Le langage HTML met à disposition un certain nombre de balises permettant de pré-formater un texte. Cela va indiquer au navigateur comment afficher un élément, bien que pour certaines balises de pré-formatage, il n’existe pas de règles d’affichages précises. 

## Éléments de formatage HTML

Les balises de pré-formatages sont utilisées afin d’indiquer au navigateur qu’un élément doit s’afficher d’une certaine manière. 

Voici la liste des balises de pré-formatages, mises à disposition par le HTML :

- ```<b></b>``` Permet de mettre du texte en gras (bold, en anglais).
- ```<strong></strong>``` est généralement pour mettre en valeur un texte important. Il n’existe pas de règle d’affichage précise par les navigateurs pour ces éléments; néanmoins ils sont, en général, affichés en gras. 
- ```<i></i>``` permet de mettre du texte en italique.
- ```<em></em>``` définit une partie de texte - généralement un mot - à mettre en valeur. C’est une emphase. L’emphase est généralement utilisée pour insister sur un mot. De manière générale, le navigateur affiche le texte écrit entre ces balises en italique.
- ```<mark></mark>``` Définit un texte à mettre en évidence, un texte à “marquer”.
- ```<small></small>``` Permet de rendre un texte plus petit.
- ```<del></del>``` Défini un texte supprimé. Généralement, le navigateur supprime une ligne du paragraphe se trouvant entre ces balises.
- ```<ins></ins>``` Définit un texte inséré. De manière générale, un texte inséré est souligné par le navigateur, lors de l’affichage.
- ```<sub></sub>``` Définit un indice mathématique. L’indice est placé légèrement sous l’élément qui le précède et dans une police plus petite.
- ```<sup></sup>``` Définit un exposant, comme en mathématiques. Un exposant, par exemple, est le “me” de “Mme” qui est généralement placé un peu au-dessus du “M”, dans une taille de police plus petite.

## Éléments i et em

L’élément ```<i></i>``` permet de mettre un texte en italique, tandis que ```<em></em>``` permet d’insister sur un mot. Ce mot est généralement affiché en italique, pour montrer que l’auteur du texte insiste particulièrement sur ce mot.

Exemple avec ```<i></i>``` :

```html
<i>Le texte est en italique</i>
```

Exemple avec ```<em></em>``` :

```html
<em>Insistance</em>
```

## Élément small

L'élément HTML ```<small></small>``` définit un texte plus petit :

Exemple :

```html
<small>Texte plus petit</small>
```

## Élément mark

L'élément HTML ```<mark></mark>``` définit le texte qui, pour une raison particulière, doit être marqué ou mis en valeur :

Exemple :

```html
<p>Il ne faut pas oublier les <mark>skis</mark></p>
```

## Élément del

L'élément HTML ```<del></del>``` définit un texte comme étant “supprimé”. Cet élément est généralement utilisé pour montrer quelque chose d’incorrect, car les navigateurs affichent le texte en le barrant. 

Exemple :

```html
<p>Il ne faut pas oublier les <del>skis</del> snowboards</p>
```

## Élément ins

L'élément HTML ```<ins></ins>``` définit un texte qui a été inséré dans un document. Bien qu’il n’y ait pas de règles d’affichage clairement définies pour les éléments insérés, les navigateurs soulignent généralement les textes insérés. 

Exemple :

```html
<p>Il ne faut pas oublier les <ins>skis</ins></p>
```

## Élément sub

L'élément HTML ```<sub></sub>``` définit un indice mathématiques. L’indice est généralement placé plus bas que l’élément et dans une taille de police inférieure.

Exemple :

```html
<p>Il faut pas oublier les <sub>skis</sub></p>
```

## Élément sup

L'élément HTML ```<sup></sup>``` définit un exposant mathématiques. Un exposant est généralement placé légèrement au-dessus de l’élément, dans une police plus petite. 

Exemple :

```html
<p>Il faut pas oublier les <sup>skis</sup></p>
```