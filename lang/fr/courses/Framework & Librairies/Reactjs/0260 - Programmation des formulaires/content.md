## Introduction

La nature de la programmation des formulaires exige que l'état soit maintenu. En effet, les informations des champs de saisie sont modifiées lorsque l'utilisateur interagit avec le formulaire. Mais comme nous l'avons appris précédemment, la bibliothèque React ne stocke ou ne maintient aucune information d'état par elle-même et le composant doit utiliser l'API de gestion d'état pour gérer l'état. Compte tenu de cela, React fournit deux types de composants pour supporter la programmation de formulaires.

- **Controlled component** − Dans le composant contrôlé, React fournit un attribut spécial, valeur pour tous les éléments de saisie et contrôle les éléments de saisie. L'attribut value peut être utilisé pour obtenir et définir la valeur de l'élément d'entrée. Il doit être synchronisé avec l'état du composant.
- **Uncontrolled component** − Dans un composant non contrôlé, React fournit un support minimal pour la programmation de formulaire. Il doit utiliser le concept Ref (un autre concept React pour obtenir un élément DOM dans le composant React pendant l'exécution) pour faire la programmation du formulaire.

Dans les prochains cours, nous allons apprendre la programmation de formulaires en utilisant des composants contrôlés et non contrôlés.