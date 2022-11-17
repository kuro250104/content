## Introduction

React permet aux développeurs de créer des composants dynamiques et avancés en utilisant des propriétés. Chaque composant peut avoir des attributs similaires aux attributs HTML et la valeur de chaque attribut est accessible à l'intérieur du composant en utilisant les propriétés (props).

Par exemple, on peut accéder au composant Hello avec un attribut de nom à l'intérieur du composant par le biais de la variable this.props.name.

```js
<Hello name="React" />
// value of name will be "Hello* const name = this.props.name
```

Les propriétés React supportent les valeurs d'attributs de différents types. Ils sont les suivants,

- Chaîne de caractères
- Numéro
- Datetime
- Array
- Liste
- Objets

Apprenons un par un dans ce chapitre.

- Créer un composant en utilisant les propriétés
- Composants imbriqués
- Composant d'utilisation
- Collection de composants