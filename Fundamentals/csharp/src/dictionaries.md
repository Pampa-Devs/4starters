# 🔠 Dicionários
A coleção genérica [Dictionary<TKey, TValue>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=netcore-3.1) permite que você acesse elementos em uma coleção usando a chave de cada elemento.

## Adição de elementos
Cada adição ao dicionário constiste em um valor com a respectiva chave associada.
```C#
var games = new Dictionary<string, Game>();

var gta = new Game("gta", "Grand Theft Auto");
var starcraft = new Game("sc", "StarCraft");
var lol = new Game("lol", "League of Legends");
var dota = new Game("dota", "dEFENSE of the Ancients");


games.Add(gta.Acronym, gta);
games.Add(starcraft.Acronym, starcraft);
games.Add(lol.Acronym, lol);
games.Add(dota.Acronym, dota);
```

Você também pode adicionar novos elementos da seguinte forma:
```
games["aoe"] = new Game("aoe", "Age of Empires");
```

Caso você adicione um elemento que já existe, o dicionário irá lançar uma `Exception`.

## Acessando elementos por chave
Podemos utilizar a chave para acessar um elemento específico em um `Dictionary`. Caso a chave não exista o será lançada uma `Exception`.
```C#
string a = games["lol"];
string b = games["dota"];

Console.WriteLine(a.Name); // League of Legends
Console.WriteLine(b.Name); // Defense of the Ancients
```

Se o elemento que você está tentando acessar, não estiver no dicionário, o mesmo irá lançar uma `Exception`;

Podemos utilizar o método `TryGetValue` que retorna um `bool` informando se a chave existe ou não:
```C#
string name = "pubg";
Game game = null;

if(games.TryGetValue(name, out game))
{
    Console.WriteLine(game.Name + " exists!");
}
else
{
    Console.WriteLine(name + " does not exist!");
}
```

## Atualização de elemento específico
A chave definida para o seu valor em um `Dictionary` pode ser utilizada para alterar o seu valor.
```C#
var game = games["dota"];

game.Name = "Defense of the Ancients";
```

Sintaxe alternativa para o exemplo acima:
```C#
games["dota"].Name = "Defense of the Ancients";
```

## Verificando se um elemento existe
Utilizando o método `ContainsKey` do dicionário, podemos saber se um elemento já está no dicionário.
```C#
bool a = games.ContainsKey("gta");
bool b = games.ContainsKey("hots");

Console.WriteLine(a); // True
Console.WriteLine(b); // False
```

## Percorrendo os elementos de um dicionário
Assim como uma lista, pode ser utilizado um [iterador]() para percorrer os elementos de um dicionário.

Ao utilizar um iterador para enumerar os elementos do dicionário, os elementos são retornados como um objeto `KeyValuePair` que contém a **chave** e o **valor** do elemento.
```C#
foreach(KeyValuePair<string Element> kvp in games)
{
    Console.WriteLine($"{kvp.Key} - {kvp.Value}");
}
// Resultado:
// gta - Grand Theft Auto"
// sc - StarCraft
// lol - League of Legends
// dota - Defense of the Ancients
// aoe - Age of Empires
```

Para acessar somente os valores, utilize:
```C#
List<Game> elements = games.Values;
```

Para acessar somente as chaves, utilize:
```C#
List<string> keys = games.Keys;
```

## Removendo chave do dicionário
Utilizando o método `Remove` podemos remover a chave específicada do `Dictionary`.
```C#
games.Remove("lol");

bool exists = games.ContainsKey("lol");

Console.WriteLine(exists); // False
```

## Classe Game
Classe `Game` utilizada nos exemplos.
```C#
class Game
{
    public Game(string acronym, string name)
    {
        Acronym = acronym;
        Name = name;
    }
    public string Acronym { get; set; }
    public string Name { get; set; }
}
```

# Referências

* [Dictionary<TKey, TValue>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=netcore-3.1)