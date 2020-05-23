# ⁉️ Operadores lógicos boolianos

Os operadores que iremos apresentar neste artigo executam operações lógicas e de comparação com operandos [bool](https://devblogs.microsoft.com/aspnet/blazor-webassembly-3-2-0-now-available/?fbclid=IwAR0brw10DyJrB4RhHmu_HwIGVIhloqUe-wdsHhQx9pNuKw4idkHgt4NPxnE)

* Operador unário [! (negação lógica)](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/logical-comparison-operators.md#operador-de-nega%C3%A7%C3%A3o-l%C3%B3gica-)
* Operadores Binários [& (AND lógico)](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/logical-comparison-operators.md#operador-and-l%C3%B3gico), [| (OR lógico)](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/logical-comparison-operators.md#operador-or-l%C3%B3gico-condicional) e [^ (XOR lógico)](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/logical-comparison-operators.md#operador-or-l%C3%B3gico-condicional). Esses operadores **sempre** avaliam os dois operandos.
* Operadores Binários [&& (AND lógico condicional)](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/logical-comparison-operators.md#operador-or-l%C3%B3gico-condicional) e [|| (OR lógico condicional)](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/logical-comparison-operators.md#operador-or-l%C3%B3gico-condicional). Esses operadores avaliam o operando à direita **somente se necessário**.

| Nome | Expressão | Categoria |
| :--- | :---: | :---: |
**Negação Lógica !** | `!condition` | Unário
**AND Lógico &** | `a & b` | Binário
**AND Lógico Condicional &&** | `a && b` | Binário
**OR Lógico |** | `a | b` | Binário
**OR Lógico Condicional ||** | `a || b` | Binário
**XOR Lógico ^** | `a ^ b` | Binário

## Operador de negação lógica !

O sufixo unário `!` computa a negação lógica de seu operando. Ou seja, se o valor do operando for `true`, então o resultado será `false`.

```C#
bool IsComplete = true;

Console.WriteLine(!IsComplete); 	// Resultado: False
Console.WriteLine(!false);		// Resultado: True
```

## Operador AND lógico &

O operador `&` computa o **AND** lógico de seus operandos. O resultado de `x & y` será `true` **se ambos** `x` e `y` forem `true`. Caso contrário, o resultado será `false`.

O operador `&` verifica **os dois operandos** mesmo se o operador da esquerda for avaliado como `false`.

Confira o exemplo a seguir:

```C#
bool SecondOperand()
{
    Console.WriteLine("Segundo operando avaliado");
    return true;
}

bool a = false & SecondOperand();
Console.WriteLine(a);
// Resultado: false
// Ambos os operandos 'false' e 'SecondOperand()' são avaliados.

bool b = true & SecondOperand();
// Resultado: true
// Ambos os operandos 'true' e 'SecondOperand()' são avaliados.
```

## Operador AND lógico condicional &&

O operador `&&`, assim como o operador `&`, computa o **AND** lógico de seus operandos. O resultado de `x & y` será `true` **se ambos** `x` e `y` forem `true`. Caso contrário, o resultado será `false`.

O operador `&&`, diferentemente do `&`, irá computar todos os operandos **somente se os mesmos forem** `true`. Caso `x` seja `false`, `y` não irá ser computado.

Confira o exemplo a seguir:
```C#
bool SecondOperand()
{
    Console.WriteLine("Segundo operando avaliado");
    return true;
}

bool a = false && SecondOperand();
Console.WriteLine(a);
// Resultado: false
// Somente o operandos 'false' é avaliado.

bool b = true && SecondOperand();
// Resultado: true
// Ambos os operandos 'true' e 'SecondOperand()' são avaliados.
```

## Operador OR lógico |

O operador `|` computa o **OR** lógico de seus operandos. Ou seja, o resultado de `x | y` será `true` **se qualquer um dos operandos**, `x` ou `y`, for `true`. Caso ambos `x` e `y` sejam `false`, o resultado será `false`.

O operador `|` verifica **os dois operandos** mesmo se o operador da esquerda for avaliado como `true`.

Exemplo operador `|`:
```C#
bool SecondOperand()
{
    Console.WriteLine("Segundo operando avaliado");
    return true;
}

bool a = false | SecondOperand();
Console.WriteLine(a);
// Resultado: true
// Ambos os operandos 'false' e 'SecondOperand()' são avaliados.

bool b = true | SecondOperand();
// Resultado: true
// Ambos os operandos 'true' e 'SecondOperand()' são avaliados.
```

## Operador OR lógico condicional ||

O operador `||`, assim como o operador `|`, computa o **OR** lógico de seus operandos. Ou seja, o resultado de `x || y` será `true` **se qualquer um dos operandos**, `x` ou `y`, for `true`. Caso ambos `x` e `y` sejam `false`, o resultado será `false`.

O operador `||`, diferentemente do `|`, **irá computar primeiro** o `x`, caso este seja `true` o `y` não será computado.

Exemplo operador `||`:
```C#
bool SecondOperand()
{
    Console.WriteLine("Segundo operando avaliado");
    return true;
}

bool a = false || SecondOperand();
Console.WriteLine(a);
// Resultado: true
// Ambos os operandos 'false' e 'SecondOperand()' são avaliados.

bool b = true || SecondOperand();
// Resultado: true
// Somente o operando 'true' é computado.
```

## Operador XOR lógico ^

O operador `^` computa o **XOR** lógico de seus operandos. Ou seja, o resultado de `x ^ y` será `true` se `x` for `true` e `y`, for `false`, ou `x` for `false` e `y` for `true`.

Exemplo:
```C#
Console.WriteLine(true ^ true);    // Resultado: False
Console.WriteLine(true ^ false);   // Resultado: True
Console.WriteLine(false ^ true);   // Resultado: True
Console.WriteLine(false ^ false);  // Resultado: False
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
bool test = true;
test &= false;
Console.WriteLine(test);  // Resultado: False

test |= true;
Console.WriteLine(test);  // Resultado: True

test ^= false;
Console.WriteLine(test);  // Resultado: True
```

## Ordem de execução dos operadores

A lista a seguir ordena os operadores lógicos, começando com os de prioridade mais alta até a mais baixa:
1. Operador de negação lógico `!`
2. Operador AND lógico `&`
3. Operador XOR exclusivo lógico `^`
4. Operador OR lógico `|`
5. Operador AND lógico condicional `&&`
6. Operador OR lógico condicional `||`

Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:

```C#
Console.WriteLine(true | true & false);   // Resultado: True
Console.WriteLine((true | true) & false); // Resultado: False

bool Operand(string name, bool value)
{
    Console.WriteLine($"Operador {name} é avaliado.");
    return value;
}

var byDefaultPrecedence = Operand("A", true) || Operand("B", true) && Operand("C", false);
Console.WriteLine(byDefaultPrecedence);
// Resultado:
// Operand A is evaluated.
// True

var changedOrder = (Operand("A", true) || Operand("B", true)) && Operand("C", false);
Console.WriteLine(changedOrder);
// Resultado:
// Operador A é avaliado.
// Operand C é avaliado.
// False
```

# Referências

* [Logical negation operator](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/expressions#logical-negation-operator)
* [Logical operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/expressions#logical-operators)
* [Conditional logical operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/expressions#conditional-logical-operators)
* [Compound assignment](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/expressions#compound-assignment)