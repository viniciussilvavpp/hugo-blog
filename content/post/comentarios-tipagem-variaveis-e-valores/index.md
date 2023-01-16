---
title: JavaScript - Comentários, literals e tipagem
description: Aqui daremos os primeiros passos para começar a entender a composição dos códigos em JavaScript, começando pela declaração de comentários...
slug: javascript-comentarios-literals-tipagem
date: 2022-12-30 14:22:00+0000
image: banner.jpg
categories:
    - Programação
tags:
    - programacao
    - javascript
---

# Aprendendo o básico da linguagem #1  
  
Aqui daremos os primeiros passos para começar a entender a composição dos códigos em JavaScript, começando pela declaração de comentários porque fazer comentários nos códigos além de ser uma parte muito importante no aprendizado de qualquer linguagem, também é vital para a organização.
Após isso veremos os que são *literals* e como eles são categorizados por tipos e que, por sua vez, podem ser atribuídos como valores de variáveis. Nesse percurso, iremos com calma e se alguma coisa ficou confusa, abaixo será explicado com exemplos e ficará tudo certo.
  
## Fazer comentários no código JavaScript  
  
Os comentários em JavaScript podem ser feitos de duas formas: linha única ou múltiplas linhas. No primeiro caso basta adicionar duas barras (//) antes do texto do comentário, ficando como o exemplo abaixo:  
``` js  
// Este texto é um comentário de linha única  
// Por isso devo adicionar as duas barras em cada linha  
```  
Já no segundo, para ter múltiplas linhas comentadas, usa-se "/*" na abertura do comentário e "*/" para finalizar o comentário, ficando a seguinte forma:  
``` js  
/*  
Aqui estou abrindo o comentário de múltiplas linhas.  
E mesma essa sendo outra linha, não preciso usar nenhum símbolo, porque ainda não foi fechada.  
Aqui finalizo o comentário  
*/  
```  
Os comentários são especialmente úteis para explicar ou desativar determinado código.  
  
## O que são *literals* na programação?  
  
No mundo da programação um *literal* é um valor fixo declarado no código fonte na forma de texto ou número. O JavaScript, que é nosso objeto de estudo, apresenta alguns tipos de `literals`:  
- String literals: são sequência de caracteres declarados entre aspas simples ou aspas duplas.  
``` js  
'Olá mundo.'  
"E ae meu bom."  
```  
- Literals numéricos: são números inteiros ou com casa decimal como `20` ou `1.62`.  
- Literals booleanos: são valores que representam verdadeiro ou false, sendo definidos pelas palavras `true` e `false`.  
- Array literals: são listas de valores separados por vírgula e entre colchetes. Exemplo: `[1, 2, 3]`.  
- Literals de objetos: são conjuntos definidos por pares chave-valor colocados entre chaves. Exemplo: `{nome: 'Zezinho', idade: 18}`.  
  
Os *literals* são usados para definir valores sem precisar usar variáveis ou objetos para armazenar valor. Mas é importante lembrar que *literals* são valores fixos que não podem ser alterados depois de criados.  
  
## A Tipagem no JavaScript  
  
O JavaScript é considerada uma linguagem dinâmica de tipagem fraca. Isso quer dizer que as variáveis em JavaScript não estão associadas a nenhum valor específico, fazendo que elas possam receber qualquer tipo de dado e ter seu valor trocado independentemente do seu tipo. Nessa linguagem os tipos são definidos em duas categorias: tipos primitivos e tipos de objetos. 
Existem seis tipos primitivos definidos como **string, número, booleano, nulo, indefinido e símbolo** e três tipos de objetos: **Object, Array** e **Function**. 
Os três primeiros tipos primitivos já foram definidos onde fala sobre *String literals*, *Literals numéricos* e *Literals booleanos*, respectivamente. Agora vamos falar um pouco sobre o tipo nulo, indefinido e símbolo.  

### Tipos primitivos: nulo, indefinido e símbolo  
#### Tipo Nulo e Indefinido

O tipo nulo em JavaScript é apresentado pela palavra-chave **null** e ela quer dizer que há ausência de valor. Ao usar o operador `typeof`, você verá que dará a resposta como **objeto**. Isso quer dizer que o nulo pode ser interpretado como um objeto que possui o valor especial que indica "Nenhum objeto". Mas na prática a palavra-chave **null** é considerada como um membro único do seu próprio tipo para definir como "sem valor" para números, strings ou mesmo objetos.
``` js
console.log(typeof("Jose Ferreira"));   // => "name" retorna string
console.log(typeof(null));              // =>  null retorna objeto
```
Além disso, o JavaScript possui outra palavra para indicar ausência de valor, no entanto, de uma forma diferente, já que no lugar de indicar que não há valor, ele mostra que o valor está indefinido. Essa palavra é o **undefined**, que possui o papel de identificar quando uma variável não foi inicializada ou a propriedade de um objeto ou elemento de uma matriz não existem. Outro momento que o tipo indefinido pode aparecer é quando você executa uma função e não passa os valores esperados por ela.
Podemos usar o operador `typeof` novamente para vizualizar novamente.
``` js
let x;                    // => variável não inicializada
console.log(typeof(x));   // => retorna "undefined"
```
Normalmente muitos programadores evitam usar *null* e *undefined* nos seus códigos, já que essas palavras geralmente são associadas a erros ou algo imprevisto na execução do programa.

#### Símbolos

Os símbolos foram introduzidos na linguagem JavaScript na versão ES6 para servirem como nomes de propriedades não-strings. Para usar esse tipo basta usar a função `Symbol()`, e ela irá armazenar o valor da string passada como parâmetro, mas toda vez que for executaerda, a função não terá as mesmas propriedades de objeto. Por exemplo:
``` js
let strname = "sou uma string";            // declarando uma string
let symname = Symbol("sou um simbolo");    // declarando um símbolo
typeof strname;                            // => retorna "string"
typeof symname;                            // => retorna "Symbol"
```
Agora, se compararmos duas variáveis que recebem os mesmos símbolos com o operador de igualdade `==`, veremos que elas são diferentes.
``` js
let sym1 = Symbol("sou um simbolo");
let sym2 = Symbol("sou um simbolo");       
console.log(sym1 == sym2)                  // => retorna false
```
Dessa forma, se você usar os mesmos nomes de símbolos, você pode ter certeza de que outros pedaços de código no seu programa não sobrescreverá acidentalmente as propriedades de outro símbolo.

### Tipos de objetos: Object, Array e Function

Aqui seremos um pouco mais direto para definir o que é cada um deles porque serão mais detalhados em artigos individuais sobre cada um deles.
- **Object**: é um conjunto de pares chave-valor entre chaves que representam um coleção de dados.
- **Array**: um conjunto de valores ordenados especificados entre colchetes e separados por vírgula.
- **Function**: uma função pode ser definida como um conjunto de código que executa determinada tarefa.
Abaixo está um exemplo com cada um deles com suas estruturas.
``` js
console.log(typeof {name: "Toinho"}); // Saída: object 
console.log(typeof [1,2,3]);          // Saída: object 
console.log(typeof function() {});    // Saída: function
```
Para finalizar, você pode estranhar e se perguntar sobre o porquê do exemplo acima ter a saída do **array** como *object*. Na verdade isso está relacionado a forma que a linguagem JavaScript trata os dados, onde quase tudo é considerado um objeto e possuem propriedades de objetos. Isso será melhor tratado em outro post para não acabar prolongando demais. 

No próximo artigo já iremos dar uma olhada sobre como usar variáveis e valores atribuídos a elas. Nesse ponto já será possível criar alguns códigos e brincar um pouco para sair da parte teórica. Valeu e até a próxima.