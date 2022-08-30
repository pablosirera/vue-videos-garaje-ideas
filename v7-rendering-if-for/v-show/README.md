## Directiva `v-show`
[Link](https://vuejs.org/guide/essentials/conditional.html#v-show) a la documentación oficial.


### Ejemplo básico con directiva v-show
```js
<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <h1>Prueba v-show</h1>

  <p v-show="count > 0">
    Tengo {{ count }}
  </p>
  <button @click="count++">
    sumar
  </button>
</template>
```
