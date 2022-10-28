Le CSS2 a présenté la règle ```@media```, permettant de définir un style pour différents types d’appareils. 

C’est à partir du CSS3 que le principe des media queries à été lancé. Avec ces queries (requêtes, en anglais), il n’est plus seulement question de définir un type de média pour lequel afficher un style bien particulier, mais il s’agit de regarder la capacité de l’appareil utilisé pour consulter un site web. Ainsi les media queries vont-elles plus loin. Elles permettent, par exemple, de vérifier :

- La largeur et la hauteur du viewport
- La largeur et la hauteur de l’appareil utilisé
- L’orientation de l’appareil (la tablette ou le téléphone est-il en mode portrait ou paysage ?)
- La résolution

L’utilisation des media queries est très démocratisée afin de rendre un site accessible pour tout type de média tel qu’un ordinateur de bureau, un ordinateur portable, un téléphone, une tablette, une télé, etc. Cela permet de créer un site web dit **responsive**, c’est-à-dire un site web qui s’adapte à tout type de média. 

## Syntaxe

Voici la syntaxe des media queries :

```css
@media not | only type_de_media and (expressions) {
	// Code CSS
}
```

Comme démontré ci-dessus, les media queries consistent à définir un type de média et elles peuvent contenir 1 ou plusieurs expressions. Le bloc de media queries, par la suite, retourne une valeur true (vrai, en anglais), si le type de média utilisé correspond au type de média défini dans la règle ```@media```. Si tel est le cas, toutes les expressions sont vraies et le code CSS écrit dans le bloc est appliqué. 

__Remarque__ : À moins que les opérateurs ```not``` ou ```only``` soient utilisés, le type de média est optionnel. Cela aura pour conséquence que le code CSS écrit dans le bloc de media queries s’appliquera à tous les types de médias.

## Types de médias

Voici un tableau énumérant les différents types de médias disponibles en CSS3 :

| **Valeur** | **Description** |
| --- | --- |
| all | Utilisé pour tous les types d'appareils |
| print | Utilisé pour les imprimantes |
| screen | Utilisé pour les écrans d’ordinateurs, tablettes, smartphones, etc. |
| speech | Utilisés pour les appareils qui “lisent” à haute voix le contenu affiché à l’écran |

Exemple d’utilisation des media queries :

```css
@media screen and (min-width: 480px) /* Pour les médias de type screen avec une largeur minimum de 480px */ {
	nav {
		display: none; /* Le menu disparaît */
	}
}
```