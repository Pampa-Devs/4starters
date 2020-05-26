# 🔷 "Tipo" var

Váriaveis que são declaradas dentro do bloco de código de um **método** podem ter um "tipo" implícito `var`.

No exemplo abaixo, ambas as váriaveis `a` e `b` são do tipo `int` e possuem um valor atribuido de 10.
```C#
var a = 10; // Tipagem implícita
int b = 10; // Tipagem explícita
```

Exemplo percorrendo uma lista:
```C# 
List<string> nomes = new List<string> { "Felipe", "Gabriel", "Luis", "Lucas" };

foreach(var nome in nomes) // Percorre a lista, um item de cada vez
{
    Console.WriteLine(nome); // Mostra o valor da propriedade nome
}
```

# Referências

* [var](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/var)