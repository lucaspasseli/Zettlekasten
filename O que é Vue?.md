
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

