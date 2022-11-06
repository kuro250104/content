Les fonctions de vue garantissent qu'elles ne modifieront pas l'état. Une fonction peut être déclarée en tant que vue. Les déclarations suivantes, si elles sont présentes dans la fonction, sont considérées comme modifiant l'état et le compilateur émettra un avertissement dans ce cas.

- Modifier les variables d'état.
- Émettre des événements.
- Créer d'autres contrats.
- Utiliser l'autodestruction.
- Envoyer de l'Ether via des appels.
- Appeler toute fonction qui n'est pas marquée view ou pure.
- Utiliser des appels de bas niveau.
- Utiliser un assemblage en ligne contenant certains opcodes.

Les méthodes Getter sont par défaut des fonctions de vue. Voir l'exemple ci-dessous qui utilise une fonction de vue :

## Exemple

```solidity
pragma solidity ^0.5.0;

contract Test {
    function getResult() public view returns(uint product, uint sum){
        uint a = 1; // local variable
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