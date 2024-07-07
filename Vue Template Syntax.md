Vue utiliza uma sintaxe de template que se baseia em HTML. Isso significa que, ao criar uma aplicação Vue, você escreve seu layout e estrutura usando HTML padrão.

Os templates Vue são HTML válido. Isso significa que qualquer template escrito para um componente Vue é compatível com os padrões HTML e pode ser interpretado por navegadores e analisadores HTML.

## Declaratively bind the rendered DOM:

Vinculação declarativa significa que você define como o conteúdo deve ser exibido usando diretivas e bindings no HTML, em vez de manipular diretamente o DOM com JavaScript. Isso é feito utilizando sintaxe especial do Vue, como `{{ }}` para interpolação de dados e `v-bind` para bindings de atributos.

## Underlaying Data instance:

Os dados aos quais você vincula o DOM são provenientes da instância do componente Vue. Cada componente Vue possui um objeto `data` que contém os valores que serão exibidos ou manipulados no template.

```html
<!-- Template -->
<div id="app">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
```

```js
// Instância do Vue
new Vue({
	el: '#app',
	data: {
	  message: 'Hello Vue!'
	}
  });
```

obs: **v-model**: Cria uma vinculação bidirecional entre um campo de formulário e os dados.

## Compilação

Por debaixo dos pano o Vue compila um código Javascript ja altamente otimizado, e junto com seu paradigma reativo, ele de forma inteligente consegue detectar e aplicação o mínimo de alterações no DOM quando a aplicação atualiza.

O conceito de Virtual Dom também existe no Vue, mas se preferir existem opções para se escrever funções que que lidam diretamente com a renderização do seu componente, e também com JSX, mas de qualquer forma, elas não terão a mesma performance do que o template syntax mais Virtual DOM
