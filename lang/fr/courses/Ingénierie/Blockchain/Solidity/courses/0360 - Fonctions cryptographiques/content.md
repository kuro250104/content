Solidity fournit également des fonctions cryptographiques intégrées. Les méthodes suivantes sont importantes

- ```keccak256(bytes memory) returns (bytes32)``` - calcule le hachage Keccak-256 de l'entrée.
- ```sha256(bytes memory) returns (bytes32)``` - calcule le hachage SHA-256 de l'entrée.
- ```ripemd160(bytes memory) returns (bytes20)``` - calcule le hachage RIPEMD-160 de l'entrée.
- ```sha256(bytes memory) returns (bytes32)``` - calcule le hachage SHA-256 de l'entrée.
- ```ecrecover(bytes32 hash, uint8 v, bytes32 r, bytes32 s) renvoie (adresse)``` - récupère l'adresse associée à la clé publique de la signature de la courbe elliptique ou renvoie zéro en cas d'erreur. Les paramètres de la fonction correspondent aux valeurs ECDSA de la signature : r - 32 premiers octets de la signature ; s : 32 seconds octets de la signature ; v : 1 dernier octet de la signature. Cette méthode renvoie une adresse.

L'exemple suivant montre l'utilisation de la fonction cryptographique dans Solidity.

## Exemple

```solidity
pragma solidity ^0.5.0;

contract Test {   
    function callKeccak256() public pure returns(bytes32 result){
        return keccak256("ABC");
    }
}
```

## Rendu

```solidity
0: bytes32: result 0xe1629b9dda060bb30c7908346f6af189c16773fa148d3366701fbaa35d54f3c8
```