## Durée approximative

1 heure

## Prérequis

- <a href="https://microlead.fr/echelles/javascript" title="Prérequis en JavaScript" target="_blank">JavaScript niveau 4</a>

## Énoncé

### Description courte

Créer une application web de calculatrice en JavaScript.

### Listing de fonctionnalités

L’application doit posséder une interface graphique pour rentrer 2 nombres et sélectionner un opérateur.

Le calcul doit s’opérer au clic d’un bouton et le résultat doit s’afficher à la suite sans recharger la page.

### Éléments donnés

Code de la page HTML :

```html
<!DOCTYPE html>
<html>
<head>
    <title>Calculatrice</title>
</head>
<body>
    <h1>Calculatrice</h1>
    <section>
        <h2>Calcul</h2>
        <form id="calculForm" style="display: inline;">
            <input type="number" id="nb1">
            <select id="operateur">
                <option value="plus">+</option>
                <option value="moins">-</option>
                <option value="multiplier">×</option>
                <option value="diviser">÷</option>
            </select>
            <input type="number" id="nb2">
            <button type="submit">=</button>
        </form>
    </section>
    <section>
        <h2>Résultat</h2>
        <div id="resultat">

        </div>
    </section>
</body>
</html>
```

### Contraintes

- Ne pas modifier l’HTML fourni (à part pour lier votre fichier JS)
- Le résultat doit s’afficher dans la div « resultat »

### Critères de réussite

A la soumission du formulaire via le bouton « = », le bon résultat s’affiche et la page ne se recharge pas quelles que soient les valeurs rentrées. Si aucune valeur n’est rentrée dans un champ, l’application le fait savoir via une alert JavaScript.

### Pour aller plus loin

Vous pouvez remplacer les 3 champs du formulaire par 1 seul et unique champ texte dans lequel pourront être rentrées des strings tels que « 4+32 » ou « 16*2 ». Celles-ci devront être interprétées dans JavaScript en recherchant les caractères des opérateurs (« + », « - », « * » ou « / »), puis en isolant les nombres avant et après pour les transformer en valeurs numériques avant d’effectuer le calcul en fonction de l’opérateur trouvé.

### Astuces

#### Astuce 1

Pour bloquer le chargement suite à la soumission du formulaire, il est possible de stopper un évènement en JavaScript via la fonction « preventDefault() ».

#### Astuce 2

Pour récupérer l’évènement de soumission du formulaire, il sera nécessaire d’appliquer un « eventListener » sur le formulaire de calcul.

#### Astuce 3

Pour récupérer la valeur d’un champ en JavaScript, il faut tout d’abord récupérer l’élément HTML via un « document.getElementById() » ou un « document.querySelector » par exemple, et y accoler « .value ».