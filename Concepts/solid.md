<h1 align="center">
  <img src="/Images/solid.png" alt="Concepts" width="450px" />
</h1>

# O que é SOLID?

Na *Programação Orientada a Objetos* (POO), **SOLID** é um acrônimo para cinco princípios que facilitam no desenvolvimento de software. Esses princípios podem ser aplicados a qualquer linguagem POO.

Estes princípios foram apresentados por [Robert C. Martin](https://en.wikipedia.org/wiki/Robert_C._Martin) no artigo [The Principles of OOD](http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod)

## Os 5 princípios **S.O.L.I.D.**:

1. **S - Single Responsability Principle** (Príncipio da responsabilidade única)
2. **O - Open-Closed Principle** (Princípio Aberto-Fechado)
3. **L - Liskov Substitution Principle** (Princípio da substituição de Liskov)
4. **I - Interface Segregation Principle** (Princípio da Segregação da Interface)
5. **D - Dependency Inversion Principle** (Princípio da inversão da depêndencia)

Ao seguir estes princípios, o código do desenvolvedor se torna **mais limpo**, mais **modularizado** e com pouco **acoplamento**, o que acaba por facilitar a refatoração e reutilização do código.

## SRP -  Príncipio da responsabilidade única
> "Uma classe deve ter apenas uma única responsabilidade"

Esse princípio declara que uma classe deve ser especializada em um **único assunto** e possuir apenas **uma responsabilidade** dentro do software, ou seja, a classe deve ter uma única tarefa ou ação para executar.

Em programação orientada a objetos, uma classe que sabe demais ou faz coisas demais é chamada de **God Class** (Classe Deus). Ao alterar uma **God Class**, sempre existe um nível de incerteza se a alteração de uma responsabilidade
irá comprometer todas as outras, principalmente se não existirem testes automatizados.

### Exemplo prático de uma violação do SRP:

```C#
class Customer
{
    public int id;
    public string name;
	
    public IEnumerable<Customer> GetCustumers() {\*...*\}
    public Order GetCustumerOrders(int customerId) {\*...*\}
    public void AddCustomer(Customer customer) {\*...*\}
    public void DeleteCustomer(Customer customer) {\*...*\}
	
    public void RenderCustomer() {\*...*\}
    public void RenderCustomerOrders() {\*...*\}

    public void Save() {\*...*\}
    public void Load() {\*...*\}
    public void Update() {\*...*\}
    public void Delete() {\*...*\}
	
}
```

A classe `Customer` está violando o SRP, pois realiza três tipos de tarefas. Ela além de lidar com os dados do `Customer`, também é responsável pela renderização e manipulação dos dados.

A violação deste príncipio pode resultar nos seguintes problemas:
* **Falta de coesão** - Uma classe não deve assumir responsabilidades que não são suas
* **Alto acoplamento** - Quanto maior o número de responsabilidades, maior o número de dependências.
* **Dificuldade na implementação de testes automatizados** - É díficil de criar uma *"versão de testes"* dessa classe
* **Dificuldades para reaproveitamento do código** - Por ter várias responsabilidades, provavelmente não irá ser reaproveitada em um projeto diferente

### Aplicando SRP na classe *customer*:
```C#
class Customer
{
    public int id;
    public string name;
}

class CustomerService
{
    public IEnumerable<Customer> GetCustumers() {\*...*\}
    public Order GetCustumerOrders(int customerId) {\*...*\}
    public void AddCustomer(Customer customer) {\*...*\}
    public void DeleteCustomer(Customer customer) {\*...*\}
}

class CustomerRenderer
{
    public void RenderCustomer() {\*...*\}
    public void RenderCustomerOrders() {\*...*\}
}

class CustomerRepository
{
    public void Save() {\*...*\}
    public void Load() {\*...*\}
    public void Update() {\*...*\}
    public void Delete() {\*...*\}
}
```
Perceba que conseguimos **quebrar** a classe `customer` em quatro diferentes classes, onde cada uma tem sua própria responsabilidade.

Por reforçar a modularização, o SRP é considerado um dos princípios mais importantes. Ele também é a base para outros princípios e padrões, pois lida com questões de coesão e acoplamento, coisa que todo bom desenvolvedor deve saber aplicar.

## OCP - Príncipio Aberto-Fechado
> "Entidades de software devem ser abertas para extensão, mas fechadas para modificação."

O *príncipio aberto-fechado* prega que quando novos comportamentos e recursos forem adicionados no software, se deve **estender** e não modificar o código original.

### Exemplo prático de uma violação do OCP:
Suponha que temos um sistema de tarifas por km percorrido para bicicletas e carros. 
```C#
class BikeFare
{
    public double CalculateBikeFare(double distance) { \*...*\ }
}

class CarFare
{
    public double CalculateCarFare(double distance) { \*...*\ }
}

class FareService
{
    public double CalculateFare(double distance, string fareType)
    {
        if (fareType == "bike")
        {
            var fare = new BikeFare();
            return fare.CalculateBikeFare(distance);
        }
        else if (fareType == "car")
        {
            var fare = new CarFare();
            return fare.CalculateCarFare(distance);
        }
    }
}
```

A classe *FareService*, para cada tipo diferente de veiculo, possui uma classe de calculo diferente. Caso surja a necessidade de adicionar suporte a outros veiculos, obviamente teríamos de modificar essa classe, assim violando o princípio Aberto-Fechado do SOLID.

**O principal problema** de alterar uma classe já em funcionamento é a introdução de novos bugs.

Existe uma frase no artigo do **Uncle Bob** que é o seguinte:
> Separe o comportamento extensível por trás de uma interface e inverta as dependências

O que ele quer dizer é:
* Isole a lógica que é extensível em classes separadas, no nosso caso seriam os métodos **CalculateBikeFare** e **CalculateCarFare**.
* Com *inverta as dependências*, o **Uncle Bob** tenta nos dizer para não depender da implementação das classes **BikeFare** e **CarFare** e sim da da abstração.

### Aplicando OCP

Olhando para o nosso exemplo, podemos concluir que o nosso problema é, que **para cada novo tipo de veiculo** iremos adicionar um novo `if` no programa. Aplicando o OCP e **isolando** esse comportamento **extensível** atrás de uma interface,
podemos criar uma interface com o nome de `IVehicleFare` contendo o método `Calculate(double distance)`. 

Nossa classe `FareService` **irá depender de uma abstração** `IVehicleFare` ao invés de depender das implementações.

Código refatorado:
```C#
interface IVehicleFare
{
    double Calculate(double distance);
}

class BikeFare : IVehicleFare
{
    public double Calculate(double distance) { \*...*\ }
}

class CarFare : IVehicleFare
{
    public double Calculate(double distance) { \*...*\ }
}

class FareService
{
    public double CalculateFare(double distance, IVehicleFare fare)
    {
        return fare.Calculate(distance);
    }
}
```

Com essa alteração, a classe `FareService` não tem mais necessidade de saber qual o tipo de tarifa necessário para chamar o método `Calculate()`. Ela será capaz de calcular a tarifa de qualquer tipo de veículo
que seja criado no futuro (caminhão, avião, etc) sem qualquer necessidade de alteração do código fonte. 

Com isso implementamos o *Open-Closed Principle* em nosso código!

## LSP - Princípio da substituição de Liskov
> "Objetos em um programa devem ser substituíveis por instâncias de seus subtipos, sem alterar a funcionalidade do programa"

Este princípio foi apresentado por [Barbara Liskov](https://en.wikipedia.org/wiki/Barbara_Liskov), que também recebeu o prêmio [Turing Award](https://en.wikipedia.org/wiki/Turing_Award) pelas suas contribuições.

A definição formal de Liskov sobre o príncipio diz que:
> Se para cada objeto o1 do tipo S há um objeto o2 do tipo T de forma que, para todos os programas P definidos em termos de T, 
o comportamento de P é inalterado quando o1 é substituído por o2 então S é um subtipo de T

De uma forma mais simples, ela tenta dizer que, em uma situação onde você tem uma classe base **ave** e uma derivada **pinguim**, pinguim deve poder executar **todas** as
ações que uma **ave** pode, em outras palavras, **o pinguim deve ser tradado como uma ave**. Se, sob qualquer circunstância, o **pinguim** não puder executar uma ação que uma **ave** pode, 
isso resultará em uma violação do *Liskov Substitution Principle*.

Para facilitar o entendimento, vamos ao exemplo prático:
```C#
class ClasseBase
{
    public string GetName()
    {
        return "Sou o objeto 'ClasseBase'";
    }
}

class ClasseDerivada : ClasseBase
{
    public new string GetName()
    {
        return "Sou o objeto 'ClasseDerivada'";
    }
}

class Program
{
    public void Main()
    {
        var objeto1 = new ClasseBase();
        var objeto2 = new ClasseDerivada();
        
        Console.WriteLine(objeto1.GetName()); // Sou o objeto 'ClasseBase'
        Console.WriteLine(objeto2.GetName()); // Sou o objeto 'ClasseDerivada'
    }
}
```
Estamos usando a função `GetName()` tanto da `ClasseBase` quanto da `ClasseDerivada` e o código funciona da mesma forma para ambas. Neste exemplo não existe violação alguma.

### Exemplos prático de violações do LSP:

* Sobrescrever/implementar um método que não faz nada;
* Lançar uma exceção inesperada;
* Retornar valores de tipos diferentes da classe base.

Sobrescrevendo um método que não faz nada:
```C#
class Penguim : Bird
{
    public override void Fly()
    {
        // Não faz nada
    }
}
```

Lançando uma exceção inesperada:
```C#
class Vehicle
{
    public void TurnOn()
    {
        // Liga o veículo
    }
}

class Bike : Vehicle
{
    public new void TurnOn()
    {
        throw new Exception("Uma bicicleta não precisa ser ligada");
    }
}
```

Retornando valores de tipos diferentes:
```C#
class Security
{
    public bool Validate()
    {
        // Valida usuário
        return true;
    }
}

class ApiSecurity : Security
{
    public new string Validate()
    {
        //Valida usuário
        return "Usuário válido";
    }
}
```

Ao seguir o **LSP** ganhamos mais confiança para usar [polimorfismo](https://www.devmedia.com.br/conceitos-e-exemplos-polimorfismo-programacao-orientada-a-objetos/18701) por exemplo. Não precisamos nos preocupar com resultados inesperados.

## ISP - Princípio da segregação da interface
> "Muitas interfaces de clientes específicas, são melhores do que uma para todos propósitos"

Basicamente, esse príncipio diz que é melhor ter **várias interfaces especificas** do que forçar uma classe a implementar interfaces e métodos que não irá utilizar.

### Exemplo prático de uma violação do ISP:
```C#
interface ILogger
{
    void Log(string message);
    List<string> GetLogs();
}

class ConsoleLogger : ILogger
{
    public void Log(string message) 
    {
        Console.WriteLine(message);
    }

    public List<string> GetLogs() 
    {
        throw new NotImplementedException();
    }
}

class EventLogger : ILogger
{
    public EventDbContext context = new EventDbContext();

    public void Log(string message) 
    {
        context.Events.Add(message);
    }

    public List<string> GetLogs() 
    {
        return context.Events.GetAll();
    }
}
```
Perceba que ao implementar a interface `ILogger`, a classe `ConsoleLogger` que não possui armazenamento de *logs* acaba por ser obrigada a implementar a função `GetLogs()`.
Essa estrutura não está violando somente *Interface Segregation Principle*, ela também viola o *Liskov Substitution Principle* pois a classe `ConsoleLogger` não implementa todas as funcionalidades de `ILogger`.

### Aplicando ISP
Esse problema é facilmente resolvido criando interfaces mais específicas, veja:
```C#
interface ILogger
{
    void Log(string message);
}

interface IDbLogger : ILogger
{
    void List<string> GetLogs();
}

class ConsoleLogger : ILogger
{
    public void Log(string message) 
    {
        Console.WriteLine(message);
    }
}

class EventLogger : IDbLogger
{
    public EventDbContext context = new EventDbContext();

    public void Log(string message) 
    {
        context.Events.Add(message);
    }

    public List<string> GetLogs() 
    {
        return context.Events.GetAll();
    }
}
```
No exemplo acima, **removemos** o método `GetLogs()` da interface `ILogger` e **adicionamos** em uma interface derivada `IDbLogger`. Essa alteração nos possibilita 
isolar os comportamentos das classes *logger* respeitando o príncipio ISP.

## DIP - Princípio da inversão da depêndencia
> "Deve-se depender de abstrações, não de objetos concretos"

De acordo com **Uncle Bob**, esse princípio pode ser definido da seguinte forma:
* Módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender da abstração.
* Abstrações não devem depender de detalhes. Detalhes devem depender de abstrações.

### Exemplo prático de uma violação do DIP:
```C#
public class PaymentService
{
    private readonly PayPalGateway _gateway;

    public class PaymentService()
    {
        _gateway = new PayPalGateway();
    }
    
    public void Pay(decimal value)
    {
        _gateway.Pay(value);
    }
}
```

Para realizar um pagamento, a classe `PaymentService` precisa inicializar o gateway de pagamento, para isso, ela cria uma instancia de `PayPalGateway` em seu construtor
para poder realizar a operação de pagamento.

O problema deste código é o **alto nível de acoplamento** entre a classe `PaymentService` e `PayPalGateway`, pois a `PayPalService` tem a responsabilidade de criar uma
instância da classe `PayPalGateway`. Para criar um teste *mocado* de nosso serviço de pagamento, teríamos que mocar também o `PayPalGateway` e neste exemplo isso não não é possível.

### Aplicando DIP

Como dito anteriormente, *módulos de alto nível (PayPalService) não devem depender de módulos de baixo nível (PayPalGateway). Ambos devem depender da abstração.*

Com isso em mente, podemos criar uma interface para o nosso gateway de pagamento.
```C#
public interface IPaymentGateway
{
    public void Pay(decimal value);
}
```

A nossa classe `PayPalGateway` será a implementação de nossa nova interface.
```C#
public class PayPalGateway : IPaymentGateway
{
    public void Pay(decimal value) {\* ... *\};
}
```

E por fim, nosso serviço de pagamento vai ser modificado para o seguinte:
```C#
public class PaymentService
{
    private readonly IPaymentGateway _gateway;

    public class PaymentService(IPaymentGateway gateway)
    {
        _gateway = gateway;
    }
    
    public void Pay(decimal value)
    {
        _gateway.Pay(value);
    }
}
```

Passamos a interface `IPaymentGateway` ao invés de passar direto a `PayPalGateway` pois imagine que existisse uma tarefa para mudar PayPal por pagamento por boleto:
A nossa classe `PaymentService` exigiria uma alteração para funcionar com o novo *gateway de pagamento*.

Com a alteração mostrada neste exemplo, possibilitamos que **n** novos *gateway de pagamentos* sejam adicionados ao código sem a necessidade de alterar a classe `PaymentService`.
Ou seja, não estamos mais violando o **DIP**, ambas as classes estão desacopladas e dependendo de uma abstração e favorecemos uma possível reusabilidade do código.

## Conclusão

Somente por respeitar os princípios defendidos pelo **SOLID**, obtemos um software escalável, flexível, robusto e modular. Além disso, realizar manutenções e testes no sistema se torna uma atividade trivial.

# Autores
* [Felipe Almeida](https://github.com/felipe-allmeida) - Fundador do PampaDevs e Engenheiro de Software

## Agradecimentos

* Minha irmã, Thais de Almeida - Pela formatação e correção do texto.
* [crejaneogomes](https://github.com/crejaneogomes) - Pela revisão do ponto de vista técnico.

# Referências
* http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod
* https://medium.com/joaorobertopb/o-que-%C3%A9-solid-o-guia-completo-para-voc%C3%AA-entender-os-5-princ%C3%ADpios-da-poo-2b937b3fc530
* https://pt.wikipedia.org/wiki/SOLID
* https://refactoring.guru/pt-br
