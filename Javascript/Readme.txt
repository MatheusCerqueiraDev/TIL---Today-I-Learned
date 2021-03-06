PT-BR
Classes

Classes em JavaScript são introduzidas no ECMAScript 2015 e são simplificações da linguagem para as heranças.
Classes em JavaScript provêm uma maneira mais simples e clara de criar objetos e lidar com herança.

----------------------------------------------------------------------
PT-BR
Uso antes da declaração (Hoisting - Lançamento)

Uma diferença importante entre declarações de funções das declarações de classes, é que  declararações de  funções são hoisted e declarações de classes não são. Primeiramente deve declarar sua classe para só então acessá-la, pois do contrário o código a seguir irá lançar uma exceção: ReferenceError:

const p = new Retangulo(); // Erro de referência (ReferenceError)

class Retangulo {}

----------------------------------------------------------------------
PT-BR
Expressões de Classes

Uma Expressão de Classe (class expression) é outra forma para definir classes. Expressões de Classes podem possuir nomes ou não (anônimas). O nome dado para uma expressão de classe é local ao corpo da classe.

// sem nome
let Retangulo = class {
  constructor(altura, largura) {
    this.altura = altura;
    this.largura = largura;
  }
};

// nomeada
let Retangulo = class Retangulo {
  constructor(altura, largura) {
    this.altura = altura;
    this.largura = largura;
  }
};
Nota: As expressões de classe também sofrem com o mesmo problema de hoisted mencionados em declarações de classe.

----------------------------------------------------------------------
PT-BR
Corpo de uma classe e definições de métodos

O corpo de uma classe é a parte que está entre chaves {}. É aí onde você define os membros da classe, como os métodos, ou os construtores.

Modo Estrito (strict mode)
Os corpos das Declarações de Classes e das Expressões de Classes são executados em modo estrito.

Construtor
O método constructor é um tipo especial de método para criar e iniciar um objeto criado pela classe. Só pode existir um método especial com o nome "constructor" dentro da classe. Um erro de sintáxe SyntaxError será lançado se a classe possui mais do que uma ocorrência do método constructor.

Um construtor pode usar a palavra-chave super para chamar o construtor de uma classe pai.

Métodos Protótipos
Veja também definições de métodos (method definitions).

class Retangulo {
    constructor(altura, largura) {
      this.altura = altura; this.largura = largura;
    }
  //Getter
    get area() {
        return this.calculaArea()
    }

    calculaArea() {
        return this.altura * this.largura;
    }
}

const quadrado = new Retangulo(10, 10);

console.log(quadrado.area);

Métodos estáticos
A palavra-chave static define um método estático de uma classe. Métodos estáticos são chamados sem a instanciação da sua classe e não podem ser chamados quando a classe é instanciada. Métodos estáticos são geralmente usados para criar funções de utilidades por uma aplicação.

class Ponto {
    constructor(x, y) {
        this.x = x;
        this.y = y;
    }

    static distancia(a, b) {
        const dx = a.x - b.x;
        const dy = a.y - b.y;

        return Math.hypot(dx, dy);
        //A função Math.hypot() retorna a raiz quadrada do somátorio do quadrado de seus parâmetros
    }
}

const p1 = new Ponto(5, 5);
const p2 = new Ponto(10, 10);

p1.distancia; //undefined
p2.distancia; //undefined

console.log(Ponto.distancia(p1, p2));

----------------------------------------------------------------------
PT-BR
Empacotando com protótipos e métodos estáticos

Quando um método estático ou protótipo é chamado sem um objeto "this" configurado (ou com "this" como boolean, string, number, undefined ou null), então o valor "this" será undefined dentro da função chamada. Autoboxing não vai acontecer. O comportamento será o mesmo mesmo se escrevemos o código no modo não-estrito.

class Animal {
  falar() {
    return this;
  }
  static comer() {
    return this;
  }
}

let obj = new Animal();
obj.falar(); // Animal {}
let falar = obj.falar;
falar(); // undefined

Animal.comer(); // class Animal
let comer = Animal.comer;
comer(); // undefined
Copy to Clipboard
Se escrevemos o código acima usando classes baseadas em função tradicional, então o autoboxing acontecerá com base no valor de "this" para o qual a função foi chamada.

function Animal() { }

Animal.prototype.falar = function() {
  return this;
}

Animal.comer = function() {
  return this;
}

let obj = new Animal();
let falar = obj.falar;
falar(); // objeto global

let comer = Animal.comer;
comer(); // objeto global

----------------------------------------------------------------------
PT-BR
Formas de Output

1° Manipulação por id
Dado id a um elemento HTML é possível alterar seu valor usando:
document.getElementById('id do elemento').innerHTML = " valor";

2° Criação de texto
Esse método só funciona no primeiro carregamento da página:
document.write("Algo");

Caso inserido pelo console após o primeiro carregamento, o resto da aplicação será substituido.

3°POP-UP
A criação de um POP-UP é feita atráves de:

window.alert("texto");

4°Mensagem no CONSOLE
O comando mais conhecido:

console.log("Mensagem");

----------------------------------------------------------------------
PT-BR
O que é o DOM(Document Object Model)

O DOM (Document Object Model) é usado para manipulação e atualização em tela pelo
JavaScript, já o Virtual DOM (VDOM) é a representação do DOM mantida em memória, o
VDOM é mais rápido que o DOM, nela é mantida uma cópia de todo código e através de
um método chamado reconciliação são alterados/atualizados somente os elementos
modificados gerando uma UX melhor.

Podemos usar a palavra reservada (document) para selecionarmos elementos em tela.

Selecionando Elementos |

Tendo um elemento que tenha um (id) podemos utilizar o DOM para selecionarmos o mesmo:

document.getElementById("id do elemento")
Dessa forma estamos somente selecionando o elemento 

Podemos alterar seu valor com 

document.getElementById("id do elemento").innerHTML = "o que você quer por"
O que será inserido é de sua escolha, HTML, Striongs e etc.

Selecionando Elementos ||

Agora vamos ver como selecionar um elemento através da classe do elemento:

document.getElementsByClassName("class do elemento")

O motivo de que o getElementsByClassName está no plural é por causa que podemos ter vários
elementos com a mesma class enquanto só podemos ter um id no escópo 

Caso exista a class selecionada em mais de um elemento, podemos selecionar qual
 dos elementos selecionar adicionando [] ao final:

document.getElementsByClassName("class do elemento")[posição do elemento]

Passado a posição do elemento podemos alterar ele:

document.getElementsByClassName("class do elemento")[0].innerHTMl = alteração;

Selecionando Elementos |||

Também podemos selecionar tags através do DOM:

document.getElementsByTagName("tag")

Também podemosfazer as alterações nesse tipo de seleção

Selecionando Elementos ||||

E por último mas não menos importante, podemos selecionar um elemento por seu nome:

document.getElementsByName("nome do elemento");

----------------------------------------------------------------------
PT-BR

Queryselector

Com o mesmo funcionamento do seletor de classes/ids o querselector serve para selecionarmos 
elementos, classes. ids ou nome de elementos.

Mas diferente dos seletores passados, usamos outro metódo para buscar nossos elementos:

Como no CSS, chamamos ID's com #
document.querySelector("#id") -> retorna o elemento com o id inserido
para alterarmos valores:
document.querySelector("#id").innerHTML = valor a ser atribuido;

Para classes:
document.querySelector(".class") -> retorna o primeiro elemento com essa class com
para alterarmos valores:
document.querySelector(".class").innerHTML = valor a ser atribuido;

Tags:
document.querySelector("tag")
para alterarmos valores:
document.querySelector("tag").innerHTML = valor a ser atribuido;

Como dito, o querySelector retorna somente o primeiro class inserido
Para chamarmos todos os itens daquela class usamos:

document.querySelectorAll(".class") -> retorna todos elementos com aquela class

----------------------------------------------------------------------
PT-BR

Scroll Behavior

Para criarmos uma rolagem suave pela tela, subir a tela de modo suave usamos:

document.scroolY(0) -> para rolarmos verticalmente para o inicio da página.
document.scroolX(0) -> para rolarmos horizontalmente para o início da página.

Agora quando queremos rolar um elemento para seu início usamos junto o querySelector:

document.querSelector('text').scrollTop(0) -> para rolamento vertical
document.querSelector('text').scrollLeft(0) -> para rolamento horizontal

Agora para um rolamento suave da página criamos uma função onde passamos seu "comportamento":

function subirATelaSuave(){
  document.scroolTo({
    top: 0,
    behavior: smooth,
  })
}

O parametro "behavior: smooth" indica que o rolamento será feito de forma suave.