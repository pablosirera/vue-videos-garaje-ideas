## Directiva `v-else`
[Link](https://vuejs.org/guide/essentials/conditional.html#v-else) a la documentación oficial.


### Ejemplo básico con directiva v-else
```js
<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <h1>Prueba v-else</h1>
  <p v-if="count > 0">
    Tengo {{ count }}
  </p>
  <p v-else>
    El contador no ha empezado
  </p>
  <button @click="count++">
    sumar
  </button>
</template>
```
