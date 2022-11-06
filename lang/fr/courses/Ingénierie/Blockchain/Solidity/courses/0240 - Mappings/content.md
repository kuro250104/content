Le **mapping** est un **type de référence** comme les tableaux et les structures. Voici la syntaxe pour déclarer un type de mapping :

```solidity
mapping(_KeyType => _ValueType)
```

Où :

- ```_KeyType``` - peut être n'importe quel type intégré, plus les octets et les chaînes de caractères. Les types de référence et les objets complexes ne sont pas autorisés.
- ```_ValueType``` - peut être n'importe quel type.

## Considérations

- Le **mapping** ne peut avoir qu'**un type de stockage** et est généralement utilisé pour les variables d'état.
- Le **mapping** peut être marqué public. Solidity crée automatiquement un getter pour celui-ci.

## Example

Essayez le code suivant pour comprendre comment le type de mapping fonctionne dans Solidity.

```solidity
pragma solidity ^0.5.0;

contract LedgerBalance {
    mapping(address => uint) public balances;

    function updateBalance(uint newBalance) public {
        balances[msg.sender] = newBalance;
    }
}
contract Updater {
    function updateBalance() public returns (uint) {
        LedgerBalance ledgerBalance = new LedgerBalance();
        ledgerBalance.updateBalance(10);
        return ledgerBalance.balances(address(this));
    }
}
```

Cliquez d'abord sur le bouton **updateBalance** pour fixer la valeur à **10**, puis regardez les journaux qui montreront la sortie décodée comme -.

## Rendu

```solidity
{
    "0": "uint256: 10"
}
```