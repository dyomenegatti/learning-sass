# **Sass**

As folhas de estilos foram crescendo e ficando mais complexas ao longo dos desenvolvimentos, dificultando a manutenção do código. Para resolver esse problema surgiu os **pré-processadores**.
* Programa para a construção de códigos CSS a partir de outra sintaxe semelhante ou quase idêntica ao CSS. 
* Permite adicionar funções que não são possíveis em CSS puro, como *mixins*, *nesting*, *seletores*, *herança*, etc.
* É possível usar a própria sintaxe CSS mas também pode escrever a folha de estilo com algumas particularidades, como não usar chaves e colocar elementos dentro um do outro, criando o *nesting*. Essas funções facilitam a manutenção e aumentam a legibilidade do CSS. 
As principais vantagens são:
* Aninhamento de código;
* Capacidade de usar variáveis;
* Capacidade de criar mixins;
* Capacidade de usar operações matemáticas/lógicas;
* Capacidade de usar loops e condições;
* Junção de vários arquivos;
Os principais pré-processadores são: **Sass, Less e Stylus**.

## **O QUE É SASS?**
*Syntactically Awesome Style Sheets* - *Folhas de Estilo Sintaticamente Impressionantes*.
* É uma ferramenta de software que cria arquivos CSS, quanto uma linguagem que adiciona recursos que não existem no CSS. 
* Vantagens:
  * Variáveis
  * Classes Aninhadas (facilitando a visualização da hierarquia)
  * Partial de arquivos (quebra de arquivos em diversos arquivos)
  * Importação
  * Mixins (reaproveitamento de estilos)
  * Operações matemáticas
* **Scss**
  * Extensão ```.scss```
  * Semelhante ao CSS, com *super poderes*
* **Sass**
  * Extensão ```.sass```
  * Suporta todos os recursos do SCSS
  * A sintaxe recuada era a sintaxe original do Sass
  * Usa espaço em vez de chaves e ponto e vírgula
* **Como o Sass funciona?**
  * Código sass -> traduz para o CSS -> navegador faz a leitura

## **CONCEITOS**

**Nesting**
* Ao invés de repetir os mesmos seletores, é possível criar uma regra de aninhamento, onde é combinado automaticamente o seletor da regra externa com o da regra interna.
```
  nav {
    ul {
      margin: 0;
      padding: 0;
      list-style: none;
    }
  }
```
* É possível lidar com lista de seletores(seletores separados por vírgula).
```
  .alert, .warning {
    ul, p {
      padding-bottom: 0;
    }
  }
```
* Também é possível combinar seletores; coloca o combinador no final do seletor externo, no ínicio do seletor interno ou até mesmo sozinho entre os dois.
```
  ul > {
    li {
      list-style-type: none;
    }
  }
```

**Parent**
* É possível usar seletores de forma mais complexo, como o seletor pai, &, é um seletor especial inventado pelo Sass, usado para adicionar pseudoclasse ou adicionar um seletor antes do pai. 
```
  .alert {
    margin-left: 0;
    &:hover {
      font-weight: bold;
    }
  }
```
* É possível usar o seletor pai para adiciona sufixos extrras ao seletor externo. 
```
  .accordion {
    max-width: 600px;
    &__copy {
      display: none;
    }
  }
```

**Interpolation**
* A interpolação serve para injetar valores de expressões como variáveis e chamadas de função em seus seletores. Isso é particularmente útil quando está utilizando mixins, pois permite criar seletores a partir de parâmetros que os usuários passam. 
```
  @mixin define-emoji($name, $glyph) {
    span.emoji-#{$name} {
      font-family: IconFont;
      font-variant: normal;
      font-weight: normal;
      content: $glyph;
    }
  }

  @include define-emoji("women-holding-hands", "👭");
```

**Variáveis**
* É possível criar variáveis para guardar principalmente cores, fontes, e o que for necessário.
* As variáveis suportam o conceito de escopo.

**Mixins**
* É um bloco de código projetado para executar uma tarefa específica e pode conter uma ou mais instruções, tornando o código mais fácil para manter, editar e modificar.
* Um mixin deve possui um nome, da mesma forma que uma variável ou uma função, os mixins precisam de um nome para ter uma referência e poderem ser chamados quando forem utilizados.
* Para utilizar um mixin é preciso da At Rule @include, e do nome do mixin que foi atribuído na criação.

**Palavras reservadas**
* ```@use```: Carrega mixins, functions e variáveis de outras folhas de estilos Sass e combina o CSS de diversas folhas de estilo juntos.
* ```@forward```: Carrega uma folha de estilo Sass e torna os mixis, functions e variáveis disponíveis quando a folha de estilo é carregada pela regra do ```@use```.
* ```@import```: Estende as regras de CSS para carregar styles, functions e variáveis de outras folhas de estilo
* ```@mixins``` e ```@include``` - facilitam a reutilização de trechos de código.
* ```@function```: Define funções customizadas que podem ser utilizadas em expressões.
* ```@extend```: Permite que os seletores herdem estilos uns dos outros.
* ```@at-root```: Coloca estilos dentro dele na raiz do documento CSS.
* ```@error```: Faz com que a compilação falhe com uma mensagem de erro.
* ```@warn```: Imprime um aviso sem parar totalmente a compilação.
* ```@debug```: Imprime uma mensagem para fins de debuggin.

**Import**
* A importação é um processo pelo qual muitos arquivos são transformados em poucos arquivvos. O Sass tem um pequeno truque pelo qual as folhas de estilo menores são importadas para a maior à medida que ela é compilada em CSS. 
* Ao digitar ```@import```, seguido pelo nome do arquivo Sass que deseja importar, você pode misturar arquivos Sass e Scss à vontade com importações. 
```
  @import "nome_do_arquivo";
```
* Por padrão, o compilador Sass gera um arquivo CSS de todos os seus arquivos .scss - para isso não ocorrer, deve iniciar o nome do arquivo .scss com um underline.

**If/Else**
Assim como em linguagens de programação, o sass possui as condicionais if e else

**@if**
* O padrão de escrita é ```@if <expression> { ... }```, que controla se seu bloco é avaliado ou não (incluindo a emissão de qualquer estilo como CSS). A expressão geralmente retorna true ou false - se a expressão retornar true, o bloco será executado e, se a expressão retornar false, não será executado. 

**@else**
* Já no caso do else, escrita é ```@else { ... }```. O bloco desta regra é avaliado se a @if retornar falso. 

