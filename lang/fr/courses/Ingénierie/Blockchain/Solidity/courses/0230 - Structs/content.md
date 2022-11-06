Les types de structure sont utilisés pour représenter un enregistrement. Supposons que vous vouliez garder la trace de vos livres dans une bibliothèque. Vous voudrez peut-être suivre les attributs suivants pour chaque livre

- Titre
- Auteur
- Sujet
- ID du livre

## Définition d'une structure

Pour définir un **Struct**, vous devez utiliser le mot-clé **struct**. Le mot-clé **struct** définit un nouveau type de données, avec plus d'un membre. Le format de l'instruction **struct** est le suivant :

```solidity
struct struct_name { 
    type1 type_name_1;
    type2 type_name_2;
    type3 type_name_3;
}
```

Exemple :

```solidity
struct Book { 
    string title;
    string author;
    uint book_id;
}
```

## Accès à une structure et à sa variable

Pour accéder à n'importe quel membre d'une structure, nous utilisons l'opérateur d'accès aux membres (.). L'opérateur d'accès aux membres est codé comme un **point** entre le nom de la variable de la structure et le membre de la structure auquel nous souhaitons accéder. Vous utiliserez le **struct** pour définir des variables de type **structure**. L'exemple suivant montre comment utiliser une structure dans un programme :

```solidity
pragma solidity ^0.5.0;

contract test {
    struct Book { 
        string title;
        string author;
        uint book_id;
    }
    Book book;

    function setBook() public {
        book = Book('Learn Java', 'TP', 1);
    }
    function getBookId() public view returns (uint) {
        return book.book_id;
    }
}
```

Cliquez d'abord sur le bouton **setBook** pour définir la valeur **LARGE** puis cliquez sur **getBookId** pour obtenir l'identifiant du livre sélectionné.

Rendu :

```solidity
uint256: 1
```