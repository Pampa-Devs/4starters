# 🎭 Polimorfismo
Como a Herança, o *Polimorfismo* é um dos pilares da programação orientada a objetos. Polimorfismo, do grego *polymorfismós*, significa "de muitas formas" e no C# podemos observar dois aspectos distintos:
* Objetos de uma classe filha podem ser tratados como objetos de uma classe pai, em parâmetros de método, coleções e matrizes. Quando isso ocorre, **o tipo declarado** do objeto **não é mais idêntico** ai seu tipo em tempo de execução.
* As classes pais podem implementar métodos **virtuais** e as classes filhas podem **substituí-los** com suas próprias implementações.

```C#
public class Pokemon
{
    public int Health { get; private set; }
    public int Damage { get; private set; }
    public string Name { get; private set; }
    
    public Pokemon(string name)
    {
        Health = 100;
        Damage = 25;
        Name = name;
    }
    
    public virtual void Attack()
    {
        Console.WriteLine("Pokémon atacou");
    }
}

public class WaterPokemon
{
    public override void Attack()
    {
        Console.WriteLine("Pokémon do tipo água atacou");
        base.Attack();
    }
}

public class FirePokemon
{
    public override void Attack()
    {
        Console.WriteLine("Pokémon do tipo fogo atacou");
    }
}

public class Program
{
    public static void Main()
    {
        var pokemons = new List<Pokemon>()
        {
            new Pokemon("Snorlax"),
            new WaterPokemon("Squirtle"),
            new FirePokemon("Charmander"),
        }
        
        foreach(var pokemon in pokemons)
        {
            pokemon.Attack();
        }
    }
}
```

O resultado do programa acima será:
```C#
Pokémon atacou
Pokémon do tipo água atacou // Substituição da função Attack pela classe filha WaterPokemon
Pokémon atacou 
Pokemon do tipo fogo atacou // Substituição da função Attack pela classe filha FirePokemon
Pokémon atacou 
```

## Membros virtuais

Quando uma classe derivada herda de uma classe base, ela obtém todos os métodos, campos, propriedades e eventos da classe base.
Uma classe derivada poderá substituir um membro de classe base somente se o membro for declarado como **virtual** ou **abstrato**.
O membro derivado também deve utilizar a palavra-chave **override** para indicar explicitamente que o método destina-se para participar da invocação virtual.
Além disso, a pessoa que desenvolve a classe base possui escolhas diferentes para o comportamento dos métodos virtuais da mesma:
* A classe derivada pode sobreescrever o comportamento dos membros virtuais na classe base
```C#
public class ClasseBase
{
    public virtual void Parar() { Console.WriteLine("Parar") }
}

public class ClasseDerivada : ClasseBase
{
    // Nesse cenário, o método sobrescrito 'Parar' substitui completamente
    // o comportamento do 'Parar' da classe Base
    public override void Parar() { Console.WriteLine("Forçar parada") }
}
```
* A classe derivada sempre herda o comportamento base mais próximo sem substituí-lo, preservando o comportamento existente, mas permitindo que mais classes derivadas substituam o método.
```C#
public class ClasseBase
{
    public virtual void Parar() { Console.WriteLine("Parar"); }
}

public class ClasseDerivada : ClasseBase 
{ 

}

public class Program 
{
    public static void Main()
    {
        var classe = new ClasseDerivada();
        classe.Parar(); // Executa o método "Parar" da classe base, retornando o texto "Parar"
    }
}
```

## Ocultar membros da classe
Caso você queira, é possível ocultar um membro da classe base. Para tal, devemos utilizar a palavra-chave **new**.
```C#
public class ClasseBase
{
    public virtual void Run() { Console.WriteLine("Running..."); }
}

public class ClasseDerivada : ClasseBase
{
    public new void Run() { Console.WriteLine("Correndo..."); }
}

public class Program 
{
    public static void Main()
    {
        var classBase = new ClasseBase();
        classBase.Run(); // Retorna "Running..."

        var classeDerivada = new ClasseDerivada();
        classeDerivada.Run() // Retorna "Correndo..."
    }
}
```

## Impedindo que classes derivadas substituam membros virtuais
Independentemente de quantos níveis de parentesco sua classe derivada possuir, os membros virtuais da classe base permanecem virtuais.
Porém, é possível interromper a herança virtual, declarando uma substituição como **sealed**.
```C#
public class A 
{
    public virtual void Run() { }
}

public class B : A
{
    public sealed void Run() { } // Método virtual selado
}

public class C : B 
{
    public new void Run() {} 
}
```
Como o método **Run** da classe B não é mais virtual, não é mais possível seguir utilizando o **override** nas classes derivadas. 
Ainda é possível entretanto substituir os membros selados utilizando a palavra-chave **new**.

## Acessando membros virtuais da classe base
Como visto no primeiro exemplo, é possível além de substituir o comportamento de um membro, seguir utilizando o comportamento base da classe base
utilizando a palavra-chave **base**.
```C#
public class ClasseBase 
{
    public virtual void Teste() 
    {
        Console.WriteLine("Teste");
    }
}

public class ClasseDerivada : ClasseBase
{
    public override void Teste() 
    {
        Console.WriteLine("Preparos adicionais antes de executar o método Teste...");
        base.Teste();
    }
}
```

# Referências
* [Polimorfismo](https://docs.microsoft.com/pt-br/dotnet/csharp/programming-guide/classes-and-structs/polymorphism)