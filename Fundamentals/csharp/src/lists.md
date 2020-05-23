# Listas

Representa uma lista de objetos que podem ser acessados por índice. Também providencia métodos para pesquisar, classificar e manipular esses objetos.

## Listas simples

*Listas simples* são as listas que utilizam *tipos simples* como `int`, `float`, `string`, `char`, etc.

### Estrutura de uma lista
O exemplo abaixo mostra que temos uma coleção do tipo `T`.
```
List<T> name;
```

### Declaração de uma lista de `string`.
```C#
var companies = new List<string>();
```

### Adicionando elementos a lista companies
```C#
companies.Add("Google");
companies.Add("Microsoft");
companies.Add("Oracle");
companies.Add("Dell");
```

Sintaxe alternativa para o exemplo acima:
```C#
var companies = new List<string>() { "Google", "Microsoft", "Oracle", "Dell"}
```

### Acessando elementos da lista
Podemos acessar qualquer elemento da lista especificando o indice que queremos acessar usando a seguinte estrutura:
```
lista[indice]
```

Utilizando a estrutura acima, vamos acessar os membros previamente criados no nosso exemplo:
```C#
Console.WriteLine("O nome da empresa é: " + companies[0]);
// O Nome da empresa é Google

Console.WriteLine("O nome da empresa é: " + companies[3]);
// O Nome da empresa é Dell

foreach (string company in companies)
{
    Console.WriteLine(company);
}
// Google
// Microsoft
// Oracle
// Dell
```

### Removendo elementos da lista
Utilizando o método `Remove` conseguimos remover o elemento específicado da lista.
```C#
companies.Remove("Dell")
// Google, Microsoft, Oracle
```

Utilizando o método `RemoveAt` conseguimos remover o elemento do índice específicado da lista.
```C#
companies.RemoveAt(0);
// Microsoft, Oracle
```


# Referências

* [Collections](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections)
* [List<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1?view=netcore-3.1)