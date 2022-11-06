
Lorsque vous écrivez un programme dans n'importe quel langage, vous devez utiliser différentes variables pour stocker diverses informations. Les variables ne sont rien d'autre que des emplacements mémoire réservés pour stocker des valeurs. Cela signifie que lorsque vous créez une variable, vous réservez un certain espace en mémoire.

Vous pouvez souhaiter stocker des informations de différents types de données, comme des caractères, des caractères larges, des nombres entiers, des nombres à virgule flottante, des nombres à virgule flottante double, des booléens, etc. En fonction du type de données d'une variable, le système d'exploitation alloue de la mémoire et décide de ce qui peut être stocké dans la mémoire réservée.

## Types de valeurs

Solidity offre au programmeur un riche assortiment de types de données intégrés et définis par l'utilisateur. Le tableau suivant énumère les sept types de données C++ de base.

| **Type** | **Mot-clé** | **Valeurs** |
| --- | --- | --- |
| Boolean | bool | vrai/faux |
| Integer | int/uint | Des entiers signés et non signés de tailles différentes. |
| Integer | int8 jusqu’à int256 | Int signé de 8 bits à 256 bits. int256 est identique à int |
| Integer | uint8 to uint256 | Int non signé de 8 bits à 256 bits. uint256 est identique à uint. |
| Fixed Point Numbers | fixed/unfixed | Nombres à virgule fixe signés et non signés de tailles diverses. |
| Fixed Point Numbers | fixedMxN | Nombre signé à virgule fixe où M représente le nombre de bits pris par le type et N représente les points décimaux. M doit être divisible par 8 et va de 8 à 256. N peut aller de 0 à 80. Fixe est identique à Fixe128x18. |
| Fixed Point Numbers | ufixedMxN | Nombre à virgule fixe non signé où M représente le nombre de bits pris par le type et N représente les points décimaux. M doit être divisible par 8 et va de 8 à 256. N peut aller de 0 à 80. ufixed est identique à ufixed128x18. |

## adresse

L'adresse contient la valeur de 20 octets représentant la taille d'une adresse Ethereum. Une adresse peut être utilisée pour obtenir le solde en utilisant la méthode ```.balance``` et peut être utilisée pour transférer le solde vers une autre adresse en utilisant la méthode ```.transfer```.

```solidity
address x = 0x212;
address myAddress = this;
if (x.balance < 10 && myAddress.balance >= 10) x.transfer(10);
```