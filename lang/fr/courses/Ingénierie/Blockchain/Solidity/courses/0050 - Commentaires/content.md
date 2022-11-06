Solidity supporte à la fois les commentaires de style C et de style C++. Ainsi :

- Tout texte entre un // et la fin d'une ligne est traité comme un commentaire et est ignoré par le compilateur Solidity.
- Tout texte entre les caractères /* et */ est traité comme un commentaire. Il peut s'étendre sur plusieurs lignes.

L'exemple suivant montre comment utiliser les commentaires dans Solidity :

```solidity
function getResult() public view returns(uint){
    // This is a comment. It is similar to comments in C++

    /*
        * This is a multi-line comment in solidity
        * It is very similar to comments in C Programming
    */
    uint a = 1;
    uint b = 2;
    uint result = a + b;
    return result;
}
```