Em Vue pode ser que em alguns momentos tenhamos que utilizar mais complexidade dentro do nosso template, e isso pode ser tanto dificultoso na escrita, quanto na leitura do código posteriormente.

Para isso podemos utilizar o método `computed` e encapsular essa lógica em um variável (`computed property`). Exemplo: 

#### Sem Computed

```js
const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

```

```vue
<p>Has published books:</p>
<span>{{ author.books.length > 0 ? 'Yes' : 'No' }}</span>
```

#### Com Computed

```vue
<script setup>
import { reactive, computed } from 'vue'

const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

// a computed ref
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})
</script>

<template>
  <p>Has published books:</p>
  <span>{{ publishedBooksMessage }}</span>
</template>
```

Com isso deixamos o nosso template bem mais limpo, e também ganhamos a vantagem de não precisar codificar isso novamente.

## Computed Caching vs. Methods

Você deve ter percebido, que não necessariamente precisa do método `computed` para garantir os benefícios acima, já que se pode fazer o mesmo encapsulando em uma simples função. Exemplo: 

```vue
<p>{{ calculateBooksMessage() }}</p>
```

```js
// in component
function calculateBooksMessage() {
  return author.books.length > 0 ? 'Yes' : 'No'
}
```

Em praticamente todos os sentido utilizar o método `computed` ou uma função resultará no mesmo. A grande diferença é que o método `computed` utiliza de um cache baseado na reatividade das suas dependências, isto é, a menos que alguma das dependências utilizadas nele mude, ele não irá recalcular novamente.

Utilizando os exemplos acima, podemos dizer que, a menos que algo em `author.books` mude, `computed` não irá recalcular o resultado, por tanto, será o mesmo resultado posterior.

O exemplo a baixo também mostra algo que nunca mudará, afinal `Date` não é um estado que ativará a reatividade para `computed` recalcular:

```js 
const now = computed(() => Date.now())
```

Em comparação, se estivessemos  utilizando uma função normal, a mesma seria executada em toda re-renderização sem precedentes.

## Writable computed

Em raros casos, você precisará escrever algum valor para dentro de um método `computed`, mas para isso, podemos fazer com que ele receba um objeto com as funções `get` e `set`  que atuaram para capturar o resultado, e mudar o resultado interno do método `computed`

```vue
<script setup>
import { ref, computed } from 'vue'

const firstName = ref('John')
const lastName = ref('Doe')

const fullName = computed({
  // getter
  get() {
    return firstName.value + ' ' + lastName.value
  },
  // setter
  set(newValue) {
    // Note: we are using destructuring assignment syntax here.
    [firstName.value, lastName.value] = newValue.split(' ')
  }
})
</script>
```

Getters devem ser livres de efeitos colaterais, por tanto, não altere outros estados, ou elementos do DOM ou faça funções assíncronas neles.

Evite também alterar diretamente uma `computed property`, já que o objetivo dela é atualizar apenas se alguma de suas dependências mudar. Caso precise, mude a dependências diretamente, mas nunca a `computed property`