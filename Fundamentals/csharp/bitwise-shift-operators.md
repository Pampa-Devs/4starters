# Operadores Bitwise e Shift

Os seguintes operadores realizam operações *bitwise* ou *shift* em operandos de tipo [numéricos integrais](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/variables.md#1-tipos-num%C3%A9ricos-integrais) ou no tipo [char](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/variables.md#4-tipos-char):

* Operador unário [~ inversão de bits]()
* Operadores de deslocamento binário [<< (left-shift)]() e [>> (right-shift)]()
* Operadores binários [& (AND lógico)](), [OR lógico]() e [XOR lógico]

Estes operadores são definidos para operações com os tipos `int`, `uint`, `long`, `ulong`. Quando ambos os operandos
são de outros tipos (`sbyte`, `byte`, `short`, `ushort` ou `char`), seus valores são convertidos automaticamente para o tipo `int`.

## Operador bitwise de inversão de bits ~

O operador `~` inverte os bits de seu operando:

```C#
uint a = 0b_1111_0000_1111_0000_1111_0000_0110_1001
Console.WriteLine(Convert.ToString(a, toBase: 2));

uint b = ~a;
Console.WriteLine(Convert.ToString(b, toBase: 2));

// Resultado:
// 11110000111100001111000001101001
// 00001111000011110000111110010110
```

## Operador de deslocamento à esquerda (left-shift) <<

O operador `<<` desloca todos os bits **n** casas para a esquerda, sendo **n** a [contagem de deslocamento com base em seu operando]().

Exemplos:
```C#
byte a = 0b_0000_0000_0000_0000_0000_0000_0000_0001;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 00000000000000000000000000000001 - 1 em binário

a = a << 1;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 00000000000000000000000000000010 - 2 em binário

a = a << 1;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 00000000000000000000000000000100 - 4 em binário

a = a << 2;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 00000000000000000000000000010000 - 16 em binário

a = a << 4;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 00000000000000000000001000000000 - 512 em binário
```

## Operador de deslocamento à direita (right-shift) >>

O operador `>>` desloca todos os bits **n** casas para a esquerda, sendo **n** a [contagem de deslocamento com base em seu operando]().

Exemplos:
```C#
byte a = 0b_1000_0000_0000_0000_0000_0000_0000_0000;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 10000000000000000000000000000000 - 2147483648 em binário

a = a >> 1;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 01000000000000000000000000000000 - 1073741824 em binário

a = a >> 1;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 00100000000000000000000000000000 - 536870912 em binário

a = a >> 21;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 00000000000000000000000100000000 - 256 em binário

a = a >> 4;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 0000000000000000000000000010000 - 16 em binário
```

## Contagem de deslocamento dos operadores << e >>

Observe o seguinte valor binário:
```
00000000000000000000000000000001 - 1 em binário
```
Ele tem exatamente **32** caracteres, ou seja, é o tamanho em binário de um tipo inteiro de 32 bits (`int` ou `System.Int32`).

Vamos deslocar este binário **33** casas para esquerda, um valor maior que o suportado por um `int`:
```
00000000000000000000000000000001 << 33
```
O resultado será o seguinte:
```
00000000000000000000000000000001
```

O valor de deslocamento **33**, foi convertido para o tamanho de deslocamento **1** para não exceder o tamanho de um `int`.

A explicação técnica para isso é que para as expressões `x << operando` e `x >> operando`, a contagem real de deslocamento é calculada com base no tipo de `x` da seguinte maneira:
* Se o tipo de `x` for `int` ou `uint`, o valor do deslocamento é definido pelos *cinco* bits de baixa ordem do operando à direita. Ou seja, a contagem de deslocamentos é calculada a partir de `operando & 0x1F` (ou `operando & 0b_1_1111`).
* Se o tipo de `x` for `long` ou `ulong`, o valor do deslocamento é definido pelos *seis* bits de baixa ordem do operando à direita. Ou seja, a contagem de deslocamentos é calculada a partir de `operando & 0x3F` (ou `operando & 0b_11_1111`).

Segue alguns exemplos:
```
// Entrada
00000000000000000000000000000001 << 34
// Saída
00000000000000000000000000000010

// Entrada
00000000000000000000000000000001 << 35
// Saída
00000000000000000000000000000100

// Entrada
00000000000000000000000000000001 << 65
// Saída
00000000000000000000000000000001
```
