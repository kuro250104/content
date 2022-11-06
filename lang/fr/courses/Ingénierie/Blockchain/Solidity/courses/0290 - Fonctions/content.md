Une **fonction** est un groupe de code réutilisable qui peut être appelé n'importe où dans votre programme. Cela élimine la nécessité d'écrire le même code encore et encore. Elle aide les programmeurs à écrire des codes modulaires. Les **fonctions** permettent à un programmeur de diviser un gros programme en un certain nombre de petites fonctions faciles à gérer.

Comme tout autre langage de programmation avancé, Solidity prend également en charge toutes les fonctionnalités nécessaires pour écrire du code modulaire à l'aide de fonctions. Cette section explique comment écrire vos propres fonctions dans Solidity.

## Définition des fonctions

Avant d'utiliser une fonction, nous devons la définir. La façon la plus courante de définir une fonction dans Solidity est d'utiliser le mot-clé function, suivi d'un nom de fonction unique, d'une liste de paramètres (qui peut être vide) et d'un bloc d'instructions entouré d'accolades.

### Syntaxe

La syntaxe de base est présentée ici.

```solidity
function function-name(parameter-list) scope returns() {
    //statements
}
```

### Exemple

Essayez l'exemple suivant. Il définit une fonction appelée **getResult** qui ne prend pas de paramètres.

```solidity
pragma solidity ^0.5.0;

contract Test {
    function getResult() public view returns(uint){
        uint a = 1; // local variable
        uint b = 2;
        uint result = a + b;
        return result;
    }
}
```

## Appel d'une fonction

Pour invoquer une fonction quelque part dans le contrat, il suffit d'écrire le nom de cette fonction comme indiqué dans le code suivant.

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
        return string(bstr);//access local variable
    }
}
```

Rendu : 

```solidity
0: string: 3
```

## Paramètres de fonction

Jusqu'à présent, nous avons vu des fonctions sans paramètres. Mais il est possible de passer différents paramètres en appelant une fonction. Ces paramètres passés peuvent être capturés à l'intérieur de la fonction et toute manipulation peut être faite sur ces paramètres. Une fonction peut prendre plusieurs paramètres séparés par une virgule.

### Exemple

Essayez l'exemple suivant. Nous avons utilisé ici une fonction **uint2str**. Elle prend un paramètre.

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
        return string(bstr);//access local variable
    }
}
```

### Rendu

```solidity
0: string: 3
```

## L'instruction de retour

Une fonction Solidity peut avoir une déclaration de retour facultative. Cette instruction est nécessaire si vous voulez renvoyer une valeur à partir d'une fonction. Cette instruction doit être la dernière instruction d'une fonction.

Dans l'exemple ci-dessus, nous utilisons la fonction **uint2str** pour retourner une chaîne de caractères.

Dans Solidity, une fonction peut également renvoyer plusieurs valeurs. Voir l'exemple ci-dessous :

```solidity
pragma solidity ^0.5.0;

contract Test {
    function getResult() public view returns(uint product, uint sum){
        uint a = 1; // local variable
        uint b = 2;
        product = a * b;
        sum = a + b;
    
        //alternative return statement to return 
        //multiple values
        //return(a*b, a+b);
    }
}
```

Rendu : 

```solidity
0: uint256: product 2
1: uint256: sum 3
```