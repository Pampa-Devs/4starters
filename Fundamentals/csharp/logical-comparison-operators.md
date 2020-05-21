# Operadores lógicos boolianos

Os operadores que iremos apresentar neste artigo executam operações lógicas e de comparação com operandos [bool](https://devblogs.microsoft.com/aspnet/blazor-webassembly-3-2-0-now-available/?fbclid=IwAR0brw10DyJrB4RhHmu_HwIGVIhloqUe-wdsHhQx9pNuKw4idkHgt4NPxnE)

* Operador unário [! (negação lógica)]()
* Operadores Binários [& ('E' lógico)](), [| ('OU' lógico)]() e [^ ('OU' exclusivo lógico)](). Esses operadores **sempre** avaliam os dois operandos.
* Operadores Binários [&& ('E' lógico condicional)]() e [|| ('OU' lógico condicional)](). Esses operadores avaliam o operando à direita **somente se necessário**.

Os operadores `&`, `|` e `^` realizam operações lógicas bitwise. Para mais informações, olhe o artigo [Operadores Bitwise e Shift]().

## Operador de negação lógica !

O sufixo unário `!` computa a negação lógica de seu operando. Ou seja, se o valor do operando for `true`, então o resultado será `false`.

```C#
bool IsComplete = true;

Console.WriteLine(!IsComplete); 	// Resultado: False
Console.WriteLine(!false);			// Resultado: True
```

## Operador E lógico

O operador `&` computa o **E** lógico de seus operandos. O resultado de `x & y` será `true` se ambos `x` e `y` forem `true`. Caso contrário, o resultado será `false`.

O operador `&` verifica **os dois operandos** mesmo se o operador da esquerda for avaliado como `false`.

Confira o exemplo a seguir:

```C#
bool SecondOperator()
{
    Console.WriteLine("Segundo operador avaliado");
    return true;
}

bool a = false & SecondOperator();
Console.WriteLine(a);
// Resultado: false
// Ambos os operadores 'false' e 'SecondOperador()' são avaliados.

bool b = true & SecondOperador();
// Resultado: true
// Ambos os operadores 'true' e 'SecondOperador()' são avaliados.
```