Solidity fournit également des fonctions mathématiques intégrées. Voici les méthodes les plus utilisées

- ```addmod(uint x, uint y, uint k) renvoie (uint)``` - calcule ```(x + y) % k``` où l'addition est effectuée avec une précision arbitraire et ne s'enroule pas autour de 2^256.
- ```mulmod(uint x, uint y, uint k) renvoie (uint)``` - calcule ```(x * y) % k``` où l'addition est effectuée avec une précision arbitraire et ne s'enroule pas autour de 2^256.

L'exemple suivant montre l'utilisation des fonctions mathématiques dans Solidity.

## Exemple

```solidity
pragma solidity ^0.5.0;

contract Test {   
    function callAddMod() public pure returns(uint){
        return addmod(4, 5, 3);
    }
    function callMulMod() public pure returns(uint){
        return mulmod(4, 5, 3);
    }
}
```

Cliquez d'abord sur le bouton **callAddMod** puis sur le bouton **callMulMod** pour voir le résultat.

## Rendu

```solidity
0: uint256: 0
0: uint256: 2
```