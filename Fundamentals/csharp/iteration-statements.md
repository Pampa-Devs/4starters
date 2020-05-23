# 🔄 Estruturas de Repetição

São instruções que executam o **mesmo bloco de código *N* vezes**.

| Instrução | Exemplos | 
| :--- | :---: |
**do-while** | `do { //do something } while(condition)`
**for** | `for (initializer; condition; iterator)`
**foreach** | `foreach (var item in items) { //do something }`
**while** | `while (condition) { // do something }`

## do 

A instrução `do` executa um bloco de código **enquanto uma condição** for avaliada como `true`.
A qualquer momento do bloco de código é possível interromper o loop (repetição) utilizando a instrução `break` ou seguir para a próxima iteração usando a instrução `continue`;

### Estrutura da instrução `do`
O corpo do loop é uma linha ou bloco de código.
```C#
do
{
    Corpo
}
while(condition)
```

### Exemplo
```C#
int n = 0;

do
{
    Console.WriteLine(n); // Imprime o valor de N
    n++ // Adiciona 1 ao valor de n
}
while (n < 5)
```

Resultado:
```
0
1
2
3
4
```

## for

A instrução `for` executa um bloco de código **enquanto uma condição** for avaliada como `true`.
A qualquer momento do bloco de código é possível interromper o loop (repetição) utilizando a instrução `break` ou seguir para a próxima iteração usando a instrução `continue`;

### Estrutura da instrução `for`
Todas as três seções são opcionais. O corpo do loop é uma linha ou bloco de código.
```C#
for (initializer; condition; iterator)
    Corpo
```

Exemplo com todas as seções definidas:
```C#
for (int i = 0; i < 3; i ++)
{
    Console.WriteLine(i);
}
```
Resultado:
```
0
1
2
```

#### A seção *initializer*
As instruções na seção *initializer* são executadas apenas uma vez, antes de entrar no loop. 

Nela você pode:
* Declarar e inicializar uma váriavel local, que não pode ser acessada de fora do corpo do loop.
* Usar zero ou mais expressões da lista a seguir, separadas por `,`
  * Instrução de atribuição
  * Invocação de um método
  * prefixo ou sufixo da expressão **incrementar** (`++i` ou `i++`)
  * prefixo ou sufixo da expressão **decrementar** (`--i` ou `i--`)
  * criação de um objeto usando o operador **new**
  * usar a expressão **await**
```C#
int i = 0;
```

#### A seção *condition*
Se presentem a seção *condition* deverá ser uma expressão booliana. Essa expressão é antes de cada iteração do loop, se a mesma for avaliada como `true`, a próxima iteração do loop será executada, caso contrário o loop será finalizado.
```C#
i < 3
```

#### A seção *iterator*
A seção *iterator* define o que acontece após cada iteração do loop. 
Nela você pode usar zero ou mais expressões separadas por `,`:
* Instrução de atribuição
* Invocação de um método
* prefixo ou sufixo da expressão **incrementar** (`++i` ou `i++`)
* prefixo ou sufixo da expressão **decrementar** (`--i` ou `i--`)
* criação de um objeto usando o operador **new**
* usar a expressão **await**
```C#
i++
```

# Referências

[The do statement](https://docs.microsoft.com/pt-br/dotnet/csharp/language-reference/language-specification/statements#the-do-statement)
[foreach, in](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/foreach-in)