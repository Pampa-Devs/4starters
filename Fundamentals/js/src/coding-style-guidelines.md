## Formatação
* 4 Espaços para identação
Use 4 espaços para identar o seu código para evitar conflitos entre **tabs** e **espaços**.
* Nova Linha
Sempre utilizar UNIX-Style para novas linhas (\n). Windows-Style é proibido dentro de qualquer repositório.(\r\n)
* Sem espaços em branco
Sempre remover os 'trailing white spaces' dos códigos, exemplo:
```js
let test = 5;                   
```
* Usar ponto e virgula
Por padrão (a não ser que seja acordado com o time), sempre utilizar `;` no final da linha.
* Usar aspas simples ao invés de aspas duplas
Sempre utilizar aspas simples a não ser que você esteja escrevendo um JSON.
**Correto**
```js
let foo = 'bar';
```
**Errado**
```js
let foo = "bar";
```
* Abrir chaves sempre na mesma linha
**Correto**
```js
if (true) {
    console.log('uwu');
} else {
    console.log('test')
}
```
**Errado**
```js
if (true) 
{
    console.log('uwu');
}
else
{
    console.log('test')
}
```
* Declarar somente uma váriavel por instrução
É mais fácil de re-ordenar as linhas quando as váriaveis estão separadas.
**Correto**
```js
let keys = ['a', 'b'];
let value = [23, 42];
```
**Errado**
```js
let keys = ['a', 'b'], value = [23, 42];
```

## Conveções de Nomeclatura
* Sempre utilizar lowerCamelCase para váriaveis, propriedades e nomes de função
**Correto**
```js
let adminUser = db.query('SELECT * FROM users ...');
```
**Errado**
```js
let admin_user = db.query('SELECT * FROM users ...');
```
* Utilizar UpperCamelCase para nomes de classe
**Correto**
```js
function BankAccount() { }
```
**Errado**
```js
function back_Account() { }
```
* Sempre utilizar UPPERCASE para Constantes
```js
const SECOND = 1 * 1000;

function File() { }

File.FULL_PERMISSIONS = 0777;
```

## Variáveis
**Correto**
```js
let a = ['hello', 'world'];

let b = {
    good: 'code',
    'is generally': 'pretty'
}
```
**Errado** (**por favor não**)
```js
let a = [
    'hello', 'world'
];

let b = {good: 'code'
        , 'is generally': 'pretty'
};
```

## Condicionais
* Sempre utilizar o operador '==='
**Correto**
```js
if (a === 0) { }
if (a !== '') { }
```
**Errado**
```js
if (a == 0) { }
if (a != '') { }
```
* Sempre escrever váriaveis com nomes descritivos
**Correto**
```js
let isValidPassword = pswd.length >= 4 && /^(?:*\d).test(pswd);
if (isValidPassword) {
    // do something
}
```
**Errado**
```js
if (pswd.length >= 4 && /^(?:*\d).test(pswd)) {
    // do something
}
```

## Funções
* Evitar arvore de instruções ao retornar
**Correto**
```js
function isPercentage(val) {
    if (val < 0) return false;
    if (val > 100) return false;
    return true;
}
```
**Errado**
```js
function isPercentage(val) {
    if (val >= 0) {
        if (val < 100) {
            return true;
        } else {
            return false;
        }
    } else {
        return false;
    }
}
```
* Encadeamento de métodos
**Correto**
```js
User.findOne({name: 'foo'})
    .populate('bar')
    .exec(function(err, user) { 
        return true; 
    });
```
**Errado**
```js
User.findOne({name: 'foo'}).populate('bar').exec(function(err, user) { return true; });
```