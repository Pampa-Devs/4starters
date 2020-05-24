# 🔢 Listas
Representa uma lista de objetos que podem ser acessados por índice. Também providencia métodos para pesquisar, classificar e manipular esses objetos.

## Estrutura de uma lista
O exemplo abaixo mostra que temos uma coleção do tipo `T`.
```
List<T> name;
```
Exemplo com diferentes tipos:
```C#
List<int> listInt;
List<float> listFloat;
List<string> listString;
List<object> listObject;
```

## Declaração de uma lista
```C#
var companies = new List<string>();
```

## Adicionando elementos a lista
```C#
companies.Add("Google");
companies.Add("Microsoft");
companies.Add("Oracle");
companies.Add("Dell");
```

Sintaxe alternativa para o exemplo acima:
```C#
var companies = new List<string>() { "Google", "Microsoft", "Oracle", "Dell"};
```

## Tamanho da lista
O método `Count` da lista retorna o número de elementos que a mesma contém.
```C#
var companies = new List<string>() { "Google", "Microsoft", "Oracle", "Dell"};

Console.WriteLine(companies.Count);
// 4
```

## Acessando elementos por índice
Também podemos acessar qualquer elemento da lista especificando o indice que queremos acessar usando a estrutura `lista[índice]`.
```C#
var companies = new List<string>() { "Google", "Microsoft", "Oracle", "Dell"};

string a = companies[0];
Console.WriteLine(a);
// Google

string b = companies[3];
Console.WriteLine(b);
// Dell
```

## Removendo elementos da lista
Utilizando o método `Remove` conseguimos remover o elemento específicado da lista.
```C#
var companies = new List<string>() { "Google", "Microsoft", "Oracle", "Dell"};

companies.Remove("Dell")
// Google, Microsoft, Oracle
```

Utilizando o método `RemoveAt` conseguimos remover o elemento do índice específicado da lista.
```C#
var companies = new List<string>() { "Google", "Microsoft", "Oracle", "Dell"};

companies.RemoveAt(0);
// Microsoft, Oracle, Dell
```

## Percorrendo cada elemento da lista
Podemos utilizar um [iterador]() para percorrer os elementos de uma coleção. Um iterador utiliza a instrução **yield return** para retornar um elemento da coleção por vez.
```C#
foreach (string company in companies)
{
    Console.WriteLine(company);
}
// Google
// Microsoft
// Oracle
// Dell
```

A estrura de repetição `for` também pode ser utilizada para percorrer os membros de uma lista.
```C#
for (int i = 0; i < companies.Count; i ++)
{
    Console.WriteLine(companies[i]);
}
```

# Referências

* [Collections](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections)
* [List<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1?view=netcore-3.1)