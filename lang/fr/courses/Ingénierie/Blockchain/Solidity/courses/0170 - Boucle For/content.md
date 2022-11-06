La boucle **for** est la forme la plus compacte de bouclage. Elle comprend les trois parties importantes suivantes :

- **L'initialisation de la boucle** où nous initialisons notre compteur à une valeur de départ. L'instruction d'initialisation est exécutée avant le début de la boucle.
- **L'instruction de test** qui vérifie si une condition donnée est vraie ou non. Si la condition est vraie, alors le code donné à l'intérieur de la boucle sera exécuté, sinon le contrôle sortira de la boucle.
- **L'instruction d'itération** où vous pouvez augmenter ou diminuer votre compteur.

Vous pouvez placer ces trois parties sur une seule ligne en les séparant par des points-virgules.

## Syntaxe

La syntaxe de la boucle **for** dans Solidity est la suivante :

```solidity
for (initialization; test condition; iteration statement) {
    Statement(s) to be executed if test condition is true
}
```

## Exemple

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    uint storedData; 
    constructor() public{
        storedData = 10;   
    }

    function getResult() public view returns(string memory){
        uint a = 10; 
        uint b = 2;
        uint result = a + b;
        return integerToString(result); 
    }

    function integerToString(uint _i) internal pure 
        returns (string memory) {
        if (_i == 0) {
            return "0";
        }
        uint j=0;
        uint len;
        for (j = _i; j != 0; j /= 10) {  //for loop example
            len++;         
        }
        bytes memory bstr = new bytes(len);
        uint k = len - 1;
        while (_i != 0) {
            bstr[k--] = byte(uint8(48 + _i % 10));
            _i /= 10;
        }
        return string(bstr);//access local variable
    }
}
```

Rendu :

```solidity
0: string: 12
```