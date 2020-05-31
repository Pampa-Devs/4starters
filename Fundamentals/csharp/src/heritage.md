# 👩 Herança
*Herança* é um dos pilares da programação orientada a objetos. Ela permite que você crie
uma classe que reutiliza, estende e modifica o comportamento definido em uma classe.
Em outras palavras, ela **herda** o comportamento da classe pai.

Por padrão, **todas** as classes no C# herdam implicitamente da classe [Object]()

> **Observação:**
> O C# não da suporte a várias heranças.

```C#
class BaseClass
{
    public string name = "Felipe"
    
    public void Start() {};
}

class ChildClass : BaseClass
{
}

class Program
{
    public static void Main()
    {
        var child = new ChildClass();
        // A instância child de 'ChildClass' pode acessar
        // a váriavel 'name' por ser filha de 'BaseClass'
        Console.WriteLine(child.name);
        
        // A instância de child chama o método 'Start' da classe pai
        child.Start();
    }
}

// Resultado:
// "Felipe"
```

## Herança de Membros

* Membros **privados** são visíveis apenas em classes derivadas que estão aninhadas 
(declaradas dentro da classe base), caso contrário eles não são visíveis em classes derivadas.
* Membros **protegidos** são visíveis apenas em classes derivadas.
* Membros **internos** são visíveis apenas em classes derivadas localizadas no *mesmo projeto* que a classe base.
* Membros **públicos** são vísiveis para todos.

**Projeto A:**
```C#
public class BaseClass
{
    private int ValuePrivate = 10;
    
    protected int ValueProtected = 20;
    
    internal int ValueInternal = 30;
    
    public int ValuePublic = 40;
    
    public BaseClass()
    {
        // Ok pois está sendo acessado de dentro da 'BaseClass'
        ValuePrivate = 0;
    }
    
    public class ChildClassB : BaseClass
    {
        public ChildClassB()
        {
            // Ok pois está sendo acessado de dentro de uma
            // classe derivada que está aninhada em 'BaseClass'
            ValuePrivate = 0;
        }
    }
}

public class ChildClassA : BaseClass
{
    public void TestMethod()
    {
        // O código abaixo gera um erro pois não é possível acessar 'ValuePrivate'
        // fora de  'BaseClass'
        //ValuePrivate = 0;
        
        // Ok pois está sendo acessado de uma classe derivada
        ValueProtected = 0;
        
        // Ok pois está sendo acessado de uma classe derivada que está no mesmo 
        // projeto que 'BaseClass'
        ValueInternal = 0;
        
        // Ok pois é uma váriavel pública
        ValuePublic = 0;
    }
}
```

**Projeto B:**
```
public class ChildClassC : BaseClass
{
    public void TestMethod()
    {
        // Ok pois está sendo acessado de uma classe derivada
        ValueProtected = 0;
        
        // O código abaixo gera um erro pois mesmo sendo acessado de uma classe derivada de 'BaseClass'
        // está em um projeto diferente
        ValueInternal = 0;
        
        // Ok pois é uma váriavel pública
        ValuePublic = 0;
    }
}
```

## Sobrescrevendo métodos

Também é possível sobrescrever o método de uma classe pai que possua a palavra-chave `virtual` antes de sua declaração.
Para isso precisamos adicionar a palavra-chave `override` no método da classe derivada. Além disso, mesmo sobrescrevendo o método da classe pai, ainda é possível executa-lo utilizando 
a palavra-chave `base`, como podemos ver no exemplo abaixo:
```C#
class BaseClass
{
    public virtual void Start()
    {
        Console.WriteLine("start");
    }
    
    public virtual void Finish()
    {
        Console.WriteLine("finish");
    }
}

class ChildClass : BaseClass
{
    public override void Start()
    {
        Console.WriteLine("Sobrescrito método start");
    }
    
    public override void Finish()
    {
        Console.WriteLine("Sobrescrito método finish");
        base.Finish();
    }
}

class Program
{
    static void Main()
    {
        var child = new ChildClass();
        
        child.Start();
        // Resultado:
        // "Sobrescrito método start"
        
        child.Finish();
        // Resultado:
        // "Sobrescrito método finish"
        // "finish"
    }
```

# Referências
* [Heritage](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/inheritance)
* [Object Oriented Programming](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/object-oriented-programming)