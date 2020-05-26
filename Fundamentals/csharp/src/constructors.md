# 🛠 Construtores

Sempre que uma [classe](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/value-types.md#tipo-de-estrutura-struct) 
ou [struct](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/src/value-types.md#tipo-de-estrutura-struct)  é criada, o construtor é executado.

Os construtores tem o mesmo nome que a classe ou struct e eles normalmente são utilizados para inicializar dados do objeto sendo criado.

## Construtores sem parâmetro

No exemplo a seguir, uma classe `Player` é definida usando um construtor sem parâmetro. A classe então é instanciada com o operador `new`. O construtor
`Player` é executado pelo operador `new` imediatamente após o objeto ser criado na memória.

```C#
class Player
{
    public int Health { get; set; }
    
    public Player()
    {
       Health = 100;
    }
}

class Program
{
    static void Main()
    {
        Player p = new Player();
        Console.WriteLine("Vida: " + p.Health);
    }
}
```

Os construtores de tipo `struct` são semelhantes aos construtores da `class`, porém não podem conter um construtor sem parâmetros explícito pois um já é fornecido
automaticamente pelo compilador. Esse construtor inicializa cada membro de um `struct` em seu valor padrão.

O código abaixo utiliza um construtor sem parâmetros para o tipo **System.Int32** para ter certeza que o `int` é inicializado:
```C#
int i = new int();
Console.WriteLine(i);
```

O código abaixo é o mesmo, exceto que ele não utiliza o operador `new` para inicializar o `int`, o que resulta em um erro na aplicação.
```C#
int i = new int();
Console.WriteLine(i);
```

Porém, como vimos antes em outros exemplos, podemos inicializar tipos de valor atribuindo valores a elas:
```C#
int a = 5; // Inicialização da váriavel a

int b; 
b = 10; // Atribuição da váriavel B depois dedeclarar a mesma. 
Console.WriteLine(a + " " + b);
```

## Construtores com parâmetro
Ambas as classes e as structs podem definir construtores que usam parâmetros. Os construtores que usam parâmetros devem ser chamados por meio de uma instrução `new`.
Também é possível definir vários construtores, sem ou com parâmetros.

Um construtor pode invocar outro construtor usando a palavra-chave `this` como podemos ver no exemplo abaixo.
```C#
class Player
{
    public int Health { get; set; }
    public int Strenght { get; set; }
    public int Inteligence { get; set; }
    public int Agility { get; set; }
    
    public Player() 
    {
       Health = 100;
    }
    
    public Player(int health) 
        : this(10, 10, 10) 
        // Faz com que o construtor 'Player(int strenght, int inteligence, int agility)' sejá chamado
    {
        Health = health;
    }
    
    public Player(int strenght, int inteligence, int agility)
        : this()
        // Faz com que o construtor 'Player()'  seja chamado
    {        
        Strenght = strenght;
        Inteligence = inteligence;
        Agility = agility;
    }
}

class Program
{
    static void Main()
    {
        Player a = new Player();
        
        Player b = new Player(100); // Atribuindo a váriavel 'health'
        
        Player c = new Player(15, 5, 10); // Atribuindo a váriavel 'strenght', 'inteligence' e 'agility'
    }
}
```


# Referências
* [Using constructors](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/constructors)