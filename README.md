# garatujas - Lucas Gabriel dos Reis da silva
## html 
html (hipertext markup language) não é uma linguagem de programação, mas sim de marcação serve para criar a estrutura de páginas web, sem interações complexas ou com a parte estética. Serve para fazer títulos, parágrafos, listas, tabelas. Mas não é capaz por si só de mudar a cor, o tamanho, direção, fonte etc. dos elementos ou de fazer interações.

## css 
css(cascading style sheet) esse sim serve para fazer a parte  estética da página que o html não consegue. Ele ppode mudar a cor do fundo, a cor das letras, a disposição dos elementos, o tamanho da fonte, o sombreamento de elementos etc.

## javascript
javascript é responsável pela interação com o usuário, da o sopro da vida para o código. Pode remover, adicionar e editar elementos html e estilos css, guardar as informações em um banco de dados, fazer animações etc.

### resumo html css e js
html => estrutura básica, corpo da página
css => estética
javascript => interatividade

## java x javascript x typescript 

java: linguagem muito ligada a orientação a objetos, compliada, fortemente tipada e focada em backend

javascipt:  tipada dinamicamente, interpretada, usada em páginas web

typescript: uma versão mais fortemente tipada de javascript, mais coesa, menos erros já que é necessário identificar o tipo

| linguagem  | interp X comp |          tipada        |   uso  |
| ---------  | ------------- | ---------------------- | ------ |
|   java     |  compilada    | altamente tipada       | bakend |
| javascript |  interpretada | tipada dinamicamente   | web    |
| typescript |  interpretada | altamente tipada       | web    |

resumo = java ≠ javascript              ts = js fortemente tipado

## POO

poo => programação orientada a objetos
ao inves do código ser feito de forma estrutural, tudo em um único código continuo, é feito usando o conceito de classe e oobjetos, dividindo o código com uma classe. É bom para dar mais organização ao código.

código estruturado: 
```javascript
const carro = 12345
const cor = vermelho
console.log(" o carro é : "+ cor)
```
código orientado a objetos: 
```javascript
class Carro {
  constructor(cor, numero) {
    this.cor = cor;
    this.numero = numero;
  }

  falarCor() {
    console.log("A cor do carro é " + this.cor);
  }
}

// Exemplo de uso:
const carro1 = new Carro("vermelho", 123);
carro1.falarCor(); // A cor do carro é vermelho
```

## classes e objetos
classes: são delimitações de coisas com as mesmas caracterísitcas, não é a coisa, mas sim a linha de fala o que é aquele objeto, por exemplo se ouver a classe carros, a classse não vai ser um carro, mas sim o conjunto de ideias que falam o que é um carro. 

objetos: esses sim são as entidades delimitadas pela classe, seguindo o exemplo anterior o carro numero 2222 é um objeto, é um carro específico que pertence a classe carro

## atributos e metodos

atributos são variáveis comuns, porém ficam dentro de uma classe. basicamente são as caracteristicas que fazem o objeto ser da classe. No mesmo exemplo do carro, o que faz um carro ser um carro? ele tem que ter rodas, marca, volante etc. essas características são os atributos

métodos: são funções normais mas estão dentro de uma classe, geralmente definido por verbos cabiveis a class. O carro pode ligar, andar, acender farois. isso são funções.

Exemplo: 
```javascript
class Carro { // classe Carro
  constructor(cor, numero) {
    this.cor = cor; // this é usado para referenciar esse carro especifico de cor vermelha
    this.numero = numero; // atributo
  }

  falarCor() { // metodo para falar a cor do carro
    console.log("A cor do carro é " + this.cor);
  }
}


const carro1 = new Carro("vermelho", 123); // objeto
carro1.falarCor(); // A cor do carro é vermelho
```

obs: this é usado para referenciar o objeto atual

## encapsulamento

private: quando um atributo é private, ele só pode ser acessado dentro da classe, isso serve para proteger o dado de ser alterado de forma que possa comprometer o funcionamento do código.

public: atributo pode ser acessado de qualquer lugar

protected: o atributo só pode ser acessado na classe e nas suas sub-classes

## getters e setters

getters: um metodo que volta um valor, pode ser usado para criar um atributo como por exemplo, um get para calcular a idade com base no ano de nascimento. Muito usado para o código fora da classe poder usar atributos privados de forma controlada. sintaxe atual => get

setters: serve para validar atributos na hora em que são definidos, por exemplo se voce quer dar um valor lara rodas do carro, não pode ser -1 ou 100000000000, o set vai validar isso

## constructor

É um método que inicilaiza atributos na criação do objeto

## herança
dentro de uma classe pode haver outras classes, que podem herdar os edlementos da classe pai, exemplo, dentro da classe carro existe a classe bmw, que recee de herança os atributos de roda, cor, velociade maxima etc.

## polimorfismo
 uma classe filha pode conter o mesmo método que a classe pai mas com um funcionamento diferente, por exemplo se a classe carro tem o metod de imposto que por padrao é 1500, a classe filha carro esportivo pode ter o mesmo metodo mas com um valor 1500,7 

## Exemplo completo
```javascript
class Veiculo {  // classe de veiculos
  constructor(cor, numero, valor) { // constructor para inicializar os atributos
    this.setCor(cor);
    this.setNumero(numero);
    this.setValor(valor);
  }

  // ===== GETTERS =====
  getCor() {
    return this._cor;
  }

  getNumero() {
    return this._numero;
  }

  getValor() {
    return this._valor;
  }

  // ===== SETTERS (com validação) =====
  setCor(cor) { // valida se o atributo pode ter o valor digitado
    if (typeof cor !== "string" || cor.trim() === "") {
      console.log("Cor inválida");
      return;
    }
    this._cor = cor;
  }

  setNumero(numero) {
    if (typeof numero !== "number" || numero <= 0) {
      console.log("Número inválido");
      return;
    }
    this._numero = numero;
  }

  setValor(valor) {
    if (typeof valor !== "number" || valor <= 0) {
      console.log("Valor inválido");
      return;
    }
    this._valor = valor;
  }

  falarCor() { // metodo para falar a cor do carro
    console.log(`A cor do veículo é ${this._cor}`);
  }

  calcularImposto() { // metodo de imposto que será sobescrito com polimorfismo
    return this._valor * 0.1;
  }
}

// subclasse
class CarroEsportivo extends Veiculo {
  constructor(cor, numero, valor, potencia) {
    super(cor, numero, valor); //  IMPORTANTE
    this.setPotencia(potencia);
  }

  getPotencia() {
    return this._potencia;
  }

  setPotencia(potencia) {
    if (typeof potencia !== "number" || potencia <= 0) {
      console.log("Potência inválida");
      return;
    }
    this._potencia = potencia;
  }

  calcularImposto() { // sobescreve o metodo anterior de imposto
    return this._valor * 0.2;
  }
}



//  Teste
const carro1 = new CarroEsportivo("azul", 123, 100000, 500); // objeto

carro1.falarCor();
console.log("Imposto:", carro1.calcularImposto());

```
 ## perguntas sobre o texto
 
 1. Sempre que uso private eu sou obrigado a criar getters e setters?
 2. Qual a vantagem da versão com get e set em vez de métodos normais?
 3. Por que transformar atributos em private melhora o código?
 4. Isso é segurança real ou só organização do código?
 5. O texto diz que sem construtor pode dar problema — mas quando isso realmente acontece?
 6. Posso criar um objeto sem passar parâmetros?
 7. O construtor sempre precisa usar this?




