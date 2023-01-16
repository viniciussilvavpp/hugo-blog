---
title: JavaScript - Variáveis e valores
description: Uma das partes mais fundamentais de qualquer linguagem de programação é usar nomes, que também são chamados de identificadores...
slug: javascript-variaveis-e-valores
date: 2023-01-02 12:34:00+0000
image: banner.jpg
categories:
    - Programação
tags:
    - programacao
    - javascript
---

# JavaScript - Variáveis e seus valores
## Como declarar variável no JavaScript

Uma das partes mais fundamentais de qualquer linguagem de programação é usar nomes, que também são chamados de identificadores, para assumir algum valor. Usar um nome associado a algum valor permite que o programador tenha acesso ao valor pelo nome dado. Quando isso é feito, chama-se o identificador de **variável**. O termo variável também indica que novos valores podem ser associados àquele identificador enquanto o programa é executado. Se você quiser que uma variável assuma o mesmo valor sempre que chamada, então é declarado como uma **constante**.

Antes de usar uma variável você precisa *declarar* ela. Para isso, a partir da versão ES6, usa-se as palavras-chave `let` e `const`, onde a primeira se trata de uma variável comum e a segunda empregada para representar constantes. 
``` js
let x;                   // declara a variável "x"
let k, l, m;             // é possível declarar mais de uma variável em uma linha
const meunome = 0;       // declara a constante "meunome"
```
É considerado uma boa prática de programação associar algum valor inicial ao declarar uma variável, mas é **obrigatório** para constantes, porque se declarar uma constante e não atribuir um valor, gerará um erro.  Esse processo é também conhecido como a inicialização da variável. Faça isso sempre que possível.
``` js
let k = 0, l = 0, m = 0;
const meunome = "JoaozinPVP";
```
Quando não é especificado um valor para a variável usando o `let`, ela assumirá o valor *undefined* até que algum valor seja associado a ela e as constantes sempre manterão o valor indicado na declaração, por isso é necessário indicar o valor nesse momento.

Você pode ver também que em muitos códigos as **constantes** apresentam o nome todo escrito em letra maiúscula. Isso é apenas uma convenção usada como forma de identificar mais facilmente o que são variáveis e constantes no código. Não é uma lei, mas é uma forma de organizar o código.
``` js
const PI = 3.14;
const GRAVITY = 9.81;
```

## Escopo de Variáveis e Constantes

O escopo das variáveis é a parte do programa que determina onde as variáveis são definidas. Variáveis e constantes funcionam como tendo escopo por bloco, onde elas só apresentam valores dentro do contexto em que são definidas. No JavaScript, um arquivo é um bloco, as classes e funções (detalhadas futuramente) funcionam como blocos, assim como instruções de condição *if/else*, laços de repetição (*for, while*) e assim por diante também são bloco.
``` js
function bhaskara(a, b, c) {               // variáveis "x1", "x2" e "delta"
	let x1 = 0, x2 = 0, delta = 0;         // com escopo limitado por uma função
	
	delta = b**2 - 4*a*c;
	x1 = ((-b) + Math.sqrt(delta)) / (2*a);
	x2 = ((-b) - Math.sqrt(delta)) / (2*a);
	
	return console.log("Valor de x' é " + x1 + " e x'' é " + x2);
};

let myName = "Manoel Gomes";
for (let i = 0; i < myName.length; i++) {       // variável "element" com escopo limitado
    let element = array[i];                     // por laço de repetição
};
```
Em resumo, pode-se dizer que se uma variável ou constante é declarada dentro de um conjunto de chaves, as chaves são o que limitam seu escopo, fazendo com que fora das chaves ela não tenha definição. E em casos que são declaradas como parte de um *for, for/in, for/of* o corpo do laço de repetição é seu escopo.

Além disso, quando um variável ou constante é declarada fora de qualquer estrutura de bloco, ela é chamada de **variável global** ou **constante de escopo global**. Isso implica que esse elemento pode ser acessado em todo o arquivo que está contido.

## Declarações repetidas

Um caso que mostra bem como o escopo da variável ou constante faz diferença na execução do código é usar o mesmo nome da variável em escopos diferentes. Isso é possível porque no JavaScript os valores são definidos de acordo apenas no escopo em que as variáveis/constantes se encontram.
``` js
const x = 4;
if (x === 4) {
	let x = 5;
	console.log(x);      // Exibe "5"
}
console.log(x);          // Exibe "4"
let x = 8;               // Erro de sintaxe ao tentar redeclarar "x"
```

## Declaração de variável usando *var*

Em versões anteriores à ES6, a única forma de declarar uma variável no JavaScript era usando a palavra-chave `var`. Mesmo ela tendo comportamento geralmente comparado com `let`, elas funcionam de formas diferentes.
``` js
var x;
var data = [], tamanho = data.length;
for (var i = 0; i < tamanho; i++) { console.log(data[i]); }
```
Como podemos ver no código acima, a declaração usando `var` e `let` é indêntico, mas agora vamos ver como elas funcionam de formas diferentes.
- Variáveis declaradas usando `var` não obedecem o escopo por blocos. Ao invés disso, elas sempre se apresentam no topo do escopo da função que está contida, não importando se está dentro de estruturas de repetição ou condicionais.
- Se usar a declaração `var` fora de funções, ela se torna uma variável global. Até aqui nada de diferente da declaração por `let`. Mas, a forma que `var` assume a posição de variável global, elas são implementadas como propriedades do objeto global e os declarados por `let` e `const` não. No que isso implica? Quer dizer que variáveis declaradas com `var` não podem deletadas do objeto global, sempre ocupando aquele espaço.
- Diferentemente de variáveis declaradas com `let`, é possível declarar a mesma variáveis várias vezes usando `var`. Isso é acontece porque elas ela obedecem o escopo por função e não por bloco.
- Por último, uma das coisas mais diferentes que acontece ao usar a declaração com `var` é conhecido como *hoisting*. Acontece que quando a variável é declarada com `var` ela é definida no topo da função que pertence, mesmo que a iniciliazação seja feita onde você escreveu, mas a definição da variável ocorre no topo da função. Assim, a variável declarada com `var` pode ser colocada em qualquer posição dentro da função sem retornar erros, onde pode existir o emprego dela em linhas anteriores à declaração. Isso pode resultar em diversos bugs, sem falar sobre o aspecto de desorganização do código. Com isso, o uso do `let` é preferível atualmente, pois ele previne que a variável seja usada antes de ser definida e obedece o escopo por blocos.