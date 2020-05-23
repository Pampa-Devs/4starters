# 🔢 Coleções de Tipos

Em diversas situações, você irá necessitar gerenciar um grupo de objetos. Existe duas maneiras de agrupar objetos no C#:

* Matrizes de objetos
* Coleções de objetos

## Matrizes

Também conhecidas como `array`. permitem a armazenação de vários objetos de um mesmo tipo. Ela também pode armazenar elementos de qualquer tipo, especificando `object` como o tipo da matriz.
As matrizes são frequentemente utilizadas para trabalhar com um **número fixo** de objetos.

### Estrutura
```C#
int[] arrayInt;

object[] arrayObject;
```

### Exemplo

#### Matrizes unidimensionais:
Declaração de uma matriz unidimensional de tamanho 5
```C#
int [] array1 = new int[5];
```

Declaração e população da matriz com elementos
```C#
int [] array2 = new int[] { 1, 3, 5, 7, 9};
```

Sintaxe alternativa para popular a matriz com elementos
```C#
int [] array3 = { 1, 3, 5, 7, 9};
```

Lendo os valores de uma matriz unidimensional:
```C#
int [] array2 = new int[] { 1, 3, 5, 7, 9};

Console.WriteLine(array2[0]); // Exibe 1
Console.WriteLine(array2[2]); // Exibe 5
```

#### Matrizes multidimensionais:
Declaração de uma matriz multidimensional 2 por 3, ao todo ela tem 6 elementos
```C#
int [,] array1 = new int [2, 3];
```

Declaração de uma matriz multidimensional 4 por 2 populada
| 1 | 2 |
| :---: | :---: |
| 3 | 4 |
| 5 | 6 |
| 7 | 8 |
```C#
int[,] array2 = new int[4, 2] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };
```

#### Matrizes *denteadas*: