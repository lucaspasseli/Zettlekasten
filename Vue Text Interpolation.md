Em Vue nós podemos utilizar o `Mustache syntax` ou `double curly braces`  `{{ }}` para dinamicamente vincular dados da nossa instancia Vue no nosso template.

Exemplos: 

```html
<div id="app">
  <span>Message: {{ msg }}</span>
</div>
```

```js
new Vue({
  el: '#app',
  data: {
    msg: 'Hello, Vue!'
  }
});
```

Neste exemplo acima nós possuímos o dados `msg` que esta dentro de `data` na nossa instancia Vue, ele possui o valor `Hello, Vue!` e para que conseguimos colocar isso na tela (template), podemos ir diretamente dentro da tag `span` e passar o nome deste dado dentro de `{{ }}`.

## Atualizações dinâmicas

Um dos maiores poderes do Vue é a reatividade, por tanto, se o valor de `msg` dentro da tag `span` mudar, o Vue de forma inteligente irá atualizar este elemento no DOM com o novo valor

```js
setTimeout(() => {
  app.msg = 'Hello, World!';
}, 2000);
```

O código acima fará com que o conteúdo da propriedade `msg` na nossa instancia Vue mude após 2 segundos, e isso refletirá no nosso template, alterando assim também o texto da tag `span`.

## Interpolações mais complexas

Nós podemos também executar operações lógicas mais complexas e funções Javascript dentro de `{{ }}`

Exemplo: 

```html
<div id="app">
  <span>Message: {{ msg.toUpperCase() }}</span>
  <span>Sum: {{ number1 + number2 }}</span>
</div>
```

```js
new Vue({
  el: '#app',
  data: {
    msg: 'Hello, Vue!',
    number1: 5,
    number2: 10
  }
});
```

- `{{ msg.toUpperCase() }}` será mostrado como: "HELLO, VUE!".
- `{{ number1 + number2 }}` será mostrado como: "15".
