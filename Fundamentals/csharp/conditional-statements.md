# 🔀 Estruturas Condicionais

*Estruturas condicionais* executam um instrução de código caso uma condição booliana sejá atendida. Elas permitem que o desenvolvedor realize desde as mais simples as mais complexas verificações de código.

| Nome      | Exemplos |
| :---      | :---:    |
**if-else** | `if`, `else`, `else if`, `condition ? :`
**switch** | `switch`, `case`, `default`, `when`

## if-else

O `if` verifica qual instrução deve ser executada com base em um valor booliano. No exemplo abaixo, a váriavel `condition`, onde o resultado será **A condição é verdadeira**.
```C#
bool condition = true;

if (condition)
{
    Console.WriteLine("A condição é verdadeira");
}
else
{
    Console.WriteLine("A condição é falsa");
}
```

Ao utilizar o operador ternário `?:`, podemos escrever o mesmo código acima da seguinte forma:
```C#
bool condition = true;

Console.WriteLine(condition ? "A condição é verdadeira" : "A condição é falsa");
```

Também podemos utilizar o `if` em conjunto com o `else`, como podemos ver no exemplo abaixo:
```C#
int testScore = 72;

if (testScore < 20)
{
    Console.WriteLine("A nota da prova é F");
}
else if (testScore < 50)
{
    Console.WriteLine("A nota da prova é D");
}
else if (testScore < 75)
{
    Console.WriteLine("A nota da prova é C");
}
else if (testScore < 90)
{
    Console.WriteLine("A nota da prova é B");
}
else
{
    Console.WriteLine("A nota da prova é A");
}
```

## switch

O `switch` escolhe uma uníca instrução para ser executada de uma lista de candidatos caso a mesma corresponda a uma das opções providênciadas.
```C#
int number = 2;

switch(number)
{
    case 1:
        Console.WriteLine("Case 1");
        break;
    case 2:
        Console.WriteLine("Case 2");
        break;
    default:
        Console.WriteLine("Default case");
        break;
}

// O resultado que será mostrado será o seguinte:
// Case 1
```

A estrutura condicional `switch` geralmente é utilizada como uma alternativa para o [if-else]() quando uma única expressão tem mais de três resultados possíveis.
```C#
WeekDay day = WeekDay.Friday;

switch(devType)
{
    case WeekDay.Monday:
    case WeekDay.Tuesday:
    case WeekDay.Wednesday:
    case WeekDay.Thursday:
        Console.WriteLine("Dia de trabalhar");
        break;
    case WeekDay.Friday:
        Console.WriteLine("Dia de trabalhar, porém tem festa depois do expediente");
        break;
    case WeekDay.Saturday:
    case WeekDay.Sunday:
        Console.WriteLine("Folga finalmente");
        break;
    default:
        Console.WriteLine("O dia informado não é um dia da semana");
        break;
}

// O resultado que será mostrado será o seguinte:
// "Dia de trabalhar, porém tem festa depois do expediente"
```

Também podemos verificar **tipos** usando o `switch` e propriedades destes tipos usando a palavra-chave `when`;
```C#
Person person = new Developer("Felipe", "dotnet");

switch (person)
{
    case Astronaut a:
        Console.WriteLine($"Um astronauta chamado {a.Name}");
        break;
    case Cop c:
        Console.WriteLine($"Um policial chamado {c.Name}");
        break;
    case Cop c when c.HasGun == true:
        Console.WriteLine($"Um policial armado chamado {c.Name}");
        break;
    case Developer d:
        Console.WriteLine($"Um desenvolvedor chamado {d.Name} focado em {d.ProgrammingLanguage}");
        break;
    case Developer d when d.Name == "Felipe":
        Console.WriteLine($"Felipe: O desenvolvedor mais motivado que você vai conhecer!");
        break;
    case null:
        Console.WriteLine($"A váriavel {nameof(person)} é nula");
        break;
    default:
        Console.WriteLine($"A váriavel {nameof(person)} não é do tipo Person");
        break;
}

// O resultado que será mostrado será o seguinte:
// "Felipe: O desenvolvedor mais motivado que você vai conhecer!"
```

# Referências
* [C# reference](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/)
* [C# programming guide](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/)
* [C# Keywords](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/)
* [?: operator](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator)
* [switch](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/switch)