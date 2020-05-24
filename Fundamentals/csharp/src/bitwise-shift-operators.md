# ⚙️ Operadores Bitwise e Shift

Antes de prosseguir, recomendo fortemente que leiam o seguinte artigo do [Jean Martins](https://github.com/jeanfmc).
[Sinal Magnitude: bit de sinal, complemento de 1 e complemento de 2](https://link.medium.com/z9f1mS1dI6)

## Explicação

Os seguintes operadores realizam operações *bitwise* ou *shift* em operandos de tipo [numéricos integrais](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/variables.md#1-tipos-num%C3%A9ricos-integrais) ou no tipo [char](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/variables.md#4-tipos-char):

| Nome | Expressão | Categoria |
| :--- | :---: | :---: |
**Complemento bitwise** | `~a` | Unário
**Left-Shift** | `a << 1` | Binário
**Right-Shift** | `a >> 1` | Binário
**AND lógico** | `a & b` | Binário
**OR lógico** | `a \| b` | Binário
**XOR lógico** | `a ^ b` | Binário

Estes operadores são definidos para operações com os tipos `int`, `uint`, `long`, `ulong`. Quando ambos os operandos
são de outros tipos (`sbyte`, `byte`, `short`, `ushort` ou `char`), seus valores são convertidos automaticamente para o tipo `int`.

## Operador de complemento bitwise (inversão de bits) `~`

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

## Operador de deslocamento à esquerda (left-shift) `<<`

O operador `<<` desloca todos os bits **n** casas para a esquerda, sendo **n** a [contagem de deslocamento com base em seu operando](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/bitwise-shift-operators.md#contagem-de-deslocamento-dos-operadores--e-).

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

## Operador de deslocamento à direita (right-shift) `>>`

O operador `>>` desloca todos os bits **n** casas para a esquerda, sendo **n** a [contagem de deslocamento com base em seu operando](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/bitwise-shift-operators.md#contagem-de-deslocamento-dos-operadores--e-).

Exemplos:
```C#
byte a = 0b_1000_0000_0000_0000_0000_0000_0000_0000;
Console.WriteLine(Convert.ToString(a, toBase: 2));
// 10000000000000000000000000000000 - 2147483648 em binário

a = a >> 1;
Console.WriteLine(Convert.ToString(a, toBase: 2));
//  1000000000000000000000000000000 - 1073741824 em binário

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

## Operador AND lógico `&`
O operador `&` computa o **AND** lógico **bit a bit** de seus operandos. Ou seja, para cada bit de cada operando, é realizada a operação `bit AND bit`.
```C#
uint a = 0b_1111_1000;
uint b = 0b_1001_1101;
uint c = a & b;

Console.WriteLine(Convert.ToString(c, toBase: 2));
// 10011000
```

## Operador OR lógico `|`
O operador `|` computa o **OR** lógico bit a bit de seus operandos. Ou seja, para cada bit de cada operando, é realizada a operação `bit | bit`.
```C#
uint a = 0b_1111_1000;
uint b = 0b_1001_1101;
uint c = a | b;

Console.WriteLine(Convert.ToString(c, toBase: 2));
// 11111101
```

## Operador XOR lógico `^`
O operador `^` computa o **XOR** lógico bit a bit de seus operandos. Ou seja, para cada bit de cada operando, é realizada a operação `bit ^ bit`.
```C#
uint a = 0b_1111_1000;
uint b = 0b_1001_1101;
uint c = a ^ b;

Console.WriteLine(Convert.ToString(c, toBase: 2));
// 01100101
```

## Atribuição composta

Para qualquer operador binário (representado aqui por `op`), uma expressão de atribuição composta no seguinte formato
```C#
x op= y;
```
é equivalente a
```C#
x = x op y;
```
exceto que x é avaliado somente uma vez.

Exemplos:
```C#
uint a = 0b_1111_1000;
a &= 0b_1001_1101;
Console.WriteLine($"{Convert.ToString(a, toBase: 2), 8}"); 
// Resultado: 10011000

a |= 0b_0011_0001;
Console.WriteLine($"{Convert.ToString(a, toBase: 2), 8}"); 
// Resultado: 10111001

a ^= 0b_1000_0000;
Console.WriteLine($"{Convert.ToString(a, toBase: 2), 8}"); 
// Resultado:   111001

a <<= 2;
Console.WriteLine($"{Convert.ToString(a, toBase: 2), 8}"); 
// Resultado: 11100100

a >>= 4;
Console.WriteLine($"{Convert.ToString(a, toBase: 2), 8}"); 
// Resultado:     1110
```

## Ordem de execução dos operadores

A lista a seguir ordena os operadores bitwise e shift, começando com os de prioridade mais alta até a mais baixa:
1. Operador de complemento bitwise `~`
2. Operadores de deslocamento (shift) `<<` e `>>`
3. Operador AND lógico `&`
4. Operador XOR lógico `^`
5. Operador OR lógico `|`

Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:
```C#
uint a = 0b_1101;
uint b = 0b_1001;
uint c = 0b_1010;

uint d1 = a | b & c;
Console.WriteLine($"{Convert.ToString(d1, toBase: 2), 4}");
// Resultado: 1101

uint d2 = (a | b) & c;
Console.WriteLine($"{Convert.ToString(d2, toBase: 2), 4}");
// Resultado: 1000
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

# Referências

* [Bitwise complement operator](https://docs.microsoft.com/en-us/dotnet/csharp/src/language-reference/language-specification/expressions#bitwise-complement-operator)
* [Shift operators](https://docs.microsoft.com/en-us/dotnet/csharp/src/language-reference/language-specification/expressions#shift-operators)
* [Logical operators](https://docs.microsoft.com/en-us/dotnet/csharp/src/language-reference/language-specification/expressions#logical-operators)
* [Compound assignment](https://docs.microsoft.com/en-us/dotnet/csharp/src/language-reference/language-specification/expressions#compound-assignment)
* [Numeric promotions](https://docs.microsoft.com/en-us/dotnet/csharp/src/language-reference/language-specification/expressions#numeric-promotions)