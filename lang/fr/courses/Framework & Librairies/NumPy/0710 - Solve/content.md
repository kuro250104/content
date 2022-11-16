## Introduction

La fonction ```numpy.linalg.solve()``` donne la solution d'équations linéaires sous forme de matrice.

Considérant les équations linéaires suivantes -

- ```x + y + z = 6```
- ```2y + 5z = -4```
- ```2x + 5y - z = 27```

Ils peuvent être représentés sous forme de matrice comme -

```
$$\begin{bmatrix}1 & 1 & 1 \\0 & 2 & 5 \\2 & 5 & -1\end{bmatrix} \begin{bmatrix}x \\y \\z \end{bmatrix} = \begin{bmatrix}6 \\-4 \\27 \end{bmatrix}$$
```

Si ces trois matrices sont appelées A, X et B, l'équation devient -

```
A*X = B  
```

Ou

```
X = A-1B
```