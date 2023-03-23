# Anotações

Vue é um framework javascript para a construção de interfaces.
Ele trabalha com HTML, CSS e Javascript e possibilita 2 formas diferentes de programação Options API e Compositions API.

### Options API

Com a API de opções, definimos a lógica de um componente usando um objeto de opções como dados, métodos e montado. As propriedades definidas por opções são expostas nestas funções internas, que apontam para a instância do componente:

```vue
<script>
export default {
  // Properties returned from data() become reactive state
  // and will be exposed on `this`.
  data() {
    return {
      count: 0
    }
  },

  // Methods are functions that mutate state and trigger updates.
  // They can be bound as event listeners in templates.
  methods: {
    increment() {
      this.count++
    }
  },

  // Lifecycle hooks are called at different stages
  // of a component's lifecycle.
  // This function will be called when the component is mounted.
  mounted() {
    console.log(`The initial count is ${this.count}.`)
  }
}
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>

```

### Composition API

Com a API de composição, definimos a lógica de um componente usando funções de API importadas. Em SFCs, a API de composição é normalmente usada com ``<script setup>``. O atributo **setup** é uma dica que faz o Vue realizar transformações em tempo de compilação que nos permitem usar a API Composition com menos clichê. Por exemplo, importações e variáveis de nível superior

```vue
<script setup>
import { ref, onMounted } from 'vue'

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment() {
  count.value++
}

// lifecycle hooks
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>

```

## Estrutura de Arquivo de Componentes Vue

Na maioria dos projetos Vue habilitados para ferramentas de construção, criamos componentes Vue usando um formato de arquivo semelhante a HTML chamado Single-File Component (também conhecido como arquivos *.vue, abreviado como SFC). Um Vue SFC, como o nome sugere, encapsula a lógica do componente (JavaScript), modelo (HTML) e estilos (CSS) em um único arquivo. Aqui está o exemplo anterior, escrito no formato SFC:

```vue
<script>
export default {
  data() {
    return {
      count: 0
    }
  }
}
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

### Composição de um projeto vue

- iniciar um projeto npm create vite@latest

A estrutura de um projeto em vue é bem parecida com a de um projeto React.js. 

Existe um arquivo index.html com uma classe / id que é referênciada no arquivo ``main.js``

```javascript
import App from './App.vue'

createApp(App).mount('#app')
```

Aonde o ``App`` é o componente que será rederizado dentro da classe ``#app``.