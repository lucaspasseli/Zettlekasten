
Toda aplicação Vue se inicia com a criação de uma nova instancia com a função `createApp`

```js
import { createApp } from 'vue'

const app = createApp({
  /* root component options */
})
```

## Root component

De fato, nós passamos um componente raiz (Root component) para dentro de função createApp, isso fará com que ele seja a base para toda a aplicação. Normalmente utilizamos SFC e esse componente é importado de um outro arquivo.

```js
import { createApp } from 'vue'
// import the root component App from a single-file component.
import App from './App.vue'

const app = createApp(App)
```

## Montando a aplicação

Uma instancia da aplicação Vue não irá ser renderizada até que o método `.mount()` seja executado, ele espera um "container" como argumento, que no caso pode ser tanto um elemento no DOM quanto uma string para ser utilizada de seletor CSS

O conteúdo da aplicação sera renderizada dentro do container que foi passado como argumento para o `.mount()`. Apesar de tudo, o container não é considerado uma parte de aplicação.

O método `.mount()` deve ser sempre executado após todo o carregamento das configurações do App.

## Configurações de uma aplicação 

Toda instancia de uma aplicação Vue, tem uma propriedade `config` que recebe um objeto com configurações globais, um exemplo é podemos estabelecer uma função de `error handling` para todo os componentes descendentes:

```js
app.config.errorHandler = (err) => { /* handle error */ }
```

Podemos também ter acessos a alguns métodos globais a partir da instancia, como por exemplo registrar componentes para serem acessados de forma global:

```js
app.component('TodoDeleteButton', TodoDeleteButton)
```

Este exemplo acima fará com que o componente `TodoDeleteButton` possa ser acessado de qualquer lugar.

## Múltiplas instancias de aplicação

Em Vue você não é limitado a utilizar apenas uma instancia de aplicação, na verdade, você pode criar quantas quiser. Você pode executar inúmeras vezes o método `createApp` e em seguida o método `mount` da instancia para renderiza-la em um elemento DOM. Desta forma, várias aplicações Vue podem coexistir sem problemas, cada uma com configurações e setups específicos e isolados. Exemplo: 


```js
const app1 = createApp({
  /* ... */
})
app1.mount('#container-1')

const app2 = createApp({
  /* ... */
})
app2.mount('#container-2')
```

