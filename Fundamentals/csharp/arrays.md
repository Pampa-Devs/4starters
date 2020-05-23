# Matrizes

Também conhecidas como `array`. permitem a armazenação de vários objetos de um mesmo tipo. Ela também pode armazenar elementos de qualquer tipo, especificando `object` como o tipo da matriz.
As matrizes são frequentemente utilizadas para trabalhar com um **número fixo** de objetos.

## Estrutura
```C#
int[] arrayInt;

object[] arrayObject;
```

## Exemplo

### Matrizes unidimensionais:
Declaração de uma matriz unidimensional de tamanho 5
```C#
int [] array1 = new int[5];
```

Declaração e população da matriz com elementos
```C#
int [] array2 = new int[] { 1, 3, 5, 7, 9};
```

| Posição | 0 | 1 | 2 | 3 | 4 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **Elementos** | 1 | 3 | 5 | 7 | 9 |

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

### Matrizes multidimensionais:
Declaração de uma matriz multidimensional 2 por 3, ao todo ela tem 6 elementos
```C#
int [,] array1 = new int [2, 3];
```

Declaração de uma matriz multidimensional 4 por 2 populada
```C#
int[,] array2 = new int[4, 2] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };
```
| 1 | 2 |
| :---: | :---: |
| **3** | **4** |
| **5** | **6** |
| **7** | **8** |

Lendo os valores de uma matriz multidimensional:
```C#
int[,] array = new int[4, 2] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };

Console.WriteLine(array[0, 0]); // Exibe 1
Console.WriteLine(array[0, 1]); // Exibe 2
Console.WriteLine(array[1, 0]); // Exibe 3
Console.WriteLine(array[3, 1]); // Exibe 8
```

### Matrizes *denteadas*:
Também conhecidas como matriz de matrizes.

Declaração de uma matriz *denteada*:
```C#
int [4][] array = new int [4][];
```

Populando uma matriz denteada populada
```C#
int [][] jaggedArray = new int[3][];

jaggedArray[0] = new int[4] { 1, 2, 3, 4};
jaggedArray[1] = new int[1] { 5 };
jaggedArray[2] = new int[5] { 6, 7, 8, 9, 10 };
jaggedArray[3] = new int[2] { 11, 12 };
```

| # | Matriz 0 | Matriz 1 | Matriz 2 | Matriz 3 |
| :---: | :---: | :---: | :---: | :---: |
| **0** | 1 | 5 | 6 | 11 |
| **1** | 2 | - | 7 | 12 |
| **2** | 3 | - | 8 | - |
| **3** | 4 | - | 9 | - |
| **4** | - | - | 10 | - |

Lendo os valores de uma matriz denteada:
```C#
int [][] jaggedArray = new int[3][];

jaggedArray[0] = new int[4] { 1, 2, 3, 4};
jaggedArray[1] = new int[1] { 5 };
jaggedArray[2] = new int[5] { 6, 7, 8, 9, 10 };
jaggedArray[3] = new int[2] { 11, 12 };

Console.WriteLine(array[0][0]); // Exibe 1
Console.WriteLine(array[0][1]); // Exibe 2
Console.WriteLine(array[1][0]); // Exibe 5
Console.WriteLine(array[3][2]); // Exibe 9
```

# Referências

* [Arrays](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/)