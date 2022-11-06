Les formulaires sont devenus omniprésents sur les sites web, que ce soit pour l’inscription à une newsletter, un formulaire de contact, un formulaire d’inscription, un livre d’or, etc. Ils permettent de renforcer les interactions avec les utilisateurs. 

## L'élément form

L’élément ```<form></form>``` est utilisé pour indiquer au navigateur que tout ce qui se trouve entre ces balises est en rapport avec le formulaire. La balise ouvrante délimite donc le début d’un formulaire, et l’ensemble du contenu jusqu’à la balise fermante sera réputé concerner le formulaire.

L'élément ```<form>``` est un conteneur pour différents types d'éléments, tels que: les champs de texte, cases à cocher, boutons radio, boutons d'envoi, etc.

Exemple :

```html
<form>
    Éléments du formulaire
</form>
```

## L'élément ```<input>```

L’élément ```<input></input>``` (littéralement *saisie*, en anglais), est utilisé afin de permettre à l’utilisateur de saisir des données. Cet élément est obligatoirement accompagné de l’attribut type. En fonction de la valeur passée à celui-ci, l’élément ```<input>``` s’affichera de plusieurs manières différentes. 

Voici un tableau dressant la liste des valeurs qui peuvent être reçues par l’attribut ```type``` :

| **Type** | **Description** |
| --- | --- |
| ```<input type="text">``` | Affiche un champ de saisie de texte sur une seule ligne |
| ```<input type="radio">``` | Affiche un bouton radio (pour sélectionner l'un des nombreux choix) |
| ```<input type="checkbox">``` | Affiche une case à cocher (pour sélectionner zéro ou plus de nombreux choix) |
| ```<input type="submit">``` | Affiche un bouton d'envoi (pour soumettre le formulaire) |
| ```<input type="button">``` | Affiche un bouton cliquable |

## Champs de texte

L’élément ```<input type="text">``` affiche un champ de texte monoligne, permettant à l’utilisateur de saisir des données de type “texte”.

Exemple :

```html
<form>
    <input type="text" id="metier" name="metier">
</form>
```

L’exemple ci-dessus affiche un champ de texte portant le nom “métier”.

## L'élément ```<label>```

```<label></label>``` (*étiquette*, en anglais), permet de définir une “légende” pour chaque élément d’un formulaire. 

Cet élément est généralement accompagné de l’attribut ```for```, bien que ce ne soit pas obligatoire. Cet attribut reçoit en valeur un mot permettant de faire le lien avec l’identifiant (**id**) du champ du formulaire auquel il est rattaché.

Cet élément est particulièrement utile lorsqu’un formulaire contient de case à cocher ou des boutons “radio”, car cela permet à l’utilisateur de cliquer sur le texte contenu entre les balises ```<label></label>``` et de cocher automatiquement la case correspondante. Pour ce faire, la valeur définie dans le **for** doit être la même que la valeur donnée au **id** du champ en question.

Exemple :

```html
<form>
    <label for=nom>Nom :</label><br />
    <input type="text" name="nom" id="nom" />
</form>
```

## Boutons radio

Les boutons radio permettent à l’utilisateur de ne choisir qu’une seule option parmi une liste proposée.

Pour créer un bouton radio, il suffit de passer la valeur **radio** à l’attribut ```type```, dans le ```<input>```.

Exemple :

```html
<form>
    <input type="radio" id="dev" name="metier" value="dev">
    <label for="male">Développeur</label><br>
    <input type="radio" id="res" name="metier" value="res">
    <label for="female">Réseaux</label><br>
</form>
```

## Cases à cocher

Les cases à cocher (*checkbox*, en anglais) permettent à l’utilisateur de sélectionner plusieurs options dans une liste.

Pour créer une case à cocher, l’attribut ```type``` doit recevoir la valeur **checkbox**.

Exemple :

```html
<form>
    <input type="checkbox" id="dev" name="metier" value="dev">
    <label for="male">Développeur</label><br>
    <input type="checkbox" id="res" name="metier" value="res">
    <label for="female">Réseaux</label><br>
</form>
```

## Le bouton Envoyer

Lorsque l’utilisateur clique sur ce bouton, il est redirigé vers une page contenant un script qui va contrôler et traiter les données saisies par le formulaire. 

Pour créer un bouton “envoyer”, il doit disposer d’un attribut ```type``` et doit recevoir la valeur **submit**.

Exemple :

```html
<form>
    <input type="checkbox" id="dev" name="metier" value="dev">
    <label for="male">Développeur</label><br>
    <input type="checkbox" id="res" name="metier" value="res">
    <label for="female">Réseaux</label><br>
    <input type="submit" value="Envoyer">
</form>
```

## Attribut name

Pour que la donnée saisie dans un champ du formulaire puisse être traitée lorsque l’utilisateur clique sur le bouton envoyer, chaque ```<input>``` doit être accompagné de l’attribut ```name```. Cet attribut reçoit en valeur un mot représentant le nom du champ.

Lors du traitement du formulaire, chaque valeur saisie sera identifiée et récupérable grâce à cet attribut. Il est donc primordial de le définir pour chaque champ. Attention à ne pas définir plusieurs fois la même valeur (sauf pour les choix multiples), sans quoi c’est la dernière valeur qui sera transmise, et les autres ne seront pas récupérables.

Exemple :

```html
<form>
    <input type="checkbox" id="dev" name="metier" value="dev">
    <label for="male">Développeur</label><br>
    <input type="checkbox" id="res" name="metier" value="res">
    <label for="female">Réseaux</label><br>
    <input type="submit" value="Envoyer">
</form>
```