# Operadores de Igualdade

São os operadores que executam checam se seus operandos são iguais ou não:

* Operador de igualdade [==](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/equality-operators.md#operador-de-igualdade-)
* Operador de desigualdade [!=](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/equality-operators.md#operador-de-igualdade-)

## Operador de igualdade ==

O operador `==` retornará `true` se seus operandos forem iguais, caso contrário, `false`.

### Igualdade entre tipos de valor

Operandos dos [tipos internos](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-types#built-in-value-types) serão iguais se seus valores forem iguais:
```C#
int a = 3 + 3;
int b = 6;
Console.WriteLine(a == b);	// Resultado: True

char c1 = 'f';
char c2 = 'F';
Console.WriteLine(c1 == c2);	// Resultado: False
```

### Igualdade entre tipos de referência

Operandos do tipo de referência são iguais quando se referem ao mesmo objeto:
```C#
var a = new object();
var b = new object();
Console.WriteLine(a == b);	// Resultado: False

var c = a;
Console.WriteLine(a == c);	// Resultado: True
```

### Igualdade entre uma cadeia de caracteres (strings)

Operandos `string` serão iguais quando ambos forem `null` ou ambas instâncias tiverem exatamente os mesmos caracteres:
```C#
string s1 = "felipe";
string s2 = "FELIPE";
Console.WriteLine(s1 == s2);	// Resultado: False

string s3 = s2.ToLower();	// Como o nome sugere, troca todas as letras maiusculas por letras minusculas.
```

### Igualdade entre delegados

Dois operandos `delegate` são iguais quando ambos forem `null` ou se suas listas de invocação são do mesmo comprimento e tem entradas iguais em cada posição:
```C#
Action a = () => Console.WriteLine("HelloWorld");
Action b = () => Console.WriteLine("HelloWorld");

Console.WriteLine(a == b);		// Resultado: False
Console.WriteLine(a + b == a + b);	// Resultado: True
Console.WriteLine(a + b == b + a);	// Resultado: False
```

## Operador de desigualdade !=

O operador de desigualdade `!=` retornará `true` caso seus operandos sejam diferentes, caso contrário `true`. 

```C#
int a = 3;
int b = 4;
Console.WriteLine(a != b);		// Resultado: True

string s1 = "Hello";
string s2 = "Hello";
Console.WriteLine(s1 != s2);		// Resultado: False

object obj1 = new object();
object obj2 = new object();
Console.WriteLine(obj1 != obj2);	// Resultado: True
```

# Referências

* [System.IQuatable<T>](https://docs.microsoft.com/en-us/dotnet/api/system.iequatable-1?view=netcore-3.1)
* [Object.Equals](https://docs.microsoft.com/en-us/dotnet/api/system.object.equals?view=netcore-3.1)
* [Object.ReferenceEquals](https://docs.microsoft.com/en-us/dotnet/api/system.object.referenceequals?view=netcore-3.1)
* [Equality comparisons](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/equality-comparisons)
* [Comparison operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/comparison-operators)