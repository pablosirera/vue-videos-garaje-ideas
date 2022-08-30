## Directiva `v-if`
[Link](https://vuejs.org/guide/essentials/conditional.html#v-if) a la documentación oficial.

### Ejemplo lógica ocultar y mostrar elemento con javascript vanilla
```js
<script setup>
const hideItem = () => {
  const p = document.querySelector('p')
  p.style.display = 'none'
}
const showItem = () => {
  const p = document.querySelector('p')
  p.style.display = 'block'
}
</script>

<template>
  <h1>Prueba v-if</h1>
  <p>
    Texto de prueba que quiero ocultar o mostrar
  </p>
  <button @click="showItem">
    mostrar texto
  </button>
  <button @click="hideItem">
    ocultar texto
  </button>
</template>
```

### Ejemplo lógica con directiva v-if
```js
<script setup>
import { ref } from 'vue'

const showText = ref(true)
</script>

<template>
  <h1>Prueba v-if</h1>
  <p v-if="showText">
    Texto de prueba que quiero ocultar o mostrar
  </p>
  <button @click="showText = true">
    mostrar texto
  </button>
  <button @click="showText = false">
    ocultar texto
  </button>
</template>
```
