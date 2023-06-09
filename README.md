# Cheerio
Documentação Web Scraping com Cheerio e Axios para iniciantes criada com GPT.

# Capítulo 1 - Introdução

Sejam bem-vindos a nossa documentação sobre Web Scraping com Cheerio e Axios para iniciantes!

## Sobre o Cheerio e seu propósito

Cheerio é uma biblioteca JavaScript para manipulação de dados HTML e XML. O principal objetivo do Cheerio é simplificar a seleção e manipulação de dados em documentos HTML e XML.

Em outras palavras, o Cheerio permite que você facilmente acesse e manipule dados em páginas da web, de uma forma muito mais simples e intuitiva do que se estivesse fazendo sem nenhuma biblioteca.

## As vantagens do uso do Cheerio para web scraping

O Cheerio é uma biblioteca leve que faz uso do jQuery, tornando a sintaxe de seleção de elementos muito mais fácil e intuitiva. Além disso, ela é muito eficiente e rápida na seleção e manipulação de dados, o que é essencial para web scraping.

Web scraping é o processo de coletar informações de páginas da web de forma automatizada. O Cheerio é uma ótima biblioteca para web scraping por ser fácil de usar e permitir a manipulação dos dados coletados de forma ágil e precisa.

## Configuração inicial do ambiente de desenvolvimento

Para utilizar o Cheerio, é necessário ter o Node.js instalado em sua máquina. Você pode baixá-lo gratuitamente em https://nodejs.org/.

Após baixar o Node.js, é possível instalar o Cheerio utilizando o npm, que já vem com o Node.js. Para isso, abra o terminal ou prompt de comando e digite:

```
npm install cheerio
```

Além do Cheerio, também utilizaremos o Axios, uma biblioteca de requisições HTTP para o Node.js. Para instalá-lo, emita o comando:

```
npm install axios
```

Pronto! Com o Node.js, Cheerio e Axios instalados em sua máquina, você está pronto para começar a utilizar a biblioteca para web scraping.
# Capítulo 2 – Conceitos básicos de HTML

Neste capítulo, iremos apresentar conceitos básicos de HTML e como eles são importantes para entender como o Cheerio funciona.

## Entendendo a estrutura do HTML

HTML (Hypertext Markup Language) é a linguagem de marcação utilizada para estruturar conteúdos e informações em uma página da web. É a partir do HTML que os navegadores da internet interpretam como a página deve ser exibida em nossa tela.

O HTML é composto por elementos, que são utilizados para estruturar o conteúdo da página. Os elementos são definidos por tags, que são delimitadas por “< >”, como a tag ```<html>```. Alguns exemplos de outras tags são ```<head>```, ```<title>```, ```<body>```, ```<p>``` e ```<img>```. 

## HTML vs. DOM

É importante notar que há uma diferença entre código HTML e árvore DOM. O DOM (Document Object Model) é a representação da estrutura HTML em forma de árvore. Cada elemento HTML é um nó dessa árvore, onde cada nó tem seus próprios atributos, filhos e pais.

Quando acessamos uma página da web, o navegador lê o código HTML e o converte em uma árvore DOM. Cada elemento HTML se torna um nó da árvore, que pode ser acessado e manipulado pelos desenvolvedores através de APIs JavaScript.

## Diferentes tipos de elementos HTML

Como mencionado anteriormente, existem muitos tipos de elementos HTML. Alguns elementos são utilizados para estruturar o conteúdo da página, como ```<div>```, ```<ul>``` e ```<li>```, enquanto outros são utilizados para inserção de mídias, tais como ```<img>```, ```<audio>``` e ```<video>```. 

Cada elemento HTML tem suas próprias propriedades e atributos, que determinam como o elemento será exibido na página.

Compreender a estrutura de uma página da web e os diferentes tipos de elementos HTML é crucial para o web scraping em geral e para o uso do Cheerio em particular.
# Capítulo 3 – Selecionando elementos com Cheerio

Neste capítulo, iremos aprender como selecionar elementos em uma página da web usando o Cheerio. 

## Instalando o Cheerio

Antes de começarmos, é necessário instalar o Cheerio. O Cheerio é um pacote do Node.js, portanto, é necessário ter o Node.js instalado em seu computador.

Para instalar o Cheerio, abra o terminal e digite o seguinte comando:

```
npm install cheerio
```

## Carregando o HTML com Cheerio

Uma vez que o Cheerio foi instalado, podemos começar a usá-lo para selecionar elementos em uma página da web.

Para carregar o HTML, primeiro precisamos fazer uma requisição HTTP para a página que queremos acessar. Há muitas bibliotecas disponíveis em JavaScript para essa tarefa, mas para esse exemplo, vamos usar o axios. Para instalar o axios, basta digitar o seguinte comando:

```
npm install axios
```

Com o axios instalado, podemos fazer uma chamada HTTP para uma página HTML e carregar o conteúdo usando o Cheerio:

```javascript
const axios = require('axios');
const cheerio = require('cheerio');

axios.get('https://www.google.com/')
  .then(response => {
    const $ = cheerio.load(response.data);
    // aqui faremos a seleção dos elementos
  })
  .catch(error => {
    console.log(error);
  });
```

Acima, fazemos uma requisição GET para o site do Google e carregamos a resposta no Cheerio.

## Selecionando por tags e classes

Usando o Cheerio, podemos selecionar elementos do HTML de diferentes maneiras. Por exemplo, podemos selecionar por tags utilizando o símbolo ```< >```. 

Por exemplo, para selecionar todos os elementos ```<a>``` da página, podemos fazer o seguinte:

```javascript
const links = $('a');
```

Também podemos selecionar elementos por classe usando o sinal ```.```. Por exemplo, para selecionar todos os elementos que têm a classe "my-class", podemos fazer:

```javascript
const elements = $('.my-class');
```

## Selecionando por ID e atributos

Podemos selecionar elementos por ID usando o sinal ```#```. Por exemplo, se quisermos selecionar um elemento com o ID "my-id", podemos fazer o seguinte:

```javascript
const element = $('#my-id');
```

Além disso, podemos selecionar elementos por outros atributos. Por exemplo, para selecionar todos os elementos que têm o atributo "src", podemos fazer:

```javascript
const elements = $('[src]');
```

Também podemos selecionar elementos que têm um atributo específico. Por exemplo, para selecionar todos os elementos que têm o atributo "href" com valor "https://exemplo.com", podemos fazer:

```javascript
const elements = $('[href="https://exemplo.com"]');
```

Aqui estão algumas maneiras comuns de selecionar elementos usando o Cheerio. Com essas ferramentas, podemos começar a extrair informações de uma página da web para uso posterior.
# Capítulo 4 - Utilizando Seletores CSS com Cheerio

Neste capítulo, vamos aprender como utilizar seletores CSS em conjunto com Cheerio para selecionar elementos em uma página da Web.

## Entendendo seletores CSS

Seletor CSS é uma forma de selecionar elementos HTML com base em seus estilos e atributos. Existem vários tipos de seletores CSS, mas aqui estão alguns dos mais comuns:

* Seletor de tag: seleciona elementos com base em sua tag HTML. Exemplo: `p` selecionará todos os parágrafos na página.
* Seletor de classe: seleciona elementos com base em seu nome de classe. Exemplo: `.exemplo` selecionará todos os elementos que possuem a classe "exemplo".
* Seletor de ID: seleciona um elemento com base em seu ID único. Exemplo: `#unico` selecionará o elemento com ID "unico".
* Seletor de atributo: seleciona elementos com base em seus atributos HTML. Exemplo: `[src]` selecionará todos os elementos que possuem o atributo "src".

Os seletores CSS também podem ser combinados para criar seletores mais específicos. Por exemplo, `.exemplo p` selecionará todos os parágrafos dentro de elementos com classe "exemplo".

## Utilizando seletores CSS em Cheerio

Agora que entendemos os seletores CSS, podemos usá-los com o Cheerio para selecionar elementos em uma página da Web.

Para selecionar elementos usando um seletor CSS, usa-se o método `$()` seguido do seletor CSS que você deseja utilizar. Por exemplo, para selecionar todos os elementos de parágrafo na página, basta fazer o seguinte:

```javascript
const cheerio = require('cheerio');
const html = '<html><body><p>Parágrafo 1</p><p>Parágrafo 2</p></body></html>';

const $ = cheerio.load(html);

const paragrafos = $('p');
```

O código acima cria um objeto Cheerio a partir do HTML e seleciona todos os elementos `<p>` usando o seletor de tag CSS `p`.

## Combinando seletores

Como mencionado anteriormente, você pode combinar seletores CSS para criar seletores mais específicos. Por exemplo, se quisermos selecionar o parágrafo dentro de um elemento com classe "exemplo", podemos fazer o seguinte:

```javascript
const paragrafo = $('.exemplo p');
```

Isso selecionaria todos os elementos de parágrafo dentro de um elemento com a classe "exemplo".

Também é possível navegar pelo DOM, usando seletores CSS para alcançar elementos de outras formas. Por exemplo, supondo que tenhamos um HTML similar ao seguinte:

```html
<div>
  <p>Parágrafo 1</p>
  <p id="unico">Parágrafo 2</p>
</div>
```

Podemos usar o seletor CSS `"#unico"` para selecionar o elemento `<p>` com o ID "unico". Mas, também podemos navegar pelo DOM a partir desse elemento, selecionando outros elementos como seus irmãos, pais ou filhos.

```javascript
const $ = cheerio.load(html);

const paragrafoUnico = $('#unico');
const paragrafoIrmao = $('#unico').next();
const divPai = $('#unico').parent();
```

O método `next()` seleciona o próximo elemento após o elemento selecionado. Nesse caso, `next()` selecionaria o segundo parágrafo.

O método `parent()` retorna o elemento pai do elemento selecionado. Nesse caso, `parent()` selecionaria o elemento da div.

Esses são alguns exemplos de como podemos combinar os seletores CSS com Cheerio para navegar pelos elementos de uma página da Web. Com essas ferramentas, podemos extrair as informações que precisamos para nosso projeto de Web Scraping.
# Capítulo 5 - Manipulando Elementos com Cheerio

Neste capítulo, vamos aprender a manipular elementos de uma página da Web usando Cheerio. Para isso, utilizaremos os seletores de CSS e as funções do Cheerio para adicionar, remover e modificar elementos.

## Adicionando, removendo e modificando elementos

Para adicionar um novo elemento a uma página da Web, podemos usar o método `$().append()` do Cheerio. Este método adiciona um novo elemento ao final do elemento selecionado.

Por exemplo, se quisermos adicionar um novo parágrafo ao final do body de uma página, podemos fazer o seguinte:

```javascript
const cheerio = require('cheerio');
const html = '<html><body><p>Parágrafo 1</p><p>Parágrafo 2</p></body></html>';

const $ = cheerio.load(html);

$('body').append('<p>Parágrafo 3</p>');
```

O código acima adiciona um novo parágrafo `<p>Parágrafo 3</p>` ao final do body da página.

Para remover um elemento da página, podemos usar o método `remove()` no elemento selecionado. Por exemplo:

```javascript
const $ = cheerio.load(html);

$('p:first-child').remove();
```

O código acima remove o primeiro elemento de parágrafo da página.

Para modificar um elemento existente na página, podemos usar os métodos `attr()` e `addClass()`. Por exemplo:

```javascript
const $ = cheerio.load(html);

$('p:first-child').attr('class', 'primeiro-paragrafo');
$('p:last-child').addClass('ultimo-paragrafo');
```

O código acima adiciona a classe "primeiro-paragrafo" ao primeiro elemento de parágrafo e adiciona a classe "ultimo-paragrafo" ao último elemento de parágrafo da página.

## Trabalhando com classes e estilos

Para trabalhar com classes e estilos em Cheerio, podemos usar os métodos `attr()` e `css()`, respectivamente.

Para definir uma classe de um elemento, podemos usar o método `attr()` passando o nome da classe como primeiro argumento e o valor, como segundo argumento. Por exemplo:

```javascript
const $ = cheerio.load(html);

$('p:first-child').attr('class', 'importante');
```

O código acima adiciona a classe "importante" ao primeiro elemento de parágrafo da página.

Para definir um estilo de um elemento, podemos usar o método `css()` passando o nome da propriedade de estilo como primeiro argumento e o valor desejado como segundo argumento. Por exemplo:

```javascript
const $ = cheerio.load(html);

$('p:first-child').css('color', 'red');
```

O código acima define a cor vermelha para o primeiro elemento de parágrafo da página.

## Inserindo e manipulando dados

Para inserir e manipular dados em uma página da Web, podemos usar o método `text()` do Cheerio. Este método recupera ou define o texto de um elemento selecionado.

Por exemplo, para recuperar o texto de um elemento, podemos fazer o seguinte:

```javascript
const $ = cheerio.load(html);

const textoParagrafo = $('p:first-child').text();
console.log(textoParagrafo); // "Parágrafo 1"
```

O código acima armazena o texto do primeiro elemento de parágrafo da página na variável `textoParagrafo`.

Para definir o texto de um elemento selecionado, podemos passá-lo como parâmetro para o método `text()`. Por exemplo:

```javascript
const $ = cheerio.load(html);

$('p:first-child').text('Novo texto do parágrafo 1');
```

O código acima define um novo texto para o primeiro elemento de parágrafo da página.

Com essas ferramentas, podemos manipular e extrair informações de uma página da Web usando Cheerio.
# Capítulo 6 - Trabalhando com Texto e Atributos em Cheerio

Neste capítulo, vamos aprender a trabalhar com texto e atributos de uma página da Web usando Cheerio. Para isso, utilizaremos as funções do Cheerio para capturar e manipular texto e atributos HTML.

## Capturando e manipulando texto

Para capturar e manipular texto em uma página da Web usando Cheerio, podemos usar o método `text()`. Este método retorna o texto dentro dos elementos selecionados.

Por exemplo, se quisermos capturar o título de uma página, podemos fazer o seguinte:

```javascript
const cheerio = require('cheerio');
const axios = require('axios');

axios.get('https://www.google.com')
  .then((response) => {
    const $ = cheerio.load(response.data);

    const title = $('title').text();
    console.log(title); // "Google"
  })
  .catch((error) => {
    console.log(error);
  });
```

O código acima captura o título da página do Google e o exibe no console.

Para definir novo texto em um elemento, podemos usar o mesmo método `text()`. Por exemplo:

```javascript
const $ = cheerio.load(html);

$('p:first-child').text('Novo texto para o primeiro parágrafo');
```

O código acima define um novo texto para o primeiro elemento de parágrafo da página.

## Capturando e manipulando atributos

Para capturar e manipular atributos em uma página da Web usando Cheerio, podemos usar o método `attr()`. Este método retorna o valor de um atributo para o primeiro elemento selecionado.

Por exemplo, se quisermos capturar o valor do atributo "href" de um link em uma página, podemos fazer o seguinte:

```javascript
const cheerio = require('cheerio');
const axios = require('axios');

axios.get('https://www.google.com')
  .then((response) => {
    const $ = cheerio.load(response.data);

    const link = $('a').attr('href');
    console.log(link); // "https://www.google.com/imghp?hl=en&tab=wi"
  })
  .catch((error) => {
    console.log(error);
  });
```

O código acima captura o valor do atributo "href" do primeiro elemento "a" da página do Google e o exibe no console.

Para definir um novo valor para um atributo, podemos usar novamente o método `attr()`. Por exemplo:

```javascript
const $ = cheerio.load(html);

$('a:first-child').attr('href', 'https://www.novolink.com');
```

O código acima define um novo valor para o atributo "href" do primeiro elemento "a" da página.

Podemos também remover um atributo de um elemento usando o método `removeAttr()`. Por exemplo:

```javascript
const $ = cheerio.load(html);

$('a:first-child').removeAttr('href');
```

O código acima remove o atributo "href" do primeiro elemento "a" da página.

## Trabalhando com URLs

Para trabalhar com URLs em Cheerio, podemos usar a biblioteca nativa do Node.js `url`. Esta biblioteca possui funções para transformar URLs em objetos e manipular diferentes partes da URL.

Por exemplo, se quisermos extrair o caminho e a query string de uma URL, podemos fazer o seguinte:

```javascript
const url = require('url');

const pagina = 'https://www.exemplo.com/pagina?parametro1=valor1&parametro2=valor2';
const urlObjeto = url.parse(pagina, true);

const caminho = urlObjeto.pathname;
const parametros = urlObjeto.query;

console.log(caminho); // "/pagina"
console.log(parametros); // { parametro1: 'valor1', parametro2: 'valor2' }
```

O código acima extrai o caminho e a query string de uma URL e os exibe no console.

Com essas ferramentas, podemos manipular e extrair informações de uma página da Web usando Cheerio e manipulação de atributos e URLs com o Node.js.
# Capítulo 7 - Aninhamento e Traversing em Cheerio

Neste capítulo, você aprenderá a usar as funcionalidades de aninhamento e traversing do Cheerio para navegar na árvore DOM da página da Web. Isso permitirá que você selecione elementos ancestrais e descendentes para trabalhar em conjunto com outros elementos.

## Entendendo aninhamento e traversing

Em uma página da Web, os elementos HTML são organizados em uma árvore hierárquica, em que cada elemento pode ter um ou mais elementos filhos.

O aninhamento se refere à forma como os elementos são agrupados em uma estrutura de árvore, em que cada elemento é um nó da árvore que pode conter outros nós filhos. O aninhamento correto é importante para o HTML ser interpretado corretamente pelos navegadores.

O traversing se refere à capacidade de navegar na árvore DOM para acessar qualquer elemento e seus filhos, irmãos e ancestrais. Isso permite que você alcance elementos em diferentes níveis da árvore, selecionando-os com base em suas relações com outros elementos.

## Navegando pela árvore DOM com Cheerio

Existem diversos métodos no Cheerio para navegar pela árvore DOM. Alguns dos mais comuns são:

- `parent()`: seleciona o elemento pai do elemento atual;
- `children()`: seleciona todos os elementos filhos do elemento atual;
- `find()`: seleciona todos os elementos correspondentes ao seletor especificado que são descendentes do elemento atual;
- `next()`: seleciona o próximo elemento imediato após o elemento atual;
- `prev()`: seleciona o elemento anterior imediatamente anterior ao elemento atual;
- `siblings()`: seleciona todos os elementos irmãos do elemento atual.

Vamos dar uma olhada em alguns exemplos para ver como esses métodos funcionam:

```javascript
const cheerio = require('cheerio');
const html = '<body><div><h1>Título</h1><ul><li>Item 1</li><li>Item 2</li></ul></div></body>';
const $ = cheerio.load(html);

// seleciona o elemento pai do elemento h1
const paiDoTitulo = $('h1').parent();
console.log(paiDoTitulo.html()); // <div><h1>Título</h1><ul><li>Item 1</li><li>Item 2</li></ul></div>

// seleciona todos os elementos filhos de div
const filhosDoDiv = $('div').children();
console.log(filhosDoDiv.length); // 2
console.log(filhosDoDiv.eq(0).html()); // <h1>Título</h1>
console.log(filhosDoDiv.eq(1).html()); // <ul><li>Item 1</li><li>Item 2</li></ul>

// seleciona todos os elementos li dentro de ul
const itensDaLista = $('ul').find('li');
console.log(itensDaLista.length); // 2
console.log(itensDaLista.eq(0).text()); // Item 1
console.log(itensDaLista.eq(1).text()); // Item 2

// seleciona o elemento irmão imediatamente após o h1
const proximoElemento = $('h1').next();
console.log(proximoElemento.html()); // <ul><li>Item 1</li><li>Item 2</li></ul>

// seleciona o elemento irmão anterior imediatamente antes do ul
const elementoAnterior = $('ul').prev();
console.log(elementoAnterior.html()); // <h1>Título</h1>

// seleciona todos os elementos irmãos de ul
const irmaosDoUl = $('ul').siblings();
console.log(irmaosDoUl.length); // 1
console.log(irmaosDoUl.eq(0).html()); // <h1>Título</h1>
```

## Selecionando elementos ancestrais e descendentes

Além dos métodos de navegação mencionados acima, existem outras formas de selecionar elementos descendentes ou ancestrais:

- `closest()`: seleciona o elemento mais próximo que corresponda a um seletor, começando pelo elemento atual;
- `parents()`: seleciona todos os elementos ancestrais do elemento atual;
- `parentsUntil()`: seleciona todos os elementos ancestrais que sejam um ancestral do elemento atual até um seletor especificado;
- `nextAll()`: seleciona todos os elementos irmãos do elemento atual que vêm depois dele;
- `prevAll()`: seleciona todos os elementos irmãos do elemento atual que vêm antes dele.

Vamos dar uma olhada no seguinte exemplo para ver como esses métodos funcionam:

```javascript
const cheerio = require('cheerio');
const html = '<body><div><h1>Título</h1><ul><li>Item 1</li><li>Item 2</li></ul></div></body>';
const $ = cheerio.load(html);

// seleciona o elemento div mais próximo que tenha uma classe especificada
const divComClasse = $('li').closest('.classe-especificada');
console.log(divComClasse.html()); // <div class="classe-especificada"><h2>Subtítulo</h2></div>

// seleciona todos os elementos ancestrais de li
const ancestraisDoLi = $('li').parents();
console.log(ancestraisDoLi.length); // 2
console.log(ancestraisDoLi.eq(0).html()); // <ul><li>Item 1</li><li>Item 2</li></ul>
console.log(ancestraisDoLi.eq(1).html()); // <div><h1>Título</h1><ul><li>Item 1</li><li>Item 2</li></ul></div>

// seleciona todos os elementos ancestrais de li até um elemento com uma classe especificada
const ancestraisAteClasse = $('li').parentsUntil('.classe-especificada');
console.log(ancestraisAteClasse.length); // 1
console.log(ancestraisAteClasse.eq(0).html()); // <ul><li>Item 1</li><li>Item 2</li></ul>

// seleciona todos os elementos irmãos de li que vêm depois dele
const proximosIrmaos = $('li:first-child').nextAll();
console.log(proximosIrmaos.length); // 1
console.log(proximosIrmaos.eq(0).text()); // Item 2

// seleciona todos os elementos irmãos de li que vêm antes dele
const irmaosAnteriores = $('li:last-child').prevAll();
console.log(irmaosAnteriores.length); // 1
console.log(irmaosAnteriores.eq(0).text()); // Item 1
```

Com essas ferramentas de aninhamento e traversing, você pode facilmente selecionar e trabalhar em qualquer elemento e em seus descendentes e ancestrais em Cheerio.
# Capítulo 8 - Operações CRUD em Cheerio

Neste capítulo, você aprenderá a realizar operações CRUD(criação, leitura, atualização e remoção) em elementos HTML utilizando o Cheerio. É importante lembrar que essas operações acontecerão somente no lado do cliente, ou seja, não serão refletidas na página da Web original.

## Introdução a Operações CRUD

Operações CRUD são os fundamentos da manipulação de dados em qualquer sistema. 

- Criação: consiste em adicionar um novo elemento à página da Web.
- Leitura: consiste em ler o conteúdo de um elemento.
- Atualização: consiste em alterar o conteúdo de um elemento existente.
- Remoção: consiste em excluir um elemento.

O Cheerio é uma excelente ferramenta para realizar todas essas operações em elementos HTML, de uma forma prática e eficiente.

## Criando novos elementos com Cheerio

Para criar um novo elemento HTML em Cheerio, basta usar a função `cheerio()` passando como argumento uma string contendo o HTML do elemento.

Por exemplo, suponha que você queira criar um elemento `div`:

```javascript
const cheerio = require('cheerio');
const $ = cheerio.load('<body></body>');

const novaDiv = cheerio('<div></div>');
$('body').append(novaDiv);
```

Este código cria e adiciona ao elemento `body` do HTML existente uma nova `div`.

Você também pode definir atributos e conteúdo para o novo elemento utilizando a mesma sintaxe de criação de elementos HTML:

```javascript
const novaDiv = cheerio('<div class="minha-classe">Conteúdo da div</div>');
```

## Lendo e atualizando dados existentes

O Cheerio torna muito fácil a leitura e atualização do conteúdo existente nos elementos HTML.

Para ler o conteúdo de um elemento existente, você pode utilizar a função `text()`:

```javascript
const textoH1 = $('h1').text();
```

Este trecho de código armazena em `textoH1` o conteúdo do primeiro elemento `h1` encontrado no HTML.

Para atualizar o conteúdo de um elemento existente, basta utilizar a mesma função `text()` com um argumento que será definido como o novo conteúdo. Por exemplo, para atualizar o conteúdo de uma `div`, você pode fazer:

```javascript
$('div').text('Novo conteúdo da div');
```

## Deletando elementos

Para excluir elementos em Cheerio, basta selecionar o elemento desejado e chamar a função `remove()`:

```javascript
$('div').remove();
```

Este trecho de código exclui todos os elementos `div` encontrados no HTML.

## Exemplo de operações CRUD

Considere o seguinte HTML:

```html
<body>
  <div id="conteudo">
    <h1>Manipulando conteúdo HTML</h1>
    <p>Este é um parágrafo.</p>
    <ul>
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ul>
  </div>
</body>
```

A seguir, temos um exemplo que executa uma operação CRUD em cada tipo de elemento no HTML:

```javascript
const cheerio = require('cheerio');
const $ = cheerio.load('<body><div id="conteudo"><h1>Manipulando conteúdo HTML</h1><p>Este é um parágrafo.</p><ul><li>Item 1</li><li>Item 2</li><li>Item 3</li></ul></div></body>');

// Cria um novo elemento
const novaDiv = cheerio('<div>Conteúdo da nova div</div>');
$('#conteudo').append(novaDiv);

// Lê o conteúdo de um elemento
const textoP = $('p').text();
console.log(textoP);

// Atualiza o conteúdo de um elemento
$('h1').text('Novo título');

// Remove um elemento
$('ul').remove();
```

Este exemplo adiciona uma nova `div` ao elemento `#conteudo`, lê o conteúdo do `p`, atualiza o conteúdo do `h1` e remove o elemento `ul`.
# Capítulo 9 - Web Scraping com Cheerio

Neste capítulo, você entenderá o que é Web Scraping e quando usá-lo. Além disso, abordaremos os principais desafios do Web Scraping e as ferramentas disponíveis para ajudá-lo a coletar dados usando Cheerio.

## O que é Web Scraping e quando usá-lo

Web Scraping é o processo de extrair dados de sites da Web automaticamente. É uma técnica muito utilizada para obter dados de sites que não possuem uma API pública ou qualquer outro recurso direto para acessar esses dados.

Web Scraping é útil em várias situações, por exemplo, se você precisar coletar informações de preços de produtos de vários sites de comércio eletrônico, ou se desejar coletar dados de relatórios financeiros divulgados em sites da Web.

No entanto, é importante ressaltar que alguns sites proíbem explicitamente o Web Scraping em seus termos de serviço. Sendo assim, certifique-se de verificar as políticas de privacidade e os termos de serviço antes de realizar qualquer tipo de Web Scraping.

## Os principais desafios do Web Scraping

Há alguns desafios comuns no Web Scraping, como:

- **Autenticação:** algumas páginas da Web exigem autenticação para permitir que você acesse certos conteúdos.
- **Estrutura do site:** a estrutura dos sites pode variar muito, e encontrar a informação que você precisa pode ser complicado.
- **Dinamismo da página:** páginas da Web que utilizam tecnologias dinâmicas, como AJAX, podem ser difíceis de capturar automaticamente.

## Ferramentas disponíveis para Web Scraping

Existem várias ferramentas disponíveis para o Web Scraping, incluindo Cheerio.

O Cheerio é uma biblioteca leve e rápida que nos permite manipular facilmente o HTML encontrado em uma página da Web. 

Existem várias outras ferramentas que podem ser usadas em conjunto com o Cheerio, como por exemplo o axios, que é uma biblioteca para requisições HTTP que permite fazer solicitações a uma página da Web e recebê-la.

## Introdução a coleta de dados com Cheerio

Para começar a coletar dados usando Cheerio, é necessário fazer uma solicitação HTTP para a página da Web que deseja obter dados e, em seguida, carregar o HTML usando Cheerio.

Para realizar a solicitação HTTP, podemos usar o axios, por exemplo. Você pode instalar o axios através do gerenciador de pacotes `npm`, executando o comando:

```bash
npm install axios
```

A seguir, apresentamos um exemplo simples que utiliza o Cheerio para extrair o título de uma página da Web:

```javascript
const axios = require('axios');
const cheerio = require('cheerio');

axios.get('https://www.google.com.br')
  .then(response => {
    const $ = cheerio.load(response.data);
    console.log($('title').text());
  })
  .catch(error => {
    console.log(error);
  });
```

Este código solicita a página do Google, carrega o HTML com Cheerio e imprime o título da página no console.

É importante lembrar que o Cheerio não executa scripts do lado do cliente, portanto, não será possível obter dados gerados dinamicamente. Mas ainda assim você pode manipular e extrair dados do HTML.
# Capítulo 10 - Exemplos Práticos

Neste capítulo, apresentaremos exemplos práticos de como fazer Web Scraping utilizando o Cheerio.

## Extraindo dados de uma página da web com Cheerio

Suponhamos que você precise extrair os títulos e as imagens de uma página de notícias. O exemplo abaixo pode ser usado para coletar o título e o URL da imagem destacada em cada notícia:

```javascript
const axios = require('axios');
const cheerio = require('cheerio');

axios.get('https://www.noticias.com/')
  .then(response => {

      const $ = cheerio.load(response.data);

      const newsTitles = [];
      const newsImages = [];

      $('article:not(.banner)').each((i, element) => {
          const title = $(element).find('h2').text().trim();
          const image = $(element).find('img').attr('src');

          newsTitles.push(title);
          newsImages.push(image);
      });

      console.log(newsTitles, newsImages);

  })
  .catch(error => {
    console.log(error);
  });
```

Este código solicita a página de notícias, carrega o HTML e usa Cheerio para extrair os títulos e as imagens destacadas de cada notícia. Por fim, o código imprime no console uma lista de títulos e uma lista de URLs de imagens.

Observe que este código seleciona apenas as tags `<article>` que não possuem a classe "banner", para excluir qualquer objeto que estiver na parte superior da página (como uma propaganda ou um banner).

## Escaneando várias páginas da web com Cheerio

Se você precisar fazer o Web Scraping em várias páginas de um site, pode ser necessário utilizar o loop `for` em conjunto com a função `axios.get()` para capturar as informações. Abaixo está um exemplo de como fazer isso:

```javascript
const axios = require('axios');
const cheerio = require('cheerio');

for (let i = 1; i <= 3; i++) {
    axios.get(`https://www.site.com/page=${i}`)
        .then(response => {

            const $ = cheerio.load(response.data);

            const products = [];

            $('.product').each((i, element) => {
                const name = $(element).find('.product-name').text().trim();
                const price = $(element).find('.product-price').text().trim();

                products.push({
                    name,
                    price
                });
            });

            console.log(products);

        })
        .catch(error => {
            console.log(error);
        });
}
```

Este código faz a solicitação HTTP para cada página desejada e, em seguida, extrai os nomes e preços dos produtos em cada página.

Observe que neste exemplo usamos um loop `for` para percorrer as três primeiras páginas do site. É importante ressaltar que caso o número de páginas for muito grande, a abordagem de usar o loop `for` em conjunto com a função `axios.get()` pode não ser a mais adequada, e é possível que o site negue a solicitação. 

## Coletando informações de várias páginas da web

Se você precisar coletar informações de várias páginas da web, mas não souber quantas páginas existem, é possível usar a recursividade para continuar coletando informações enquanto houver páginas disponíveis. Abaixo está um exemplo de como fazer isso:

```javascript
const axios = require('axios');
const cheerio = require('cheerio');

let products = [];

function scrapeProductPage(url) {
    axios.get(url)
        .then(response => {

            const $ = cheerio.load(response.data);

            $('.product').each((i, element) => {
                const name = $(element).find('.product-name').text().trim();
                const price = $(element).find('.product-price').text().trim();

                products.push({
                    name,
                    price
                });
            });

            const nextPage = $('.next-page').attr('href');

            if (nextPage) {
                scrapeProductPage(nextPage);
            } else {
                console.log(products);
            }

        })
        .catch(error => {
            console.log(error);
        });
}

scrapeProductPage('https://www.site.com/page=1');
```

Este código começa fazendo a solicitação HTTP para a página 1 do site e, em seguida, extrai os nomes e preços dos produtos. Em seguida, a função verifica se existe uma próxima página e, se houver, chama a função `scrapeProductPage()` novamente com o URL da próxima página. Este processo é repetido até não haver mais páginas disponíveis.

Observe que neste exemplo usamos a recursividade para continuar coletando informações enquanto houver páginas disponíveis. É importante ressaltar que o uso excessivo de recursão pode esgotar a pilha de chamadas, por isso, dependendo do site, convém usar outras abordagens para coletar informações de várias páginas.

## Gerenciamento de erros em Cheerio

Ao fazer o Web Scraping usando Cheerio, podem ocorrer vários erros, como falha na conexão HTTP ou erro no HTML retornado. É importante ter um gerenciamento adequado de erros em seu código.

Uma abordagem comum é usar o bloco `try`/`catch` para capturar exceções. Em geral, é recomendável adotar uma estratégia para lidar com erros específicos que podem ocorrer durante o processo de Web Scraping.

```javascript
const axios = require('axios');
const cheerio = require('cheerio');

function scrapePage(url) {
    try {

        axios.get(url)
          .then(response => {

              const $ = cheerio.load(response.data);

              const title = $('title').text().trim();

              console.log(title);

          });

    } catch (error) {
        console.log(`Erro ao processar ${url}: ${error}`);
    }
}

scrapePage('https://www.sitequeporventura.com/');
```

Este código faz a solicitação HTTP para uma página da web e usa Cheerio para extrair o título da página. Observe que estamos usando o bloco `try`/`catch` para capturar exceções e exibir uma mensagem de erro caso ocorra algum erro durante o processo de Web Scraping.

É importante ressaltar que é possível e recomendável adotar outras abordagens para o gerenciamento de erros. Por exemplo, em vez de simplesmente exibir uma mensagem de erro na tela, é possível usar uma estrutura encapsuladora para lidar com erros de forma mais granular.

