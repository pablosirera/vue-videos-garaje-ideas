## Directiva `v-else-if`
[Link](https://vuejs.org/guide/essentials/conditional.html#v-else-if) a la documentación oficial.


### Ejemplo básico con directiva v-else-if
```js
<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <h1>Prueba v-else-if</h1>
  <p v-if="count > 5">
    Tengo más de 5
  </p>
  <p v-else-if="count > 0">
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
