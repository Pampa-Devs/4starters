# Operadores Aritméticos

São os operadores que executam operações aritméticas utilizando-se de tipos númericos:

* Operadores unários [++ (incrementar)](), [-- (decrementar)](), [+ (soma)]() e [- subtração]()
* Operadores binário [\* (multiplicação)](/ (divisão)), [% (resto)](), [+ (adição)](), [+ (subtração)]()

## Operadores de incremento ++ e decremento --

O operador de incremento unário `++` incrementa, e o operador `--` decrementa o valor de uma váriavel de tipo numérico em 1.

Há duas formas de suporte para os operador `++` e `--`: O operador sufixo `x++` e `x--`, e 
o operador prefiro , `++x` e `--x`.

### Operador sufixo
O resultado de `numero++` é o valor de `numero` *antes* da operação ser realizada, como mostra o exemplo a seguir:
```C#
int numero = 5;

Console.WriteLine(numero);			 // Resultado: 5
Console.WriteLine(numero++);			 // Resultado: 5
Console.WriteLine(numero);			 // Resultado: 6
```

O resultado de `numero--` é o valor de `numero` *antes* da operação ser realizada, como mostra o exemplo a seguir:
```C#
int numero = 5;

Console.WriteLine(numero);			 // Resultado: 5
Console.WriteLine(numero--);			 // Resultado: 5
Console.WriteLine(numero);			 // Resultado: 4
```

### Operador prefixo
O resultado de `++numero` é o valor de `numero` *após* a operação ser realizada, como mostra o exemplo a seguir:

```C#
int numero = 5;

Console.WriteLine(numero);			 // Resultado: 5
Console.WriteLine(++numero);			 // Resultado: 6
Console.WriteLine(numero);			 // Resultado: 6
```

O resultado de `--numero` é o valor de `numero` *após* a operação ser realizada, como mostra o exemplo a seguir:

```C#
int numero = 5;

Console.WriteLine(numero);			 // Resultado: 5
Console.WriteLine(--numero);			 // Resultado: 4
Console.WriteLine(numero);			 // Resultado: 4
```

## Operadores unários de adição e subtração

O operador unário `+` retorna o próprio valor da váriavel. O operador unário `-` retorna o próprio valor multiplicado por -1.
```C#
Console.WriteLine(+10);			 // Resultado: 10
Console.WriteLine(-10);			 // Resultado: -4
Console.WriteLine(-(-10));			 // Resultado: 10

uint a = 20;
var b = -a;

Console.WriteLine(b);			// Resultado: -20
Console.WriteLine(b.GetType());			 // Resultado: System.Int64
```

## Operador de multiplicação *

O operador de multiplicação `*` calcula o produto dos operandos:
```C#
Console.WriteLine(2 * 2);			// Resultado: 4
Console.WriteLine(0.5 * 2);			// Resultado: 1
Console.WriteLine(0.5m * 25.5);			// Resultado: 12.75
```

## Operador de divisão /

O operador de divisão `/` divide o operando à esquerda pelo da direita.

### Divisão de inteiros
O resultado do operador `/` é um tipo inteiro e igual ao quociente dos dois operandos **arredondados para zero**:
```C#
Console.WriteLine(10 / 2);			// Resultado: 5
Console.WriteLine(-2 / 10);			// Resultado: 0
Console.WriteLine(10 / -2);			// Resultado: -5
Console.WriteLine(-2 / -10);			// Resultado: 0
```

Para obter um resultado de ponto flutuante ao dividir dois operandos inteiros, use o tipo `float`, `double` ou `decimal`.
```C#
Console.WriteLine((double)-2 / 10);			// Resultado: -0.2
```

### Divisão de números de ponto flutuante
Para os tipos `float`, `double` e `decimal`, o resultado do operador `/` é o quociente dos dois operandos:
```C#
Console.WriteLine(16.8f / 4.1f);   // Resultado: 4.097561
Console.WriteLine(16.8d / 4.1d);   // Resultado: 4.09756097560976
Console.WriteLine(16.8m / 4.1m);   // Resultado: 4.0975609756097560975609756098
```

### Operador de resto %
O operador de resto `%` calcula o resto após dividir o operando á esquerda pelo da direita.
```C#
Console.WriteLine(5 % 4);			// Resultado: 1
Console.WriteLine(5 % -4);			// Resultado: 1
Console.WriteLine(-5 % 4);			// Resultado: -1
Console.WriteLine(-5 % -4);			// Resultado: -1
```

### Operador de adição +
O operador `+` calcula a soma dos operandos:
```C#
Console.WriteLine(10 + 10);			// Resultado: 20
Console.WriteLine(10 + 10.5);			// Resultado: 20.5
Console.WriteLine(8.2m + 4.2m);			// Resultado: 12.4
```

### Operador de subtração -
O operador `-` calcula a subtração dos operandos:
```C#
Console.WriteLine(10 - 10);			// Resultado: 0
Console.WriteLine(10 - 10.5);			// Resultado: -0.5
Console.WriteLine(8.2m - 4.2m);			// Resultado: 4
```

### Atribuição composta

Para operador binário **op**, uma expressão de atribuição
```
x op= y;
```
é equivalente
```
x = x op y;
```

O exemplo a seguir demonstra o uso de atribuição composta com operadores aritiméticos:
```C#
int a = 13;
a += 7;
Console.WriteLine(a);			// Resultado: 20

a -= 5;
Console.WriteLine(a);			// Resultado: 15

a *= 2;
Console.WriteLine(a);			// Resultado: 30

a /= 6;
Console.WriteLine(a);			// Resultado: 5

a %= 3;
Console.WriteLine(a);			// Resultado: 2
```