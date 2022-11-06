Solidity offre la possibilité d'utiliser le langage assembleur pour écrire un code assembleur en ligne dans le code source de Solidity. Nous pouvons également écrire un code assembleur autonome qui sera ensuite converti en bytecode. Standalone Assembly est un langage intermédiaire pour un compilateur Solidity et il convertit le code Solidity en Standalone Assembly puis en byte code. Nous pouvons utiliser le même langage que celui utilisé dans Inline Assembly pour écrire du code dans un Standalone Assembly.

## Assembleur en ligne

Le code assembleur en ligne peut être intercalé dans la base de code Solidity afin d'avoir un contrôle plus fin sur EVM. Il est utilisé en particulier lors de l'écriture des fonctions de bibliothèque.

Un code assembleur est écrit sous le bloc assembly { ... }.

## Exemple

Essayez le code suivant pour comprendre comment fonctionne une bibliothèque dans Solidity.

```solidity
pragma solidity ^0.5.0;

library Sum {   
    function sumUsingInlineAssembly(uint[] memory _data) public pure returns (uint o_sum) {
        for (uint i = 0; i < _data.length; ++i) {
            assembly {
                o_sum := add(o_sum, mload(add(add(_data, 0x20), mul(i, 0x20))))
            }
        }
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
    function sum() external view returns(uint){      
        return Sum.sumUsingInlineAssembly(data);
    }
}
```

__Remarque__ : Sélectionnez ```Test``` dans la liste déroulante avant de cliquer sur le bouton de déploiement.

## Rendu

```solidity
0: uint256: 15
```