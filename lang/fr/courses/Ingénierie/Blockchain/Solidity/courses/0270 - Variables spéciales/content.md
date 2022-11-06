Les variables spéciales sont des variables disponibles dans le monde entier et fournissent des informations sur la blockchain. Voici la liste des variables spéciales

- ```blockhash(uint blockNumber) returns (bytes32)``` : Hash du bloc donné - ne fonctionne que pour les 256 blocs les plus récents, à l'exclusion des blocs actuels.
- ```block.coinbase (address payable)``` : Adresse du mineur du bloc actuel.
- ```block.difficulty (uint)``` : la difficulté du bloc actuel.
- ```block.gaslimit (uint)``` : Limite de gaz du bloc actuel.
- ```block.number (uint)``` : Numéro du bloc actuel.
- ```block.timestamp``` : Horodatage du bloc actuel en secondes depuis l'époque unix.
- ```gasleft() returns (uint256)``` : Gaz restant.
- ```msg.data (bytes calldata)``` : Données d'appel complètes.
- ```msg.sender (address payable)``` : Expéditeur du message (appel en cours).
- ```msg.sig (bytes4)``` : Les quatre premiers octets des données d'appel (c'est-à-dire l'identifiant de la fonction).
- ```msg.value (uint)``` : Nombre de wei envoyés avec le message.
- ```now (uint)``` : Horodatage du bloc actuel (alias pour block.timestamp).
- ```tx.gasprice (uint)``` : Prix du gaz de la transaction.
- ```tx.origin (address payable)``` : Expéditeur de la transaction (chaîne d'appel complète).

## Exemple

Essayez le code suivant pour voir l'utilisation de msg, une variable spéciale pour obtenir l'adresse de l'expéditeur dans Solidity.

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

Cliquez d'abord sur le bouton **updateBalance** pour fixer la valeur à **10**, puis regardez les journaux qui montreront la sortie décodée :

```solidity
{
    "0": "uint256: 10"
}
```