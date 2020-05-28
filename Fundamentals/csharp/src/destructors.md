# 🗑 Finalizadores 

Também conhecidos como **destruidores**, os *finalizadores* são utilizados para executar a "limpeza final", quando uma instância está prestes a ser coletada pelo coletor de lixo, em outras palavras, sendo destruída.
Quando um objeto é finalizado, a memória alocada para o seu armazenamento é liberada.

Os *finalizadores* tem o mesmo nome de sua classe, sendo precedido pelo operador `~`.

```
class DatabaseConnection
{
    private SqlConnection connection;
    
    ~DatabaseConnection
    {
        // Fecha a conexão no finalizador.
        connection.Dispose();
    }
}
```

O programador não tem controle sobre quando um finalizador é chamado pois isso é tarefa do coletor de lixo. O coletor busca por objetos que não estão mais sendo utilizados e, caso seja qualificado para finalização, ele irá executar
o finalizador (se o mesmo existir) e irá recuperar a memória alocada para armazenar aquele objeto.

# Referências

* [Destructors](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/destructors)