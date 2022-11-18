## Introduction

L'une des caractéristiques avancées de React est qu'il permet de transmettre un contenu d'interface utilisateur (IU) arbitraire dans le composant à l'aide de propriétés. Par rapport à la propriété children spéciale de React, qui ne permet de transmettre qu'un seul contenu d'interface utilisateur dans le composant, cette option permet de transmettre plusieurs contenus d'interface utilisateur dans le composant. Cette option peut être considérée comme une extension de la propriété children. L'un des cas d'utilisation de cette option est la mise en page de l'interface utilisateur d'un composant.

Par exemple, un composant avec un en-tête et un pied de page personnalisables peut utiliser cette option pour obtenir l'en-tête et le pied de page personnalisés par le biais de propriétés et mettre en page le contenu.

Un exemple simple et rapide avec deux propriétés, l'en-tête et le pied de page, est donné ci-dessous.

```js
<Layout header={<h1>Header</h1>} footer={<p>footer</p>} />
```

Et la logique de rendu de la disposition est la suivante -

```js
return (<div>
    <div> 
        {props.header} 
    </div> 
    <div> 
        Component user interface 
    </div> 
    <div> 
        {props.footer} 
    </div> 
</div>)
```

Ajoutons un en-tête et un pied de page simples à notre composant Liste des entrées de dépenses (ExpenseEntryItemList).

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ensuite, ouvrez le fichier ExpenseEntryItemList.js dans le dossier src/components.

Ensuite, utilisez les props d'en-tête et de pied de page dans la méthode ```render()```.

```js
return (
    <div> 
        <div>{this.props.header}</div> 
            ... existing code ... 
        <div>{this.props.footer}</div> 
    </div> 
);
```

Ensuite, ouvrez index.js et incluez les propriétés d'en-tête et de pied de page tout en utilisant le composant ExpenseEntryItemList.

```js
ReactDOM.render(
    <React.StrictMode>
        <ExpenseEntryItemList items={items}
            header={
                <div><h1>Expense manager</h1></div>
            }
            footer={
                <div style={{ textAlign: "left" }}>
                <p style={{ fontSize: 12 }}>Sample application</p>
                </div>
            } 
        />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

## Partage de logique dans les composants aka Render props

Les props de rendu sont un concept avancé utilisé pour partager la logique entre les composants React. Comme nous l'avons appris précédemment, un composant peut recevoir du contenu arbitraire de l'interface utilisateur ou des éléments React (objets) par le biais de propriétés. Habituellement, le composant rend les éléments React qu'il reçoit tels quels avec sa propre interface utilisateur, comme nous l'avons vu dans le concept des enfants et de la disposition. Ils ne partagent aucune logique entre eux.

En allant un peu plus loin, React permet à un composant de prendre une fonction qui renvoie l'interface utilisateur au lieu d'un objet d'interface utilisateur simple à travers les propriétés. Le seul but de la fonction est de rendre l'interface utilisateur. Ensuite, le composant fera des calculs avancés et appellera la fonction passée avec la valeur calculée pour rendre l'interface utilisateur.

En bref, la propriété du composant, qui accepte une fonction JavaScript qui rend l'interface utilisateur, est appelée Render Props. Le composant qui reçoit les Render Props va faire de la logique avancée et la partager avec les Render Props, qui vont rendre l'interface utilisateur en utilisant la logique partagée.

Beaucoup de bibliothèques tierces avancées sont basées sur les Render Props. Certaines des bibliothèques qui utilisent Render Props sont -

- React Router
- Formik
- Downshift

Par exemple, le composant de la bibliothèque Formik se chargera de la validation et de la soumission du formulaire et transmettra la conception du formulaire à la fonction d'appel (Render Props). De même, React Router s'occupe de la logique de routage tout en déléguant la conception de l'interface utilisateur à d'autres composants à l'aide de Render Props.