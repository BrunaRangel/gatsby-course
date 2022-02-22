---
date: 2018-08-10 05:54:23
title: Como escrever HTML com acessibilidade?
description: Elementos semânticos trazem informações adicionais a leitores de tela e outras ferramentas, facilitando a navegação no site.
category: Acess
background: "#1E90FF"
---

# O que é WAI-ARIA?

Em algumas situações, é difícil criar controles de acessibilidade para elementos não semânticos do HTML ou elementos dinâmicos de JavaScript. Por esse motivo, foi desenvolvida a WAI-ARIA, uma especificação escrita pelo W3C, que **define um conjunto de atributos HTML para acessibilidade**. Esses atributos podem ser reconhecidos por navegadores e tecnologias assistivas, conferindo semântica adicional ao elemento.


- **Atributos** `role`: definem o que um elemento é ou faz. São atribuídos aos landmarks, que serão explicados adiante.

- **Propriedades**: conferem semântica adicional. A propriedade `aria-required="true"`, por exemplo, especifica que um campo deve estar preenchido para validar um formulário.

- **Estados**: propriedades especiais que definem condições atuais dos elementos, como `aria-disabled="true"`, que especifica para um leitor de telas que o campo de um formulário está inativo naquele momento. Estados diferem de propriedades porque podem variar conforme o ciclo de vida de uma aplicação.

As diretrizes podem ser acessadas na documentação oficial da WAI-ARIA em [inglês](https://www.w3.org/TR/wai-aria/) ou [português](https://www.w3.org/Translations/WCAG20-pt-br/).

## Como trazer acessibilidade para o HTML?

Devemos pensar em acessibilidade durante todo o desenvolvimento de um site. Pode ser que você não tenha controle absoluto sobre códigos desenvolvidos em algum framework. Mas qualquer melhoria que consiga fazer contribui para uma internet mais acessível.

Confira algumas dicas a seguir.

### 1. Definir a linguagem do seu documento

Logo no início do HTML, defina a linguagem que você está usando (`<html lang="pt-br">`). Além de ser bom para SEO e ferramentas de tradução, a definição do idioma no documento ajuda tecnologias assistivas a definirem o perfil de voz e conjunto de caracteres.
É possível ainda alterar a linguagem em elementos específicos, quando necessário, utilizando o atributo `lang`.

### 2. Estrutura textual semântica

Utilize tags adequadas para títulos, subtítulos, parágrafos e listas no seu conteúdo textual. O leitor de telas vai identificar cada elemento para o usuário, permitindo ainda navegar de título em título (o que é bastante útil para portais de notícias, por exemplo).
Evite pular níveis de títulos (`<h1>` a `<h6>`), para que o leitor de telas possa navegar de maneira hierárquica entre os cabeçalhos. Ou seja, se o usuário está navegando entre títulos `<h1>`, a qualquer momento ele poderá varrer os cabeçalhos `<h2>` filhos de um `<h1>`.

Outras dicas para texto:

- Não utilize hífen na estrutura da frase, se for possível evitar (por exemplo, escreva “2 a 4” no lugar de “2–4”).

- Expanda abreviações sempre que possível (“janeiro” no lugar de “jan”).

- Expanda acrônimos pelo menos uma vez no texto (“interface de programação de aplicações” quando mencionar “API” pela primeira vez).

### 3. Landmarks

Landmarks são pontos de referência utilizados por leitores de tela para saltos no conteúdo. Devem ser usados para marcar blocos importantes, como menu de navegação, conteúdo principal, campos de busca, entre outros, permitindo que o usuário chegue diretamente a esses elementos.

Para criar landmarks, devemos incluir o atributo `role` no elemento, identificando seu valor semântico (como `search`, `form`, `navigation`, `article`, entre outros). O atributo `role` também deve ser usado dentro de elementos semânticos, mesmo que pareça redundante.


### 4. Elementos de interação

Controles de User Interface (UI) são os elementos com os quais o usuário interage, como botões, links e formulários. Navegadores permitem que esses controles sejam acessados pelo teclado. Eles devem ser usados adequadamente, pois são elementos com padrões de acessibilidade nativos que facilitam a navegação.

O elemento `label`, por exemplo, é um rótulo importante para controle de formulários. Os rótulos de texto devem ser claros e distintos, tanto em formulários, como em botões e links. Assim, o usuário sabe para onde será direcionado ou como preencher um campo.

Ainda falando de formulários, você pode utilizar a tag `<fieldset>` para agrupar e contextualizar elementos, como opções de checkbox ou radio button. Nesse caso, a legenda do campo poderia estar em uma tag `<legend>` (dentro do `<fieldset>`) e cada `<input>` estaria associado a uma `<label>`.

Outra dica importante é não confundir link com botão. Enquanto o botão é utilizado para interações, como envio de formulários, o link deve ser usado para navegação (interna ou externa). Lembrando que links que direcionam para fora do site devem ser identificados dessa forma.

### 5. Tabelas

Tabelas devem ser escritas em HTML com células de cabeçalho associadas corretamente às suas colunas ou linhas, para uma leitura mais clara do leitor de telas. Ou seja, é importante separar corretamente o conteúdo em tags `<th>` e `<td>`. É possível, ainda, especificar se `<th>` é cabeçalho de linhas ou colunas, utilizando o atributo `scope`.

O elemento `<caption>` e o atributo `summary` (resumo) funcionam como texto alternativo para a tabela, fornecendo mais informações ao usuário. Não é necessário utilizar os dois juntos, sendo a tag `<caption>` mais recomendada por fornecer uma legenda que também pode ser útil a usuários com visão.

### 6. Imagens

No HTML, as imagens devem possuir o atributo `alt` com um texto alternativo que descreva seu conteúdo. Não é necessário iniciar o texto com “Imagem/Figura/Gráfico de …”, pois o leitor de tela fará isso de qualquer maneira.

Se a tag `<img>` tiver apenas o atributo `src`, o leitor lerá o nome do arquivo, o que pode ser bem confuso e pouco específico. Sem dúvida, também é importante usar nomes significativos para esses arquivos.

É possível incluir informações contextuais extras no atributo `title`, que também será lido pelo leitor de telas, além de ser exibido quando o mouse estiver sobre a imagem.

Outra forma de associar um texto complementar a uma imagem é inserí-lo em uma tag de parágrafo com um `id`, que será referido no atributo `aria-labelledby` da imagem. Isso é bastante útil se você quiser usar o mesmo texto como rótulo para várias imagens, ou ainda para gráficos e infográficos, com uma descrição mais detalhada.

Caso as imagens sejam apenas decorativas, é recomendado incluí-las na página como `background-image` através de CSS.

Vale sinalizar que todos os elementos visuais ou multimídia, como ícones, vídeos e áudios, precisam de um elemento textual que os descrevam.


### 7. Algumas dicas adicionais

- Evite fontes de ícones, se possível, pois não são um formato acessível;

- Não transmita informações somente através de cores (em tabelas, por exemplo);

- Links sublinhados são úteis para usuários com dificuldade para discernir contraste;

- Textos de links devem ser descritivos (e não apenas “clique aqui”);

- A rolagem infinita pode ser problemática para navegação por teclado;

- Teste sua página sem CSS, para avaliar a estrutura e verificar se o conteúdo continua fazendo sentido;

- Teste a navegação por teclado e o leitor de telas em seu site;

- Se possível, disponibilize uma visualização do site em “modo noturno”.




```javascript
a=3
puts a
```

