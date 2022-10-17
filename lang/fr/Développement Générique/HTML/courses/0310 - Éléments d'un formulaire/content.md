Dans le cours concernant les bases de la création d’un formulaire, l’élément input a été évoqué en détail. Cependant, il existe bien d’autres éléments pouvant composer un formulaire.

## L'élément <select>

L’élément ```<select></select>``` permet de créer une liste déroulante. En général, cet élément est utilisé lorsqu’un grand choix d’options est possible. 

Chaque item de la liste doit être entouré de l’élément ```<option></option>```. Cet élément est accompagné de l’attribut ```value```, qui reçoit en valeur le nom de l’item.

__Remarque__ : Par défaut, c’est toujours le premier item qui est pré-sélectionné.

Exemple :

``` html
<form>
    <label for="metier">Métier :</label>
    <!-- Liste déroulante -->
    <select id="metier" name="metier">
        <!-- items de la liste -->
        <option value="dev">Développeur</option>
        <option value="res">Réseaux</option>
    </select>
</form>
```

Pour changer l’item présélectionné, il est possible d’utiliser l’attribut ```selected``` à la fin de l’élément ```<option>``` choisi.

Exemple :

``` html
<option value="dev" selected>Développeur</option>
```

Lorsque l’attribut ```multiple``` est ajouté à la fin de l’élément ```<select>```, cela permet à l’utilisateur de sélectionner plusieurs options.

Exemple :

``` html
<label for="metier">Métier :</label>
<!-- Liste déroulante avec la possibilité de choisir plusieurs options -->
<select id="metier" name="metier"  multiple>
    <option value="dev" selected>Développeur</option>
    <option value="res">Réseaux</option>
</select>
```

## L'élément <textarea>

L’élément ```<textarea></textarea>``` défini une zone de texte multilignes. Cet élément est généralement utilisé afin que l’utilisateur puisse laisser un message ou un commentaire sous un article, par exemple.

Cet élément est généralement accompagné de l’attribut ```rows```, qui définit le nombre de lignes visibles dans la zone de texte, et de l’attribut ```cols```, qui définit la largeur de la ligne.

Exemple :

``` html
<!-- Zone de texte -->
<textarea name="message" rows="10" cols="30">
    Zone de texte
</textarea>
```

## L'élément <button>

L'élément ```<button></button>``` définit un bouton cliquable :

Exemple :

``` html
<!-- bouton affichant “Cliquer !” -->
<button type="button">Cliquer !</button>
```

## Les éléments <fieldset> et <legend>

L’élément ```<fieldset></fieldset>``` permet d’organiser un formulaire en regroupant ensemble les champs qui ont un rapport entre eux. Par exemple, les champs concernant l’identité de l’utilisateur (nom, prénom, date de naissance, etc…), les champs concernant son adresse postale (rue, numéro, code postale, ville, pays, etc…) ou encore ses informations de contact (adresse mail, téléphone, etc...).

L’élément ```<legend></legend>```, quant à lui, permet de définir un nom pour le ```<fieldset>```.

De manière générale, les navigateurs entourent les ```<fieldset>``` d’une bordure, et placent la ```<legend>``` en haut du cadre. 

``` html
<form>
    <!-- Regroupe les champs ayant un rapport entre eux -->
    <fieldset>
        <!-- Définit un nom pour le fieldset -->
        <legend>Identité</legend>
        <label for="nom">Nom :</label>
        <input type="text" id="nom" name="nom" />
	   <label for="nom">Prénom :</label>
        <input type="text" id="prenom" name="prenom" />
        <input type="submit" value="Envoyer">
    </fieldset>
</form>
```

## L'élément <datalist>

L’élément ```<datalist></datalist>``` est particulier en ceci qu’il représente à la fois un champ de texte et un liste déroulante. Cependant, le principe est simple. Lorsque l’utilisateur va placer le curseur dans le champ texte (créé par ```<datalist>```), une liste d’options prédéfinies va s’afficher juste en dessous. 

Pour créer une ```<datalist>```, il faut d’abord créer un élément ```<input>```. Cet élément est accompagné du seul attribut ```list```, qui reçoit en valeur l’identifiant qui est donné à l’élément ```<datalist>```.

Ensuite, il faut accompagner l’élément ```<datalist>``` de l’attribut ```id```, qui reçoit en valeur le nom spécifié dans l’attribut list de l’```<input>```.

Enfin, il faut créer l’élément ```<option>```, accompagné de l’attribut ```value```. Cet attribut reçoit en valeur l’option à afficher.

Exemple :

``` html
<form>
    <!-- Permet de faire une liste déroulante avec une liste prédéfinie d'options -->
    <input list="metier">
    <datalist id="metier">
        <option value="Développeur">
        <option value="Administrateur">
    </datalist>
</form>
```