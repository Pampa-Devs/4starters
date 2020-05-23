# ⚖️ Operadores de Comparação

São os operandos que executam operações relacionais. O C# da suporte a operações relacionais a **todos os tipos númericos** [integral]() e [de ponto flutuante]()

| Nome | Expressão | Categoria |
| :--- | :---: | :---: |
**Menor** | `a < b` | Binário
**Maior** | `a > b` |  Binário
**Menor ou igual** | `a <= b` | Binário
**Maior ou igual** |  `a >= b` | Binário

O tipo [Char]() também suporta os operadores de comparação. Porém é utilizado o código do caractere.

## Operador menor que <

O operador `<` retornará `true` se o operando da esquerda for menor que o operando à direita, caso contrário, `false`:
```C#
Console.WriteLine(7.0 < 5.0);	// Resultado: False
Console.WriteLine(10.2 < 15.5);	// Resultado: True
Console.WriteLine(5.0 < 5.0);	// Resultado: True
```

## Operador maior que >

O operador `>` retornará `true` se o operando da esquerda for maior que o operando à direita, caso contrário, `false`:
```C#
Console.WriteLine(7.0 > 5.0);	// Resultado: True
Console.WriteLine(10.2 > 15.5);	// Resultado: False
Console.WriteLine(5.0 > 5.0);	// Resultado: True
```

## Operador menor ou igual <=

O operador `<=` retornará `true` se o operando da esquerda for menor ou igual ao operando à direita, caso contrário, `false`:
```C#
Console.WriteLine(7.0 <= 5.0);	// Resultado: False
Console.WriteLine(10.2 <= 15.5);	// Resultado: True
Console.WriteLine(5.0 <= 5.0);	// Resultado: True
```

## Operador menor ou igual >=

O operador `>=` retornará `true` se o operando da esquerda for maior ou igual ao operando à direita, caso contrário, `false`:
```C#
Console.WriteLine(7.0 >= 5.0);	// Resultado: Ture
Console.WriteLine(10.2 <= 15.5);	// Resultado: False
Console.WriteLine(5.0 >= 5.0);	// Resultado: True
```

# Referências

* [C# reference](https://docs.microsoft.com/en-us/dotnet/csharp/src/language-reference/)
* [C# operators](https://docs.microsoft.com/en-us/dotnet/csharp/src/language-reference/operators/)
* [IComparable<T>](https://docs.microsoft.com/en-us/dotnet/api/system.icomparable-1?view=netcore-3.1)