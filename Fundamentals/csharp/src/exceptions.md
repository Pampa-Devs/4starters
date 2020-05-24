# 🛑 Exceções e Manipulação de Execeções

Os recursos de manipulação da linguagem C# ajudam a lidar com quaisquer situações excepcionais ou inesperadas que ocorram
durante a execução de um programa.

## Exceções
Exceções são representadas por classes derivadas de [Exception](https://docs.microsoft.com/en-us/dotnet/api/system.exception?view=netcore-3.1), elas são mecanismos primários do C# para comunicar um estado de erro em seu software. 

No exemplo a seguir temos o método `BuyProduct` que verifica se um prroduto está disponível para compra. Caso o mesmo não esteja,
é lançada a exceção `ProductNotAvailableException` utilizando a instrução `throw`, que irá gerar um erro em seu programa.
```C#
class ProductNotAvailableException : Exeception
{
    public ProductNotAvailableException(string message) : base(message)
    {
    }
}

class ProductStore
{
    List<string> products = new List<string>() { "ps4", "xbox", "iphone 10" };
    
    public void BuyProduct(string product)
    {
        if (!products.Contains(product))
        {
            throw  new ProductNotAvailableException($"Erro: Situação não esperada, o produto não existe!");
        }
    }
}
```

## Manipulação de Exceções
No C#, os erros no programa em tempo de execução são **propagados** pelo programa usando um mecanismo chamado **exceções**. Uma vez que a exceção é gerada,
ela irá mostrar uma caixa de diálogo exibindo o erro em seu programa. Porém podemos capturar esta exceção utilizando a instrução `try` e `catch`.

```
try
{
    // Código que irá lançar uma exceção em uma situação inesperada.
}
catch (Exception ex)
{
    // Caso o bloco 'try' lance uma exceção, a mesma será capturada
    // pelo 'catch' e este trecho de código será executado:
    Console.WriteLine("Exceção capturada!);
}
```


```C#

class ProductStore
{
    List<string> products = new List<string>() { "ps4", "xbox", "iphone 10" };
    
    public void BuyProduct(string product)
    {
        try
        {
            if (!products.Contains(product))
            {
                throw new ProductNotAvailableException($"Erro: Situação não esperada, o produto não existe!");
            }
        }
        catch(ProductNotAvailableException exception)
        {
            Console.WriteLine("O produto não pode ser comprado pois não está disponível");
        }
    }
}
```
Uma instrução `try` pode conter mais de um bloco `catch`. A primeira instrução `catch` que puder capcturar a `Exception` é executado.
Qualquer `catch` posterior, é ignorado. Portanto os blocos de captura `catch` devem ser ordenados dos mais específicos para os menos específicos.

Antes do bloco `catch` ser executado, é verificado se existe um bloco `finally`. O bloco `finally` permite que o programador
trate estados ambíguos que podem ter acontecido durante o lançamento da exceção.
```C#
public class ExceptionExample
{
    static void Main()
    {
        StreamWriter sw;
        
        try
        {
            using(sw = new StreamWriter(@"C:\test\test.txt"))
            {
                sw.WriteLine("Hello");
            }
        }
        
        // Exceção mais específica primeiro
        catch (DirectoryNotFoundException ex)
        {
            Console.WriteLine(ex);
        }
        catch (FileNotFoundException ex)
        {
            Console.WriteLine(ex);
        }
        // Exceção menos específica por último
        catch (IOException ex)
        {
            Console.WriteLine(ex);
        }
        finally
        {
            Console.WriteLine("Executado com sucesso");
            
            // Caso algum erro tenha acontecido, verifica se sw foi fechado.
            // Se não foi, fecha.
            if (sw != null)
            {
                sw.Close();
            }
        }
    }
}
```

# Referências

* [Exceptions and Exception Handling](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/exceptions/)