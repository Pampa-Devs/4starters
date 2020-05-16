<h1 align="center">
  <img src="/Images/types.png" alt="Types" width="650px" />
</h1>

# Tipos de Tipagem

Muitas pessoas costumam falar que a linguagem 'x' tem tipagem fraca ou forte, mas o que isso significa?

Neste artigo vou trazer vários tipos de tipagem explicados e exemplos práticos.

### Tipagem Estática

Uma linguagem tem tipagem estática quando o **tipo da váriavel** é conhecido em tempo de compilação.
Isso significa que o desenvolvedor não pode alterar o tipo da variável depois de a mesma ser declarada, o que possibilida a identificação de vários bugs triviais muito rápido.

<br>

Exemplos de linguagem estática: `C`, `C++`, `Java`, `Rust`, `Go`, `Scala` 

<br>

Exemplo em **Java**:
```Java
public class MyClass {
    public static void main(String args[]) {
        int valor = 10; // Váriavel valor é um tipo Inteiro com um valor de 10.
		
        valor = "Felipe Almeida"; // error: incompatible types: String cannot be converted to int
    }
}
```

### Tipagem Dinâmica

Na tipagem dinâmica essa verificação também ocorre, todavia ela é feita em cima do dado em si, já que as variáveis
podem conter qualquer tipo de dado. Isso significa que você, como um programador, consegue escrever um pouco mais rápido pois 
não é necessário especificar os tipos o tempo inteiro (a não ser que você use uma linguagem estática com inferência de tipo).

<br>

Exemplos de linguagem dinâmica: `Perl`, `Ruby`, `Python`, `PHP`, `JavaScript`

<br>

Exemplo em **JavaScript**:
```JavaScript
let variavel = 'Felipe Almeida'; // Variavel declarada como string

variavel = 10; // Então mudamos o tipo para number

variavel = true; // E por fim para boolean

console.log()
```

### Inferência de Tipos

Temos algumas linguagens estáticas que podem fazer a **inferência de tipo** na declaração da váriavel, mas não permitem 
que o tipo seja alterado após a declaração.

<br>

Exemplo de linguagens com inferência de tipo: `C#`, `PHP`, `Javascript`, `Python`, `Ruby`.

<br>

Exemplo em **C#**:
```C#
using System;

public class Program
{
    public static void Main()
    {
        var variavel = "Minha string"; // Variavel declarada como String
		
        variavel = 28; // Compilation error (line 9, col 14): Cannot implicity convert type 'int' to 'string'
    }
}
```

### Tipagem Fraca

A tipagem fraca está ligada a habilidade de uma linguagem **realizar conversões automaticamente** entre tipos diferentes
de dados.

Exemplo em **JavaScript**:
```JavaScript
var nome = "Felipe Almeida"; //string

var idade = 25; //number

console.log(nome + " " + idade); //Felipe Almeida 25
```

### Tipagem Forte

Linguagens com tipagem forte **não realizam conversões** entre tipos diferentes automaticamente.

Exemplo em **Python**:
```Python
nome = "Felipe Almeida" //str
idade = 25 //int

print(nome + " " + idade); //TypeError: can only concatenate str (not "int") to str
```

## Conclusão

Perceba também que várias linguagens não são **totalmente estáticas ou dinâmicas**, muitas vezes 
as linguagems tendem a mesclar alguns aspectos de tipagens diferentes.

Espero que o conceito de "tipagem" tenha ficado mais claro para você depois de ler esse artigo.

<h1 align="center">
  <img src="/Images/meme.jpeg" alt="Meme" width="600px" />
</h1>

# Autores
* [Felipe Almeida](https://github.com/felipe-allmeida) - Fundador do PampaDevs e Engenheiro de Software

# Referências
* https://www.treinaweb.com.br/blog/quais-as-diferencas-entre-tipagens-estatica-ou-dinamica-e-forte-ou-fraca/
* https://stackoverflow.com/questions/1517582/what-is-the-difference-between-statically-typed-and-dynamically-typed-languages

