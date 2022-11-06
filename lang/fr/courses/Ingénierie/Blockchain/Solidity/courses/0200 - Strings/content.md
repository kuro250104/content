Solidity prend en charge les chaînes de type **String** en utilisant à la fois les guillemets doubles (") et les guillemets simples ('). Il fournit **string** comme type de données pour déclarer une variable de type **String**.

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    string data = "test";
}
```

Dans l'exemple ci-dessus, "**test**" est une chaîne de caractères et **data** est une variable de type **string**. Il est préférable d'utiliser des types d'octets plutôt que des chaînes de caractères, car les opérations sur les chaînes de caractères nécessitent plus de gaz que celles sur les octets. Solidity fournit une conversion intégrée entre les octets et les chaînes de caractères et vice versa. Dans Solidity, nous pouvons facilement affecter un littéral String à une variable de type byte32. Solidity le considère comme un littéral de type byte32.

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    bytes32 data = "test";
}
```

## Caractères d’échappement

Comme pour d’autres langages, Solidity met à disposition un caractère d'échappement afin de permettre d’afficher dans les chaînes de caractères certains symboles spécifiques : 

- ```\n``` : Démarre une nouvelle ligne
- ```\\``` : Backslash
- ```\’``` : guillemet simple
- ```\”``` : guillemet double
- ```\b``` : retour en arrière
- ```\f``` : Alimentation en formulaires
- ```\r``` : retour chariot
- ```\t``` : tabulation
- ```\v``` : tabulation vertical
- ```\xNN``` : Représente une valeur hexadécimale et insère les octets appropriés.
- ```\uNNNN``` : Représente une valeur Unicode et insère une séquence UTF-8.

## Conversion d'octets en chaîne de caractères

Les octets peuvent être convertis en chaîne de caractères à l'aide du constructeur ```string()``` :

```solidity
bytes memory bstr = new bytes(10);
string message = string(bstr);
```

### Exemple

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {   
    constructor() public{       
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
        
        while (j != 0) {
            len++;
            j /= 10;
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

### Rendu

```solidity
0: string: 3
```