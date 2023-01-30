## Video 11. Directivas personalilzadas

Resumen sobre cómo crear directivas personalizadas con Vue 3.

---

Crear directiva básica
```js
<script setup>
const vFocus = {
  mounted: (el) => el.focus()
}
</script>

<template>
  <input v-focus />
</template>
```

Uso de directiva básica sin script setup
```js
export default {
  setup() {
    const msg = ref('Hello World!')

    return {
      msg
    }
  },
  directives: {
    focus: {
      mounted: (el) => el.focus()
    }
  }
}
```

Otro ejemplo de directiva aplicada a un párrafo
```js
<script setup>
const vRed = {
  mounted: (el, { value }) => {
    el.style.color = value || 'red'
  }
}
</script>

<template>
  <p v-red="'blue'">
    asd
  </p>
  <p>
    aaa
  </p>
</template>
```

Adaptar una directiva para que sea reactiva a los cambios. Las anteriores en el caso de cambiar el valor enviado no actualizaría el template.
```js
<script setup>
import { ref } from 'vue'

const vRed = {
  mounted: (el, { value }) => {
    el.style.color = value || 'red'
  },
  updated: (el, { value }) => {
    el.style.color = value || 'red'
  },
}
const color = ref('blue')
</script>

<template>
  <p v-red="color">
    asd
  </p>
  <p>
    aaa
  </p>
  <button @click="color = 'red'">
    change to red
  </button>
</template>
```

Una vez conocemos cómo definir una directiva es hora de conocer su uso simplificado
```js
const vRed = (el, { value }) => {
  el.style.color = value || 'red'
}
```

Por último definimos una directiva a nivel global
```js
import App from './App.vue'

const app = createApp(App).mount('#app')

app.directive('color', (el, { value }) => {
  el.style.color = value || 'red'
})
```