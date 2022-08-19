## Video 6. Ciclos de vida

Ejemplo básico ciclo de vida `onMounted` usando Composition API
```html
<script setup>
import { ref, onMounted } from 'vue'

const counter = ref(0)

onMounted(() => {
  console.log('onMounted')
})
</script>

<template>
  <p>
    Counter: {{ counter }}
  </p>
</template>
```

Ejemplo básico ciclo de vida `onMounted` usando Options API
```html
<script>
export default {
  name: 'Options',
  data() {
    return {
      counter: 0
    }
  },
  mounted() {
    console.log('mounted')
  },
}
</script>

<template>
  <p>
    Counter: {{ counter }}
  </p>
</template>
```

Ejemplo completo con varios ciclos de vida y su funcionalidad
```html
// App.vue
<script setup>
import { ref } from 'vue'
import Counter from './Counter.vue'

const showCounter = ref(true)

</script>

<template>
  <button @click="showCounter = !showCounter">
    Toggle contador
  </button>
  <Counter v-if="showCounter"></Counter>
</template>


// Counter.vue
<script setup>
import { ref, onUnmounted, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount } from 'vue'

const counter = ref(0)

console.log('created')

onBeforeMount(() => {
  // antes de montarse en el DOM
  console.log('onBeforeMount')
})
onMounted(() => {
  // al montarse en el DOM
  console.log('onMounted')
})
onBeforeUpdate(() => {
  // al detectar cualquier cambio en la instancia
  console.log('onBeforeUpdate')
})
onUpdated(() => {
  // al hacer cualquier cambio en la instancia
  console.log('onUpdated')
})
onBeforeUnmount(() => {
  // antes de desmontar la instancia
  console.log('onBeforeUnmount')
})
onUnmounted(() => {
  // al desmontar la instancia
  console.log('onUnmounted')
})
</script>

<template>
  <p>
    Counter: {{ counter }}
  </p>
  <button @click="counter++">
    Sumar
  </button>
</template>
```

Uso ciclo de vida created en Options API
```html
<script>
export default {
  name: 'Options',
  data() {
    return {
      counter: 0
    }
  },
  created() {
    console.log('created')
  },
}
</script>
<template>
  <p>
    Counter: {{ counter }}
  </p>
</template>
```
