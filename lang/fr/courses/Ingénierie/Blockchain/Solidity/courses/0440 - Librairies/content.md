## Généralités

Les bibliothèques sont similaires aux contrats mais sont principalement destinées à être réutilisées. Une bibliothèque contient des fonctions que d'autres contrats peuvent appeler. Solidity impose certaines restrictions quant à l'utilisation d'une bibliothèque. Voici les principales caractéristiques d'une bibliothèque Solidity :

- Les fonctions de la bibliothèque peuvent être appelées directement si elles ne modifient pas l'état. Cela signifie que seules les fonctions pures ou de vue peuvent être appelées depuis l'extérieur de la bibliothèque.
- La bibliothèque ne peut pas être détruite car elle est supposée être sans état.
- Une bibliothèque ne peut pas avoir de variables d'état.
- Une bibliothèque ne peut hériter d'aucun élément.
- Une Library ne peut pas être héritée.

### Exemple

Essayez le code suivant pour comprendre comment fonctionne une bibliothèque dans Solidity :

```solidity
pragma solidity ^0.5.0;

library Search {
    function indexOf(uint[] storage self, uint value) public view returns (uint) {
        for (uint i = 0; i < self.length; i++) if (self[i] == value) return i;
        return uint(-1);
    }
}
contract Test {
    uint[] data;
    constructor() public {
        data.push(1);
        data.push(2);
        data.push(3);
        data.push(4);
        data.push(5);
    }
    function isValuePresent() external view returns(uint){
        uint value = 4;
        
        //search if value is present in the array using Library function
        uint index = Search.indexOf(data, value);
        return index;
    }
}
```

__Remarque__ : Sélectionnez ```Test``` dans la liste déroulante avant de cliquer sur le bouton de déploiement.

### Rendu

```solidity
0: uint256: 3
```

## Utiliser For

La directive ```using A for B ;``` peut être utilisée pour attacher des fonctions de la bibliothèque A à un type B donné. Ces fonctions utilisent le type de l'appelant comme premier paramètre (identifié par self).

### Exemple

Essayez le code suivant pour comprendre comment fonctionne une bibliothèque dans Solidity.

```solidity
pragma solidity ^0.5.0;

library Search {
    function indexOf(uint[] storage self, uint value) public view returns (uint) {
        for (uint i = 0; i < self.length; i++)if (self[i] == value) return i;
        return uint(-1);
    }
}
contract Test {
    using Search for uint[];
    uint[] data;
    constructor() public {
        data.push(1);
        data.push(2);
        data.push(3);
        data.push(4);
        data.push(5);
    }
    function isValuePresent() external view returns(uint){
        uint value = 4;      
        
        //Now data is representing the Library
        uint index = data.indexOf(value);
        return index;
    }
}
```

__Remarque__ : Sélectionnez ```Test``` dans la liste déroulante avant de cliquer sur le bouton de déploiement.

### Rendu

```solidity
0: uint256: 3
```