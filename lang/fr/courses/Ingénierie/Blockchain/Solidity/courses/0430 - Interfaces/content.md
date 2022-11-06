Les interfaces sont similaires aux contrats abstraits et sont créées à l'aide du mot clé interface. Voici les principales caractéristiques d'une interface :

- L'interface ne peut pas avoir de fonction avec implémentation.
- Les fonctions d'une interface ne peuvent être que de type externe.
- L'interface ne peut pas avoir de constructeur.
- L'interface ne peut pas avoir de variables d'état.
- Une interface peut avoir des enum, des structs auxquels on peut accéder en utilisant la notation par points du nom de l'interface.

## Exemple

Essayez le code suivant pour comprendre comment l'interface fonctionne dans Solidity.

```solidity
pragma solidity ^0.5.0;

interface Calculator {
    function getResult() external view returns(uint);
}
contract Test is Calculator {
    constructor() public {}
    function getResult() external view returns(uint){
        uint a = 1; 
        uint b = 2;
        uint result = a + b;
        return result;
    }
}
```

__Remarque__ : Sélectionnez ```Test``` dans la liste déroulante avant de cliquer sur le bouton de déploiement.

## Rendu

```solidity
0: uint256: 3
```