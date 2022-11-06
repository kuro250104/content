Solidity permet la conversion implicite et explicite. Le compilateur Solidity permet la conversion implicite entre deux types de données à condition qu'aucune conversion implicite ne soit possible et qu'il n'y ait pas de perte d'information. Par exemple, uint8 est convertible en uint16 mais int8 n’est pas convertible en uint256 car int8 peut contenir une valeur négative non autorisée dans uint256.

## Conversion explicite

Nous pouvons convertir explicitement un type de données en un autre en utilisant la syntaxe des constructeurs.

```solidity
int8 y = -3;
uint x = uint(y);
// Now x = 0xfffff..fd == two complement representation of -3 in 256 bit format.
```

La conversion à des caractères plus petits coûte des bits d'ordre supérieur.

```solidity
uint32 a = 0x12345678;
uint16 b = uint16(a); // b = 0x5678
```

La conversion en un type supérieur ajoute des bits de remplissage à gauche.

```solidity
uint16 a = 0x1234;
uint32 b = uint32(a); // b = 0x00001234
```

La conversion en octets plus petits coûte des données d'ordre supérieur.

```solidity
bytes2 a = 0x1234;
bytes1 b = bytes1(a); // b = 0x12
```

La conversion en octet plus grand ajoute des bits de remplissage à droite.

```solidity
bytes2 a = 0x1234;
bytes4 b = bytes4(a); // b = 0x12340000
```

La conversion entre des octets de taille fixe et des int n'est possible que si les deux sont de même taille.

```solidity
bytes2 a = 0x1234;
uint32 b = uint16(a); // b = 0x00001234
uint32 c = uint32(bytes4(a)); // c = 0x12340000
uint8 d = uint8(uint16(a)); // d = 0x34
uint8 e = uint8(bytes1(a)); // e = 0x12
```

Les nombres hexadécimaux peuvent être affectés à n'importe quel type de nombre entier si aucune troncature n'est nécessaire.

```solidity
uint8 a = 12; // no error
uint32 b = 1234; // no error
uint16 c = 0x123456; // error, as truncation required to 0x3456
```