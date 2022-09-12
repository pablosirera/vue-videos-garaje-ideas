## Video 8. Componentes con Vuejs

Componente `BaseInput.vue` con validación de props
```html
<script setup>
defineProps({
  type: {
    type: String,
    default: 'text',
    validator: value => ['text', 'email'].includes(value)
  }
})
const emit = defineEmits(['update'])

const saveValue = (event) => {
  emit('update', event.target.value)
}
</script>

<template>
  <input :type="type" name="input" @input="saveValue">
</template>

<style scoped>
input {
  padding: 5px 8px;
}
</style>
```

Ejemplo `App.vue` usando el componente creado `BaseInput.vue`
```html
<script setup>
import BaseInput from './BaseInput.vue'

const saveValue = value => {
  alert(value)
}
</script>

<template>
  <h1>Ejemplo Componentes</h1>
  <BaseInput @update="saveValue"/>
</template>
```