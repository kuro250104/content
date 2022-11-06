Un contrat abstrait est un contrat qui contient au moins une fonction sans aucune implémentation. Un tel contrat est utilisé comme contrat de base. En général, un contrat abstrait contient à la fois des fonctions implémentées et des fonctions abstraites. Le contrat dérivé implémente la fonction abstraite et utilisera les fonctions existantes en cas de besoin.

Dans le cas où un contrat dérivé n'implémente pas la fonction abstraite, ce contrat dérivé sera marqué comme abstrait.

## Exemple

Essayez le code suivant pour comprendre comment les contrats abstraits fonctionnent dans Solidity.

```solidity
pragma solidity ^0.5.0;

contract Calculator {
    function getResult() public view returns(uint);
}
contract Test is Calculator {
    function getResult() public view returns(uint) {
        uint a = 1;
        uint b = 2;
        uint result = a + b;
        return result;
    }
}
```

## Rendu

```solidity
0: uint256: 3
```