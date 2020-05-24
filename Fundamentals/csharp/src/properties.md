# 🧬 Propriedades

Uma propriedade é um membro de uma 
[classe](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/value-types.md#tipo-de-estrutura-struct) 
ou [struct](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/value-types.md#tipo-de-estrutura-struct) 
que oferece um mecanismo flexível para ler, gravar e calcular o valor de um campo particular.

No exemplo abaixo, a palavra `nome` do tipo `string` é uma propriedade da classe `Pessoa`.
```C#
class Pessoa
{
    string nome { get; set; }
}
```

No exemplo a seguir iremos **ler**, **alterando** e **gravar** o valor da propriedade `nome`.
```C#
// Criação de uma classe 'Pessoa'
Pessoa p = new Pessoa();

// Atribuição do valor "lucas" a propriedade 'nome' da pessoa
p.nome = "Lucas";

// Lendo a propriedade 'nome' da pessoa
string a = p.nome;
Console.WriteLine(a); // Exibe "Lucas" no console

// Utilizando o 'nome' para calcular o valor da váriavel 'b'
// O novo valor de 'b' é "Felipe de Almeida"
string b = p.nome + " de Almeida";

// Gravando a váriavel 'b' em 'nome'
p.nome = b;
Console.WriteLine(p.nome); // Exibe "Felipe de Almeida" no console
```

# Referências

* [Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties)
