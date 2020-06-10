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
Pokémon do tipo água atacou // Substituição da função Attack pela classe filha
Pokémon atacou 
Pokemon do tipo fogo atacou
```