Les fonctions pures garantissent qu'elles ne lisent ni ne modifient l'état. Une fonction peut être déclarée comme pure. Les déclarations suivantes, si elles sont présentes dans la fonction, sont considérées comme lisant l'état et le compilateur lancera un avertissement dans de tels cas.

- Lecture des variables d'état.
- Accès à l'adresse ```(this).balance``` ou ```<address>.balance```.
- Accès à l'une des variables spéciales de block, tx, msg (```msg.sig``` et ```msg.data``` peuvent être lus).
- L'appel de toute fonction non marquée pure.
- L'utilisation d'un assemblage en ligne qui contient certains opcodes.

Les fonctions pures peuvent utiliser les fonctions ```revert()``` et ```require()``` pour revenir sur les changements d'état potentiels si une erreur se produit. Voir l'exemple ci-dessous utilisant une fonction de vue.

## Exemple

```solidity
pragma solidity ^0.5.0;

contract Test {
    function getResult() public pure returns(uint product, uint sum){
        uint a = 1; 
        uint b = 2;
        product = a * b;
        sum = a + b; 
    }
}
```

## Rendu

```solidity
0: uint256: product 2
1: uint256: sum 3
```