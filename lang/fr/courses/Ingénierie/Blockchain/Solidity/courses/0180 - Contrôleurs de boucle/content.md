Solidity offre un contrôle total pour gérer les boucles et les instructions de commutation. Il peut arriver que vous ayez besoin de sortir d'une boucle sans en atteindre le fond. Il peut également arriver que vous souhaitiez sauter une partie de votre bloc de code et commencer l'itération suivante de la boucle.

Pour gérer toutes ces situations, Solidity fournit des instructions **break** et **continue**. Ces instructions sont utilisées respectivement pour sortir immédiatement d'une boucle ou pour commencer l'itération suivante d'une boucle.

## L'instruction break

L'instruction break est utilisée pour sortir prématurément d'une boucle, en se détachant des accolades qui l'entourent.

Exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    uint storedData; 
    constructor() public{
        storedData = 10;   
    }
    function getResult() public view returns(string memory){
        uint a = 1; 
        uint b = 2;
        uint result = a + b;
        return integerToString(result); 
    }
    function integerToString(uint _i) internal pure 
        returns (string memory) {
        
        if (_i == 0) {
            return "0";
        }
        uint j = _i;
        uint len;
        
        while (true) {
            len++;
            j /= 10;
            if(j==0){
                break;   //using break statement
            }
        }
        bytes memory bstr = new bytes(len);
        uint k = len - 1;
        
        while (_i != 0) {
            bstr[k--] = byte(uint8(48 + _i % 10));
            _i /= 10;
        }
        return string(bstr);
    }
}
```

Rendu :

```solidity
0: string: 3
```

## L'instruction continue

L'instruction **continue** indique à l'interpréteur de commencer immédiatement l'itération suivante de la boucle et de sauter le bloc de code restant. Lorsqu'une instruction **continue** est rencontrée, le programme passe immédiatement à l'expression de contrôle de la boucle et si la condition reste vraie, il lance l'itération suivante, sinon le contrôle sort de la boucle.

Exemple : 

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    uint storedData; 
    constructor() public{
        storedData = 10;   
    }
    function getResult() public view returns(string memory){
        uint n = 1;
        uint sum = 0;

        while( n < 10){
            n++;
            if(n == 5){
                continue; // skip n in sum when it is 5.
            }
            sum = sum + n;
        }
        return integerToString(sum); 
    }
    function integerToString(uint _i) internal pure 
        returns (string memory) {

        if (_i == 0) {
            return "0";
        }
        uint j = _i;
        uint len;

        while (true) {
            len++;
            j /= 10;
            if(j==0){
                break;   //using break statement
            }
        }
        bytes memory bstr = new bytes(len);
        uint k = len - 1;

        while (_i != 0) {
            bstr[k--] = byte(uint8(48 + _i % 10));
            _i /= 10;
        }
        return string(bstr);
    }
}
```

Rendu : 

```solidity
0: string: 49
```