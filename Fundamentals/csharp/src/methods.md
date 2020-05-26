# 🚶 Métodos

Um *método* é um bloco de código **nomeado** que implementa alguma ação ou cálculo que pode ser executado.

Métodos são declarados da seguinte forma:
```C#
void MyMethod()
{
    // Executa ção ou cálculo...
}
```

Os métodos também podem retornar valores, basta atribuir o **tipo** do valor a ser retornado ao método.
```C#
// Não retorna nada 'void'
void MyMethod()
{
}

// Retorna um tipo 'int'
int MyAge()
{
    return 25;
}

// Retorna um tipo 'string'
string MyName()
{
    return "Felipe";
}
```

E no exemplo a seguir, atribuimos o valores dos métodos `MyAge` e `MyName` as váriaveis `age` e `name`:
```C#
int age = MyAge();

string name = MyName();
```

## Parâmetros

Podemos passar parâmetros por valor ou por referência para um método. Estes parâmetros podem ser de qualquer **tipo** e métodos podem receber **N** parâmetros.
```C#
static void Main()
{
    // Invoca o método 'SendMessage' passando "HelloWorld" como parâmetro
    SendMessage("HelloWorld");
    
    // Invoca o método 'GetSeconds' que converte horas em segundos
    var seconds = GetSeconds(24);
    
    //Invoca o método 'CreatePerson' que cria o tipo 'Person'
    Person person = CreatePerson("Felipe", 25);
}

public static void SendMessage(string message)
{
    Console.WriteLine(message);
}

public static int GetSeconds(int hour)
{
    return hour * 3600;
}

public static Person CreatePerson(string name, int age)
{
    Person p = new Person();
    
    p.name = name;
    p.age = age;
    
    return p;
}


public class Person
{
    public string name;
    public string age;
}
```

## Parâmetros de **Tipo de Valor**
Passar uma váriavel de tipo de valor para um método, significa passar uma cópia da váriavel para o método. Qualquer alterações no parâmetro que ocorrem dentro do método não afetam os dados originais.

### Parâmetros de **tipo de valor**, sendo passados por valor
O exemplo a seguir demonstra a passagem de parâmetros de **tipo de valor** por *valor*. A váriavel `number` é passada por *valor* para o método `AddFiveToNumber`.
Toda e qualquer alteração que acontecer dentro do método não irão afetar o valor original da váriavel `number`.
```C#
static void Main()
{
    
    int number = 5;
    Console.WriteLine("Valor antes de chamar o método: " + number);
    
    AddFiveToNumber(number);
    
    Console.WriteLine("Valor depois de chamar o método: " + number);
}

public static void AddFiveToNumber(int number)
{
    number = number + 5;
    Console.WriteLine("Valor dentro do método: " + number);
}


// Resultado:
// Valor antes de chamar o método: 5
// Valor dentro do método: 10
// Valor após chamar o método: 5
```

### Parâmetros de **tipo de valor**, sendo passados por referência
O exemplo a seguir é o mesmo que o anterior, exceto que o argumento é passado como um parâmetro `ref`, o que faz a váriavel se comportar como um tipo de referência, -
ou seja, as alterações dentro do método serão persistidas fora do método.
```C#
static void Main()
{
    
    int number = 5;
    Console.WriteLine("Valor antes de chamar o método: " + number);
    
    AddFiveToNumber(ref number);
    
    Console.WriteLine("Valor depois de chamar o método: " + number);
}

public static void AddFiveToNumber(ref int number)
{
    number = number + 5;
    Console.WriteLine("Valor dentro do método: " + number);
}


// Resultado:
// Valor antes de chamar o método: 5
// Valor dentro do método: 10
// Valor após chamar o método: 10
```

## Parâmetros de **Tipo de Referência**
Uma váriavel de um **tipo de referência** não contém seus dados diretamente, ela contém uma referência a seus dados. Quando você passa um parâmetro de tipo de referência por valor, é possível
alterar os dados que pertencem ao objeto referenciado.

### Parâmetros de **Tipo de Referência**, sendo passado por valor
O exemplo abaixo demonstra a passagem de um parâmetro de **tipo de referência**, `listNumbers`. para um método chamado `ChangeFirstNumber`.
Alterar um dos valores do elemento da lista dentro do método é possível, porém criar uma nova lista dentro do método não irá afetar a váriavel original, como pode ser demonstrado no exemplo abaixo:
```C#
static void Main()
{
    
    var listNumbers = new List<int> { 1, 2, 3 };
    
    Console.WriteLine("Valor do primeiro elemento da lista, antes de chamar o método: " + listNumbers[0]);
    
    CreateNewList(listNumbers);
    
    Console.WriteLine("Valor do primeiro elemento da lista, depois de chamar o método: " + listNumbers[0]);
}

public static void ChangeFirstNumber(List<int> list)
{
    list[0] = 42; // Essa alteração altera a váriavel original
    
    list = new List<int> {100, 200, 300 }; // Essa alteração é somente local.
    
    Console.WriteLine("Valor do primeiro elemento da lista, dentro do método: " + list[0]);
}


// Resultado:
// Valor antes de chamar o método: 1
// Valor dentro do método: 100
// Valor após chamar o método: 42
```

## Parâmetros de **Tipo de Referência**, sendo passado por referência
O exemplo abaixo é o mesmo do anterior, só que agora utilizando a palavra-chave `ref`. Alterações dentro do método são persistidas na váriavel original.
```C#
static void Main()
{
    
    var listNumbers = new List<int> { 1, 2, 3 };
    
    Console.WriteLine("Valor do primeiro elemento da lista, antes de chamar o método: " + listNumbers[0]);
    
    CreateNewList(ref listNumbers);
    
    Console.WriteLine("Valor do primeiro elemento da lista, depois de chamar o método: " + listNumbers[0]);
}

public static void ChangeFirstNumber(ref List<int> list)
{
    list[0] = 42; // Essa alteração altera a váriavel original
    
    list = new List<int> {100, 200, 300 }; // Essa alteração é somente local.
    
    Console.WriteLine("Valor do primeiro elemento da lista, dentro do método: " + list[0]);
}


// Resultado:
// Valor antes de chamar o método: 1
// Valor dentro do método: 100
// Valor após chamar o método: 100
```

# Referência
* [Methods](https://docs.microsoft.com/en-us/dotnet/csharp/src/language-reference/language-specification/classes#methods)