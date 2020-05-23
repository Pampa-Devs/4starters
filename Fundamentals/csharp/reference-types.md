# 🟢 Tipos de Referência

Com os **tipos de referência** é possível que duas variáveis diferentes referenciem o mesmo objeto, ou seja, alterar uma delas irá alterar o valor da outra.

## Tipo String

O tipo `string` é uma cadeira de caracteres que representa uma sequência de um ou mais caracteres Unicode. `string` é um alias de [System.String](https://docs.microsoft.com/pt-br/dotnet/api/system.string?view=netcore-3.1).

Mesmo `string` sendo um tipo de referência, os operadores de igualdade `==` e `!=` comparam os **valores** de objetos `string`, não referências. Por exemplo:
```C#
string a = "M";
string b = "Mundo";

a += "undo";

Console.WriteLine("As strings são iguais: " + (a == b));
Console.WriteLine("As referências das strings são iguais: " + object.ReferenceEquals(a, b));
```
Este código vai exibir **As strings são iguais: true** e, em seguida, **As referências das strings são iguais: false** porque os conteúdos das cadeidas de caracteres são equivalentes, mas `a` e `b` são instâncias diferentes.

O operador `+` concatena as cadeias de caracteres:
```C#
string a = "Olá " + "Mundo";
Console.WriteLine(a);
```
Isso cria uma cadeia de caracteres que contém **Olá mundo**.

Cadeia de caracteres são *imutáveis*, ou seja, o conteúdo de uma `string` não pode ser alterado depois que o objeto é criado, embora a sintaxe faça com que pareça que você pode fazer isso. Toda nova operação em uma string acaba
por criar uma nova `string`.

O operador `[]` pode ser usado para ler um caracter específico dentro de uma `string`. Por exemplo:
```C#
string texto = "Felipe";
char caracter = texto[0];

Console.WriteLine(caracter);
```
O resultado irá imprimir a letra **F** como resultado;

## Tipo Class

Class é um objeto que é declarado usando o alias `class`. Uma classe é uma estrutura de dados que combina ações e estados em uma única unidade. 
```C#
class TestClass
{
    // Métodos, prorpriedades, campos, eventos, delegados e sub classes vão aqui dentro
}
```

O **C#** não da suporta a múltiplas heranças que nem linguagens como **C++**, somente herança única. Porém, uma classe pode implementar mais de uma interface. 
Exemplos:

```C#
// Classe sem nenhuma herança
class ClassTest
{
}

// Classe com uma única herança
class ClasseDerivada : ClasseBase
{
}

// Classe sem nenhuma herança, porém implementa duas interfaces
class ClassTest : InterfaceA, InterfaceB
{
}

// Classe com uma única herança e implementa uma interface
class ClasseDerivada : ClasseBase, InterfaceA
{
}
```

Classes que você declara dentro de um namespace, que não são sub classes de outras classes, podem ser [públicas]() ou [internas](). As classes são `internal` por padrão

Já seus membros podem ser [públicos](), [internos protegidos](), [protegidos](), [internos](), [privados]() ou [protegidos privados](). Os membros são `private` por padrão.

Uma classe pode conter várias declarações:
* Construtores
* Constantes
* Campos
* Finalizadores
* Métodos
* Propriedades
* Indexadores
* Operadores
* Eventos
* Delegados
* Classes
* Interfaces
* Tipos de estrutura
* Tipos de enumeração

Exemplo:
```C#
class Personagem
{    
    // Campos
    private string Nome;
    private string Classe;

    // Construtor padrão
    public Personagem()
    {
        Nome = "Sem Nome";
        Classe = "Sem Classe";
    }
    
    // Construtor com parâmetros
    public Personagem(string nome, string classe)
    {
        this.Nome = nome;
        this.Classe = classe;
    }
    
    // Finalizador
    ~Personagem()
    {
        Nome = string.Empty;
        Classe = string.Empty;
    }
    
    // Método
    public void Atacar()
    {
        Console.WriteLine($"{Nome} da classe {Classe} está atacando!");
    }
}

class Mundo
{
    static void Main()
    {
        // Instanciação usando Construtor padrão
        var personagemSemNome = new Personagem();
        
        // Instanciação usando Construtor com parâmetros
        var felipe = new Personagem("Felipe", "Berserker");
        
        // Invocação do método Personagem.Atacar()
        personagemSemNome.Atacar();
        felipe.Atacar();
        
        //Removendo referência para chamar o Finalizador
        felipe = null;
    }
}
```

## Tipo Interface

Uma interface tem como objetivo definir um contrato, qualquer [class](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/variaveis.md#2-tipo-class) ou [struct](https://github.com/Pampa-Devs/4starters/blob/master/Fundamentals/csharp/variaveis.md#2-tipo-class)
que implemente este contrato deve fornecer uma implementação **obrigatória** dos membros definidos na interface. Exemplo:
```C#
interface ICarro
{
    // Propriedade
    string Nome { get; set; }
    string Marca { get; }
    
    // Métodos
    void Acelerar();
    void Freiar();

    // Método com implementação padrão
    void Buzinar()
    {
        Console.WriteLine("Nani!?")
    }
}

class Fusca : ICarro
{
    // Implementação das propriedades
    string Nome { get; set; }
    string Marca => return "Meu Fusquinha Turbinado";
	
    // Implementação explícita da interface
    void ICarro.Acelerar()
    {
        //Lógica para acelerar o fusca
    }
    // Implementação implícita da interface
    void Freiar()
    {
        //Lógica para freiar o fusca
    }
    
    static void Main()
    {
        // Declaração de uma interfacia com uma instância de fusca
        ICarro carro = new Fusca();
        
        // Invocação dos métodos da interface
        carro.Acelerar();
        carro.Freiar();
        
        // Invocação de uma implementação padrão
        carro.Buzinar();
    }
}
```

Uma declaração de interface podem ser as seguintes:
* Método
* Propriedades
* Indexadores
* Eventos
Nenhuma dessas declarações de membros precisa conter um corpo. Como podemos observar no exemplo acima, **Acelerar** e **Freiar**, na interface **ICarro** não possuem implementação.
Caso seja criado um corpo para uma declaração, este corpo será uma *implementação padrão*.

# Referências
* https://docs.microsoft.com/pt-br/dotnet/csharp/
* https://www.utf8-chartable.de/unicode-utf8-table.pl?utf8=dec
* https://www.devmedia.com.br/introducao-a-variaveis-e-constantes-no-csharp/29629
* http://www.macoratti.net/net_tpdt.htm