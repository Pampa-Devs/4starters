# 🤝 Classes parciais

No **C#** é possível segregar a definição de [class](), [struct](), uma [interface] e até um método em dois ou mais arquivos. 
Cada um desses arquivos contem o seu próprio bloco de código e todas as partes são combinadas quando o aplicativo é compilado.

## Classes parciais

Existem vários motivos para separar uma uma `class` em arquivos diferentes, aqui alguns deles:
* Adicionar novos comportamentos sem alterar o arquivo original
* Separar uma classe com várias interfaces em diferentes arquivos
* Vários programadores podem trabalhar ao mesmo tempo em uma mesma classe, porém em arquivos diferentes

Para utilizar uma classe parcial basta adicionar a palavra-chave `partial` antes de `class`.

No exemplo abaixo temos a classe parcial `Product`
```C#
public partial class Product
{
    public string GetPrice()
    {
    }
}

public partial class Product
{
    public string GetOwner()
    {
    }
}
```

É o equivalente à:
```C#
public partial class Product
{
    public string GetPrice()
    {
    }
    
    public string GetOwner()
    {
    }
}
```



O mesmo ocorre com heranças, interfaces e atributos:
```C#
public partial class Earth : Planet, IRotate {}
public partial class Earth : IRevolve {}
```

O resultado será o seguinte:
```C#
class Earth : Planet, IRotate, IRevolve { }
```

## Métodos parciais

Classes e structs também podem conter métodos parciais, porém esses tem algumas restrições:
* Devem retornar `void`
* Não podem utilizar o parâmetro `out`
* Por serem implicitamente `private` não podem ser `virtual`

# Referências

* [partial-classes-and-structs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)