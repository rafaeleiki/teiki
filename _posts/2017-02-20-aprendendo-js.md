---
layout: post
title:  "Aprendendo JavaScript"
date:   2017-02-20 11:04:05 -0300
tags:
- javascript
---
Nesse post eu vou falar um pouco mais sobre JavaScript. Essa é uma linguagem que 
está em alta e está sendo usada para diferentes tipos de desenvolvimento 
(back-end, front-end, mobile). Existem diversos frameworks excelentes que usam JavaScript,
como o React, React Native, AngularJS e Node.js, mas para entender qualquer um deles
você precisa entender o básico da linguagem. Esse JavaScript "puro" também é conhecido
como Vanilla JS.

## Introdução

O JavaScript é uma linguagem interpretada sem tipagem forte. Isso significa que 
**você não define os tipos das variáveis explicitamente**.
Para esse tutorial, vamos usar o ambiente mais comum de uso
do JS: o browser. Os navegadores permitem que você execute os
scripts nessa linguagem pelo console. No Google Chrome você pode acessá-lo
pelo atalho `Ctrl + Shift + J`.

**Obs:** O JavaScript falado aqui **não é o mais atual**. Nem todos os
browsers aceitam as versões mais novas do JS, então é bom você saber
em que ambientes pode usá-lo ou não.

## Tipos

Vamos criar a clássica função "Hello World".

{% highlight javascript %}
function helloWorld() {
    console.log("Hello World!");
}
helloWorld();
// => Hello World!
{% endhighlight %}

Vamos agora criar uma função simples que some 2 números. Note
que a sintaxe para criar uma função pode variar.

{% highlight javascript %}
var somar = function(x, y) {
    return x + y;
}
somar(1, 4.5);
// => 5.5
{% endhighlight %}

Ao criar uma função como no primeiro exemplo, você está criando uma 
variável com o nome da função e fazendo o valor dela ser a função. Assim,
o exemplo a seguir é válido (apesar de não fazer muito sentido):

{% highlight javascript %}
function helloWorld() {
    console.log("Hello World!");
}
helloWorld();
// => Hello World!

helloWorld = function() {
    return 2;
}
helloWorld();
// => 2
{% endhighlight %}

Outro fator interessante da linguagem é que ela permite você acessar
os parâmetros da função como se fosse um array. Para isso, use o `arguments`.

{% highlight javascript %}
function somar() {
    var somatoria = 0;
    for (var index = 0; index < arguments.length; index++) {
        somatoria += arguments[index];
    }
    return somatoria;
}
somar(1, 2, 3, 4, 5, 6);
// => 21
{% endhighlight %}

Alguns dos tipos básicos comuns em outras linguagens também são
definidos em JS, como por exemplo, números, strings e booleans.
Além disso, no JS é muito fácil definir um objeto, que funciona
como um dicionário (série de pares chave-valor). Os objetos em JavaScript
são importantes pois são a definição de JSON (JavaScript Object Notation).

{% highlight javascript %}
var objetoVazio = {}; // Objeto vazio
var geladeira = {
    ovos: 6,
    caixasDeLeite: 1,
    tomates: 2
};
console.log(geladeira.ovos); // => 6
console.log(geladeira["caixasDeLeite"]); // => 1

var oQueEuQuero = 'tomates';
console.log(geladeira[oQueEuQuero]); // => 2
{% endhighlight %}

Outro tipo importante para a programação são os vetores. No JavaScript, os vetores não
possuem tamanho fixo e possuem alguns métodos.

{% highlight javascript %}
var vetor = []; // vetor vazio
var numeros = [1, 2, 3];
var aleatorio = ['abacaxi', 42, null];

console.log(numeros.length); // => 3
console.log(aleatorio[0]); // => abacaxi

// Coloca um elemento na última posição do vetor
vetor.push(10);
console.log(vetor.length); // => 1

// Remove o último elemento do vetor e o retorna
console.log(vetor.pop()); // => 10
console.log(vetor.length); // => 0
{% endhighlight %}

Veja mais sobre tipos nesses links:
<a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array" target="_blank">
    arrays (vetores)
</a>,
<a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Trabalhando_com_Objetos" target="_blank">
    objetos
</a>.

## Classes

O JS possui o conceito de classe a partir da versão ECMAScript 2015.
Antes disso, para se ter o equivalente a "classe" é usada uma função.

{% highlight javascript %}
function Automovel(rodas) {
    this.rodas = rodas;
    this.kmRodados = 0;
}

Automovel.prototype = {
    andar: function(km) {
        this.kmRodados += km;
    }
};

var carro = new Automovel(4);
carro.andar(15);
console.log(carro.kmRodados); // => 15
{% endhighlight %}

O JavaScript usa a Orientação a Protótipos ao invés da
Orientação a Objetos tradicional. As instâncias de uma "classe" do JS
são objetos que possuem a propriedade "prototype". Quando uma chamada de 
função ou procura de um atributo é feito em uma instância, caso ela
não o encontre, o atributo é procurado no "prototype" dela, e assim por 
diante. 

Como a orientação a objetos não é definida como em linguagens como
Java e C#, é necessário "gambiarras" para se ter o mesmo efeito
em JS. Ao contrário do que outras linguagens fazem, em que uma classe
herda da outra, aqui, uma instância herda da outra. Esse exemplo
é uma das formas de se ter herança no JavaScript:

{% highlight javascript %}
function Automovel(rodas) { ... }
function Moto() {
    // Chama o construtor de Automovel
    // passando 2 como parâmetro
    Automovel.call(this, 2);
}
Moto.prototype = new Automovel(); 
Moto.prototype.constructor = Moto;

var moto = new Moto();
moto.rodas; // => 2

moto.andar(45);
moto.kmRodados; // => 45
{% endhighlight %}

Em geral, esse tipo de padrão de herança não vai ser necessário
quando o JS for usado em conjunto com outras bibliotecas / frameworks
ou se a versão do JS for igual ou superior ao ECMAScript 2015.

Para saber mais sobre a orientação a protótipos do JS,
<a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype" target="_blank">
    clique aqui
</a>.

## Escopo
Uma das coisas que pode causar mais dor de cabeça em programadores de
JS é o funcionamento do escopo. Os pedaços de código de JavaScript
sempre estão ligados a um escopo, que no caso sempre é definido por uma função.
Cada variável é sempre declarada no início do escopo, e isso pode levar a 
alguns resultados inesperados.

{% highlight javascript %}
var index = 2;

function teste() {
    if (index >= 2) {
        var index = 1;
    }
    return index;
}
teste(); // => undefined
{% endhighlight %}

Isso ocorreu porque **toda vez que aparece uma declaração de variável**,
ela é passada para o início do escopo. Assim, esse código é equivalente a:

{% highlight javascript %}
var index;
var teste;

index = 2;
teste = function() {
    var index;
    if (index >= 2) { // sempre é undefined, nunca entra no if
        index = 1;
    }
    return index;
}
{% endhighlight %}

Outro detalhe importante é que, nesse caso, `index` e `teste` são variáveis
globais. É sempre bom evitá-las para manter o código organizado, então
para usá-las num pedaço de código, é possível isolá-las usando uma função
imediata.

{% highlight javascript %}
(function() {
    // As duas variáveis só ficam disponíveis dentro dessa função
    var index = 2;
    function teste() { ... }
    ...
})(); // A função é criada e já executada

index; // => ReferenceError: index is not defined
{% endhighlight %}