
Vue é um framework Javascript criado para construção de interfaces. Ele é construído com base em HTML, CSS e Javascript, e proporciona uma forma declarativa e produtiva de se programar baseando-se em componentes, o que foca em ajudar na construção de interfaces de qualquer complexidade.

Exemplo de código: 

```js
import { createApp, ref } from 'vue'

createApp({
  setup() {
    return {
      count: ref(0)
    }
  }
}).mount('#app')
```

```vue
<div id="app">
  <button @click="count++">
    Count is: {{ count }}
  </button>
</div>
```

O exemplo acima demonstra dois dos principais conceitos do Vue, sendo eles:

**Declarative rendering:**

Com a renderização declarativa, nós podemos construir a interface (UI) com base em valores dinâmicos(variáveis, estados, retorno de funções), sem especificar diretamente com isso será feito. Utilizamos o Template sintax para declarativamente descrever como deve ser o output em HTML e o Binding Dinâmico utilizando. `{{ }}` (interpolação) para incluir valores dinâmicos na nossa interface.

**Reatividade:** O Vue permite com que o DOM seja automaticamente atualizado após uma mudança de estado.

## O Framework

Vue é um framework que atende as funcionalidade mais comuns em um desenvolvimento front-end. Mas o mundo web por si só é muito vasto, por tanto, Vue é construído para ser flexível e adotável incrementalmente. Vue pode ser utilizada das mais diversas formas, entre elas:

- Enhancing static HTML without a build step
- Embedding as Web Components on any page
- Single-Page Application (SPA)
- Fullstack / Server-Side Rendering (SSR)
- Jamstack / Static Site Generation (SSG)
- Targeting desktop, mobile, WebGL, and even the terminal

Vue é um framework em que você pode crescer junto e adaptá-lo para suas necessidades.

## Single-File Components (SFC)

Na maioria dos projetos desenvolvidos com Vue vamos nos deparar com Single-File Components ou SFC(também podem ser identificados como `*.vue` em arquivos, que é uma abreviação do SFC). O SFC encapsula a lógica do componente(Javascript), a marcação dos elementos ou template(HTML) e a estilização(CSS) em um arquivo só. Exemplo:

```vue
<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
```

Single-File Components (SFCs) são uma característica fundamental do Vue.js e são recomendados para criar componentes Vue, especialmente se o seu projeto usa uma configuração de build (ferramentas de construção como Webpack ou Vite).

## API styles

Em Vue nós temos duas diferentes formas de de escrever nossos componentes, sendo uma delas a Options API e a outra a Composition API.

### Options API

é uma forma mais simples e alto nível de se escrever, com ela nós usaremos um objeto que terá as propriedades data, methods e mounted. Todas essas propriedades são expostas nas funções dentro de this, que será a instancia do componente

### Composition API

Com Componsition nós escreveremos nosso componente através de função do próprio Vue, utilizando SFC (Single File Component). Compostion API é uma forma mais declarativa e completa de se programar com Vue

### Qual utilizar?

A duas maneiras compartilham do mesmo fundamento e conhecimento de Vue, sendo a Options feita por cima da Composition.

Options segue um paradigma mais voltado a OOP e é mais amigável.

Composition é mais completa e tem seu paradigma voltado a reatividade. ë uma maneira mais livre de se lidar com Vue, apenas de mais complexa, ela nos permite mais flexibilidade, utilização de bons padrões e reutilização de código.

Para código em produção, é recomendado que utilizemos Options caso não estivermos com nenhuma ferramenta de build, ou se pretendemos utilizar Vue de forma primaria e sem muita complexidade.

Utilize Composition em produção quando quiser ter todo poder do Vue, principalmente com SFC