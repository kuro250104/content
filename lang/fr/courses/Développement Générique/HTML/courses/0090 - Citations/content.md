Afin que les développeurs puissent respecter les standards et droits d’auteurs concernant une œuvre, ainsi que le droit à la courte citation, le langage HTML met à disposition plusieurs balises. Il est ainsi possible de citer les sources, le nom de l’auteur, le titre d’une œuvre, etc.

## L'élément ```<blockquote>```

L’élément ```<blockquote></blockquote>``` indique le texte est une citation longue. Dans un ```<blockquote>```, les retours à la ligne sont respectés par le navigateur. 

Le HTML permet également d’utiliser l’attribut cite avec cette balise, afin d’indiquer la source de la citation. Par exemple :

```html
<body>
    <!-- Bloc de citation sans l'attribut cite -->
    <blockquote>
        <p>Bloc de citation</p>
    </blockquote>

    <!-- Bloc de citation avec l'attribut cite -->
    <blockquote cite="https://url.com">
        <p>Bloc de citation</p>
    </blockquote>
</body>
```

## L’élément ```<q>```

L’élément ```<q></q>``` (raccourci de *quote*, “citation” en anglais) indique le texte est une citation. Cet élément est utilisé pour les citations courtes, qui ne nécessitent pas de respecter les retours à la ligne. 

Bien qu’il n’y ait pas de règles d’affichages définies, la plupart des navigateurs modernes affichent les citations placées entre les balises ```<q></q>``` avec des guillemets.

Avec cet élément aussi, l’attribut ```cite``` est utilisable afin de fournir la source de la citation.

Exemple :

```html
<body>
    <!-- Faire une citation en incise dans le paragraphe -->
    <p>Chaque fois que Kenny est tué, Stan dira
        <q cite="http://fr.wikipedia.org/wiki/Kenny_McCormick#Le_dialogue_rituel">
            Oh mon Dieu, ils ont tué Kenny !
        </q>.
    </p>
</body>
```

## L’élément ```<cite>```

```<cite></cite>``` permet d’indiquer le titre d’une œuvre (livre, chanson, sculpture, peinture, etc.) La référence peut être abrégée selon la convention d'utilisation utilisée pour ajouter des métadonnées de référence. Par exemple, pour Arthur Rimbaud, les métadonnées de référence permettent d’écrire A. Rimbaud.

Exemple :

```html
<body>
    <p>Plus d'informations sont disponibles dans <cite>[ISO-0000].</cite></p>
</body>
```

## L’élément ```<abbr>```

L’élément ```<abbr></abbr>``` est utile afin d’indiquer que le texte placé entre les balise est un acronyme ou une abréviation. Cela permet de fournir des informations utiles aux navigateurs, aux systèmes de traduction et aux moteurs de recherche.

Exemple :

```html
<p>La ville de <abbr title="Toulouse">TLS</abbr> est belle.</p>
```

## L’élément ```<address>```

Cet élément est utilisé afin d’indiquer les informations de contact d’un auteur et/ou propriétaire d’un document ou d’un article. Ces informations sont, de manière générale, une adresse email, une adresse URL, une adresse de domicile, un numéro de téléphone, un profil sur les réseaux sociaux, etc. 

Le texte placé entre ```<address>``` et ```</address>``` est généralement affiché en italique, et les navigateurs ajoutent toujours un saut de ligne avant et après l’élément.

Exemple :

```html
<address>
Écrit par John Doe.<br>
Venez sur:<br>
google.com<br>
</address>
```

## L’élément ```<bdo>```

BDO signifie Bi-Directional Override ou l'élément de surcharge bidirectionnelle en français. La balise HTML ```<bdo>``` est utilisée pour remplacer la direction actuelle du texte. Ainsi, la direction d’un texte peut être changée pour aller de la droite vers la gauche, par exemple.

La direction du texte est définie avec l’attribut dir, qui peut recevoir une des valeurs suivantes :

- **ltr** : pour un texte allant de gauche à droite (*left-to-right*, en anglais).
- **rtl** : pour un texte allant de droite à gauche (*right-to-left*, en anglais).
- **auto** : Selon la nature du contenu, le navigateur décide de la direction.

Exemple avec un texte allant de la droite vers la gauche :

```html
<bdo dir="rtl">Le texte est écrit de droite vers la gauche</bdo>
```