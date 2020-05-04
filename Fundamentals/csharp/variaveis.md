# Tipos e Váriaveis

##Tipos de Valor

### Tipos numéricos integrais

Como o nome já diz, os *tipos numéricos integrais* representam **números inteiros**. São **tipos simples** e todos suportam 
operadores aritméticos, Bitwise lógicos, de comparação e de igualdade.

alias | Intervalo | Tamanho | Tipo .NET
------- | ------- | ------- | -------
`sbyte` | -128 **até** 127 | Inteiro de 8 bits com sinal | [System.SByte](https://docs.microsoft.com/pt-br/dotnet/api/system.sbyte?view=netcore-3.1)
`byte` | 0 **até** 255 | Inteiro de 8 bits sem sinal | [System.Byte](https://docs.microsoft.com/pt-br/dotnet/api/system.byte?view=netcore-3.1)
`short` | -32.768 **até** 32.767 | Inteiro de 16 bits com sinal | [System.Int16](https://docs.microsoft.com/pt-br/dotnet/api/system.int16?view=netcore-3.1)
`ushort` | 0 **até** 65.535 | Inteiro de 16 bits sem sinal | [System.UInt16](https://docs.microsoft.com/pt-br/dotnet/api/system.uint16?view=netcore-3.1)
`int` | -2.147.483.648 **até** 2.147.483.647 | Inteiro assinado de 32 bits | [System.Int32](https://docs.microsoft.com/pt-br/dotnet/api/system.int32?view=netcore-3.1)
`uint` | 0 **até** 4.294.967.295 | Inteiro de 32 bits sem sinal | [	System.UInt32](https://docs.microsoft.com/pt-br/dotnet/api/system.uint32?view=netcore-3.1)
`long` | -9.223.372.036.854.775.808 **até** 9.223.372.036.854.775.807 | Inteiro assinado de 64 bits | [System.Int64](https://docs.microsoft.com/pt-br/dotnet/api/system.int64?view=netcore-3.1)
`ulong` | 0 **até** 18.446.744.073.709.551.615 | Inteiro de 64 bits sem sinal | [System.UInt64](https://docs.microsoft.com/pt-br/dotnet/api/system.uint64?view=netcore-3.1)

A coluna **Tipo** representa um *alias* a ser utilizado dentro do código. Por exemplo, as declarações a seguir representam o mesmo tipo:
```C#
int a = 123;
System.Int32 b = 123;
```

O valor padrão de cada tipo integral é `0`. Cada um dos tipos possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.

### Tipos numéricos de ponto flutuante

Os *tipos numéricos de ponto flutuante* representam números reais. São **tipos simples** e também suportam operadores aritméticos, bitwise lógicos], de comparação e de igualdade.

alias | Precisão | Tamanho | Tipo .NET
------- | ------- | ------- | -------
`float` | ~6 **a** 9 dígitos | 4 bytes | [System.Single](https://docs.microsoft.com/pt-br/dotnet/api/system.single?view=netcore-3.1)
`double` | ~15 **a** 17 dígitos | 8 bytes | [System.Double](https://docs.microsoft.com/pt-br/dotnet/api/system.double?view=netcore-3.1)
`decimal` | 28 **a** 29 dígitos | 16 bytes | [System.Decimal](https://docs.microsoft.com/pt-br/dotnet/api/system.decimal?view=netcore-3.1)


### Tipo Boolean

A `bool` é um tipo para [System.Boolean](https://docs.microsoft.com/pt-br/dotnet/api/system.boolean?view=netcore-3.1). Representa um
valor booleano que pode ser `true` ou `false` (verdadeiro ou falso).

Bastante utilizado para realizar operações lógicas do tipo booleano. É o resultado de comparação e igualdade dos operadores. No exemplo a seguir, o resultado será `A luz está ligada`:

```C#
bool luzLigada = true;

if (luzLigada == true)
{
    Console.WriteLine("A luz está ligada");
}
else
{
    Console.WriteLine("A luz está desligada");
}
```

O valor default de um bool é `false`.


##Tipos de Referência