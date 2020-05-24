# 🚦 Modificadores de Acesso

*Modificadores de acesso* são palavras-chaves que garantem níveis de acessos aos nossos atributos, métodos e classes.

O nível de acessibilidade controla se eles podem ser usados a partir de outro código em qualquer parte de seu projeto. 
Utilize os seguintes modificadores para específicar a acessibilidade de um tipo ou membro quando você declara-lo:

| Modificador | Descrição |
| :---: | :--- | 
| **public** | O tipo ou membro pode ser acessado por qualquer outro código |
| **private** | O tipo ou membro só pode ser acessado dentro dentro de sua `class` |
| **protected** | O tipo ou membro só pode ser acessado dentro dentro de sua `class`, ou em uma `class` derivada de sua `class` |
| **internal** | O tipo ou membro pode ser acessado por qualquer outro código dentro de um mesmo projeto |
| **internal protected** | O tipo ou membro pode ser acessado por qualquer outro código dentro de um mesmo projeto, ou em uma `class` derivada de sua `class` |
| **private protected** | O tipo ou membro só pode ser acessado dentro dentro de sua `class`, por código dentro de sua `class` ou em um tipo derivado de sua `class` |

## Modificador `public`

A palavra-chave `public` é um modificador de acesso para tipos e membros de tipo. 
Acesso público é o nível de acesso **mais permissivo**. Não existe nenhuma restrição quanto a acesso a membros públicos:

```C#
class Coord
{
    public int x;
    public int y;
}

class Program
{
    static void Main()
    {
        var coord = new Coord();
        
        // Acesso permitido aos membros x e y da classe Coord
        coord.x = 10;
        coord.y = 15;
        Console.WriteLine($"x = {coord.x}, y = {coord.y}"); // Resultado: x = 10, y = 15
    }
}
```

## Modificador `private`
A palavra-chave `private` é um modificador de acesso para tipos e membros de tipo. 
Acesso privado é o nível de acesso **menos permissivo**. Membros privados são acessíveis somente dentro do corpo de sua classe ou do struct em que são declarados:

```C#
class Coord
{
    private int x;
    private int y;
    
    public string GetCoordX()
    {
        return x;
    }
    
    public string Y
    {
        get
        {
            return y;
        }
    }
}

class Program
{
    static void Main()
    {
        var coord = new Coord();
        
        // Os membros x e y da classe Coord são inacessíveis, 
        // eles não podem ser acessados da forma abaixo:
        //coord.x = 10;
        //coord.y = 15;
        
        // Aqui, 'x' é indiretamente acessado por um método
        int x = coord.GetX();
        
        // Aqui 'y' é indiretamente acessado por uma propriedade
        int y = coord.Y;
    }
}
```

## Modificador `protected`
A palavra-chave `protected` é um modificador de acesso para tipos e membros de tipo.
Um membro protegido **é acessível dentro de sua classe e por instâncias da classe derivada**.

```C#
class Person
{
    protected string name = "Felipe";
}

class Student : Person
{
    public string GetName()
    {
        // É ok acessar a propriedade 'name' pois Student deriva de Person.
        return name;
    }
}

class Program
{
    static void Main()
    {
        var person = new Person();
        var student = new Student();
        
        
        
        // O membro name das classe Person e Student são inacessíveis, 
        // eles não podem ser acessados da forma abaixo:
        //person.name = "Lucas";
        //student.name = "Victor";
    }
}
```

## Modificador `internal`
A palavra-chave `internal` é um modificador de acesso para tipos e membros de tipo.
Tipos ou membros internos **são acessíveis somente em arquivos no mesmo projeto**, como pode ser visto no exemplo:

**Projeto A**
```C#
internal class DatabaseConnection
{
    public static string ConnectionString = "~imaginem uma string de conexão de banco de dados aqui~";
}

public class Database
{
    public void Connect()
    {
        // Isto é possível pois DatabaseConnection se comporta como público dentro
        // de um mesmo projeto.
        Console.WriteLine("ConnectionString: " + DatabaseConnection.ConnectionString);
    }
}
```

**Projeto B**
```C#
class Program
{
    static void Main()
    {
        // A classe 'DatabaseConnection' é inacessível fora do 'Projeto A'
        // var connectionString = DatabaseConnection.ConnectionString;
        
        var database = new Database();
        
        // Vai exibir a connection string pois está acessando a classe interna 'DatabaseConnection'
        // de forma indireta.
        database.Connect();
    }
}
```

## Modificador `internal protected`
A combinação das palavras-chave `internal` e `protected`, `internal protected`, é um modificador de acesso para membros de tipo.
Tipos ou membros `internal protected` são acessíveis **somente em arquivos no mesmo projeto**. Também é acessível em **classes derivadas** somomente se o acesso ocorre por meio de uma váriavel do tipo da classe derivada.

**Projeto A**
```C#
public class BaseClass
{
    protected internal int number = 0;
}

public class TestClass
{
    public void Test()
    {
        // Funciona pois a 'BaseClass' está no mesmo projeto.
        var baseObj = new BaseClass();
        baseObj.number = 5;
    }
}
```

**Projeto B**
```C#
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObj = new BaseClass();
        var derivedObj = new DerivedClass();
        
        // Erro, pois 'number' só pode ser acessado por classes que derivam de 'BaseClass'
        //baseObj.number = 10;
        
        // Funciona pois a classe 'DerivedClass' deriva de 'BaseClass'
        derivedObj.number = 10;
    }
}
```

## Modificador `private protected`
A combinação das palavras-chave `private` e `protected`, `private protected`, é um modificador de acesso para membros de tipo.
Tipos ou membros `private protected` são acessíveis **por tipos derivados de sua classe base**, porém **apenas dentro de seu projeto**.

**Projeto A**
```C#
public class BaseClass
{
    private internal int number = 0;
}

public class DerivedClass1 : BaseClass
{
    public void Test()
    {
        var baseObj = new BaseClass();
        
        // Erro, pois 'number' só pode ser acessado
        // por classes derivadas de 'BaseClass'
        //baseObj.number = 5;
        
        // Funciona pois estamos acessando 'number' da instância da classe derivada
        number = 5;
    }
}
```

**Projeto B**
```C#
class DerivedClass2: BaseClass
{
    public void Test()
    {
        // Erro, pois 'number' só pode ser acessado dentro do Projeto A
        //number = 10;
    }
}
```

# Referências

* [Access Modifiers](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)
* [Modificadores de Acesso](https://medium.com/trainingcenter/modificadores-de-acesso-3f87133611c8)