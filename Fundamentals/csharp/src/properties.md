# 🧬 Propriedades

Uma propriedade é um membro de uma 
[classe](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/value-types.md#tipo-de-estrutura-struct) 
ou [struct](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/value-types.md#tipo-de-estrutura-struct) 
que oferece um mecanismo flexível para ler, gravar e calcular o valor de um campo particular.

Porém, na realidade, as tarefas de ler, gravar e calcular são métodos realmente especiais chamados de **acessadores**. Elas permitem que os dados sejam acessados facilmente
e ainda ajudam a promover a segurança e flexibilidade dos métodos. 

Existem dois tipos de acessadores dentro de uma propriedade:
* Leitura `get`
* Gravação `set`

## Características das propriedades
* As propriedades podem ser de *leitura*/*gravação* (possui `get` e `set`), *somente leitura* (possui somente `get`) ou *somente gravação* (possui somente `set`).
* As propriedades permitem uma forma simples de obter e definir valores de uma classe, enquanto oculta o código que realiza essa tarefa.
* A palavra-chave `value` é usada para definir o valor que esta sendo atríbuido pelo acessador `set`.
* Propriedades que não exigem nenhum código de acessador **personalizado** podem ser implementadas como [propriedades autoimplementadas]().

## Propriedades com campos de suporte
No exemplo abaixo, temos duas váriaveis, `firstName` e `lastName` do tipo `string`, e uma propriedade chamada `Name` também do tipo `string`.
```C#
class Pessoa
{
    public string firstName;
    public string lastName;
    
    public string Name
    {
        get
        {
            return firstName + " " + lastName;
        }
        set
        {
            var names = value.Split(" ");
            
            firstName = names[0];
            lastName = names[1];
        }
    }
}
```
Note que o acessador `get` retorna na realidade as váriaveis concatenadas `firstName` e `lastName`.Já o acessador `set` recebe uma `string` e então a separa
pela quantidade de espaços com a função `Split`, com o nome completo dividido ele salva cada parte em sua respectiva váriavel.

Outra sintaxe para escrever o código acima:
```C#
class Pessoa
{
    public string firstName;
    public string lastName;
    
    public string Name
    {
        get => return firstName + " " + lastName;
        set => return ParseName(value);
    }
    
    private string ParseName(string name)
    {
        var name = value.Split(" ");
            
        firstName = name[0];
        lastName = name[1];
    }
}
```


No exemplo a seguir iremos **ler**, **alter** e **gravar** o valor da propriedade `nome`.
```C#
// Criação de uma classe 'Pessoa'
Pessoa p = new Pessoa();

// Gravando o valor "Felipe Almeida" na propriedade 'Name' da pessoa
p.Name = "Felipe Almeida";

// Lendo a propriedade 'Name' da pessoa
Console.WriteLine(p.Name); // Exibe "Felipe Almeida" no console

// Lendo o valor das váriaveis 'firstName' e 'lastName' da pessoa
Console.WriteLine(p.firstName); // Exibe "Almeida" no console
Console.WriteLine(p.firstName); // Exibe "Almeida" no console
```

## Propriedades autoimplementadas
Em alguns casos, os acessadores `get` e `set` da propriedade apenas atribuem ou leem um valor de um campo sem incluir nenhuma lógica adicional.
Usando propriedades autoimplementadas, você pode simplificar o código enquanto o compilador C# fornece um campo de forma transparente.

```C#
class Pessoa
{
    public string FirstName { get; set;}
    public string LastName { get; set; }
}
```

# Referências

* [Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties)
