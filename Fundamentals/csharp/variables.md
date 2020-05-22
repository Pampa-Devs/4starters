# Tipos e Variáveis

No C# existem dois tipos: **tipos de valor** e **tipos de referência**. As váriaveis de **tipos de valor** contêm diretamente seus dados
enquanto variáveis de **tipos de referência** armazenam a referência a seus dados, o último sendo conhecido como objetos. 
* Com os **tipos de valor**, as váriaveis possuem sua própria cópia de dados, e não é possível que as operações em uma variavel afetem outra.
* Com os **tipos de referência** é possível que duas variáveis diferentes referenciem o mesmo objeto, ou seja, alterar uma delas irá alterar o valor da outra.

## A) Tipos de Valor

### 1. Tipos numéricos integrais

Como o nome já diz, os *tipos numéricos integrais* representam **números inteiros**. São **tipos simples** e todos suportam 
operadores aritméticos, Bitwise lógicos, de comparação e de igualdade.

Tipo | Intervalo | Tamanho | Tipo .NET
------- | ------- | ------- | -------
`sbyte` | -128 **até** 127 | Inteiro de 8 bits com sinal | [System.SByte](https://docs.microsoft.com/pt-br/dotnet/api/system.sbyte?view=netcore-3.1)
`byte` | 0 **até** 255 | Inteiro de 8 bits sem sinal | [System.Byte](https://docs.microsoft.com/pt-br/dotnet/api/system.byte?view=netcore-3.1)
`short` | -32.768 **até** 32.767 | Inteiro de 16 bits com sinal | [System.Int16](https://docs.microsoft.com/pt-br/dotnet/api/system.int16?view=netcore-3.1)
`ushort` | 0 **até** 65.535 | Inteiro de 16 bits sem sinal | [System.UInt16](https://docs.microsoft.com/pt-br/dotnet/api/system.uint16?view=netcore-3.1)
`int` | -2.147.483.648 **até** 2.147.483.647 | Inteiro assinado de 32 bits | [System.Int32](https://docs.microsoft.com/pt-br/dotnet/api/system.int32?view=netcore-3.1)
`uint` | 0 **até** 4.294.967.295 | Inteiro de 32 bits sem sinal | [    System.UInt32](https://docs.microsoft.com/pt-br/dotnet/api/system.uint32?view=netcore-3.1)
`long` | -9.223.372.036.854.775.808 **até** 9.223.372.036.854.775.807 | Inteiro assinado de 64 bits | [System.Int64](https://docs.microsoft.com/pt-br/dotnet/api/system.int64?view=netcore-3.1)
`ulong` | 0 **até** 18.446.744.073.709.551.615 | Inteiro de 64 bits sem sinal | [System.UInt64](https://docs.microsoft.com/pt-br/dotnet/api/system.uint64?view=netcore-3.1)

A coluna **Tipo** representa um *alias* (palavra-chave ou apelido) a ser utilizado dentro do código. Por exemplo, as declarações a seguir representam o mesmo tipo:
```C#
int a = 123;
System.Int32 b = 123;
```
O alias `int` é um apelido para `System.Int32`

O valor padrão de cada tipo integral é `0`. Cada um dos tipos possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.

### 2. Tipos numéricos de ponto flutuante

Os *tipos numéricos de ponto flutuante* representam números reais. São **tipos simples** e também suportam operadores aritméticos, bitwise lógicos], de comparação e de igualdade.

alias | Precisão | Tamanho | Tipo .NET
------- | ------- | ------- | -------
`float` | ~6 **a** 9 dígitos | 4 bytes | [System.Single](https://docs.microsoft.com/pt-br/dotnet/api/system.single?view=netcore-3.1)
`double` | ~15 **a** 17 dígitos | 8 bytes | [System.Double](https://docs.microsoft.com/pt-br/dotnet/api/system.double?view=netcore-3.1)
`decimal` | 28 **a** 29 dígitos | 16 bytes | [System.Decimal](https://docs.microsoft.com/pt-br/dotnet/api/system.decimal?view=netcore-3.1)

Estes tipos também possuem sufixos para serem determinados:
* O literal sem sufixo ou com o d ou D sufixo é do tipo `double`
* O literal f com F o ou sufixo é do tipo `float`
* O literal m com M o ou sufixo é do tipo `decimal`

Exemplos:
```C#
double d1 = 3D;
double d2 = 4d;

float f1 = 3000F;
float f2 = 4500f;

decimal dinheiro1 = 400.75m;
decimal dinheiro2 = 800.00M;

```

### 3. Tipo Boolean

A `bool` é um alias para o tipo [System.Boolean](https://docs.microsoft.com/pt-br/dotnet/api/system.boolean?view=netcore-3.1). Representa um
valor booleano que pode ser `true` ou `false` (verdadeiro ou falso).

Bastante utilizado para realizar operações lógicas do tipo booleano. É o resultado de comparação e igualdade dos operadores. No exemplo a seguir, o resultado será `A luz está ligada`:

```C#
bool luzLigada = true;

if (luzLigada == true)
{
    Console.WriteLine("A luz está ligada");
}
else
{
    Console.WriteLine("A luz está desligada");
}
```

O valor default de um boolean é `false`.

### 4. Tipos Char

O `char` é um alias para o tipo [System.Char](https://docs.microsoft.com/pt-br/dotnet/api/system.char?view=netcore-3.1) que representa um caractere [Unicode UTF-16](http://www.fileformat.info/info/charset/UTF-16/list.htm).

alias | Intervalo | Tamanho | Tipo .NET
------- | ------- | ------- | -------
`char` | U+0000 **até** U+FFFF | 16 bits | [System.Char](https://docs.microsoft.com/pt-br/dotnet/api/system.char?view=netcore-3.1)

Você pode específicar um `char` das seguintes formas:
* Um caracter literal, **j** (char a, no exemplo abaixo). 
* Uma sequência de fuga Unicode `\u`, que é seguida pela representação hexadecimal de um código de caractere (char b).
* Uma sequência de fuga hexadecimal `\x`, que é seguida pela representação hexadecimal de um código de caractere (char c).
* Um valor de código de caracter no valor correspondente (char d).

No exemplo abaixo, escolhi o caracter unicode **j** para o exemplo. Escrevi **j** em seu valor unicode **\u006A**, seu valor hexadecimal **\x006A**, e por fim, sua posição na tabela unicode **106**.
```C#
char a = 'j';
char b = '\u006A';
char c = '\x006A';
char d = (char)106;

string abcd = string.Join(" ", a, b, c, d);

Console.WriteLine(abcd);
```
No exemplo acima, utilizo a função **string.Join()** para unir todos os caracteres, o resultado exibido será **j j j j**.

### 5. Tipo de enumeração

Um *tipo de enumeração* (ou *tipo enum*) é um tipo de valor definido por um conjunto de constantes nomeadas do tipo [numérico integral](https://github.com/Pampa-Devs/concepts/blob/master/Fundamentals/csharp/variaveis.md#1-tipos-num%C3%A9ricos-integrais). `enum` é o alias do tipo [System.Enum](https://docs.microsoft.com/pt-br/dotnet/api/system.enum?view=netcore-3.1).
Para definir uma enumeração, use o alias `enum` e especifique os membros:
```C#
enum Profissoes
{
    Professor,
    Engenheiro,
    Astronauta    
}
```

Por padrão, os valores constantes associados dos membros do `enum` são do tipo `int`. Eles começam com **zero** e aumentam em **um** seguindo a ordem definida. Você também pode especificar explicitamente qualquer outro tipo 
[numérico integral](https://github.com/Pampa-Devs/concepts/blob/master/Fundamentals/csharp/variaveis.md#1-tipos-num%C3%A9ricos-integrais) como um enum, além de também poder especificar explicitamente os valores constantes, como mostra o exemplo a seguir:
```C#
enum Profissoes : ushort
{
    Professor = 0,
    Engenheiro = 1,
    Astronauta = 200    
}
```

#### 5.1. Tipos de Enumeração como Bit Flags
Se você quiser que um tipo de enumeração represente uma combinação de escolhas, defina os membros dessa enumeração de tal forma que cada membro individual seja um bit. Com isso, você pode utilizar os
[operadores lógicos bitwise '|' ou '&']() para combinar ou interceptar combinações de escolhas. Para indicar que um enumerador declara seus membros como bits, utilize o atributo [[Flags]](), por exemplo:
```C#
[Flags]
public enum DiasDaSemana
{
    Segunda				= 0b_0000_0001, //1
    Terca				= 0b_0000_0010, //2
    Quarta				= 0b_0000_0100, //4
    Quinta				= 0b_0000_1000, //8
    Sexta				= 0b_0001_0000, //16
    Sabado				= 0b_0010_0000, //32
    Domingo				= 0b_0100_0000, //64
    FinalDeSemana			= Sabado | Domingo
}

public class FlasEnumExemplo
{
    public static void Main()
    {
        Dias diasDeReuniao = Dias.Segunda | Dias.Quarta | Dias.Sexta;
        Console.WriteLine(diasDeReuniao);
        // Output: Segunda, Quarta, Sexta
        
        Dias diasHomeOffice = Dias.Terca | Dias.Sexta;
        Console.WriteLine($"Entre na reunião por telefone na {diasDeReuniao & diasHomeOffice}");
        // Output: "Entre na reunião por telefone na Sexta"

        bool temReuniaoTerca = (diasDeReuniao & Dias.Terca) == Dias.Terca;
        Console.WriteLine($"Tem reuniao na terça: {temReuniaoTerca}");
        // Output: "Tem reunião na terça: false";

        var a = (Dias)37;
        Console.WriteLine(a);
        // 37 em bits é 100101, ou seja: 0b_0010_0101
        // Output: Segunda, Quarta, Sabado
    }
}
```

### 6. Tipo de Estrutura

Um *tipo de estrutura* é um tipo de valor que pode encapsular dados e funcionalidades relacionadas. Você usa o alias `struct` para definir uma estrutura:

```C#
public struct Coordenadas
{
    public Coordenadas(double x, double y)
    {
        X = x;
        Y = y;
    }
    
    public double X { get; }
    public double Y { get; }

    public override string ToString() => $"({X}, {Y})";
}
```
Os tipos de estrutura têm *semântica de valor*. Ou seja, uma variável de um tipo de estrutura contém uma instância do tipo. Por padrão, os valores variáveis são copiados na atribuição, passando um argumento para um método
e retornando um resultado do método. No caso de uma variável do tipo `struct`, uma instância do tipo é copiada.

Normalmente, usamos uma `struct` para criar pequenos tipos centrados em dados que fornecem pouco ou nenhum comportamento.

## B) Tipos de Referência

### 1. Tipo String

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

### 2. Tipo Class

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

### 3. Tipo Interface

Uma interface tem como objetivo definir um contrato, qualquer [class](https://github.com/Pampa-Devs/concepts/blob/master/Fundamentals/csharp/variaveis.md#2-tipo-class) ou [struct](https://github.com/Pampa-Devs/concepts/blob/master/Fundamentals/csharp/variaveis.md#2-tipo-class)
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