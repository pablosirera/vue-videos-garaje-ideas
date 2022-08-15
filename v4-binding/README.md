## Video 4. Binding Atributos

Ejemplo básico con imagen en atributo src
```js
<script setup></script>

<template>
  <img src="https://bit.ly/3yN7z3B" class="w-24" />
</template>

<style>
.w-24 {
  width: 24rem;
}
</style>
```

Ejemplo usando v-bind en src y class de una imagen
```js
<script setup>
const image = 'https://bit.ly/3yN7z3B'
const imgClasses = 'w-24'
</script>

<template>
  <img
    v-bind:src="image"
    v-bind:class="imgClasses"
  />
</template>

<style>
.w-24 {
  width: 24rem;
}
</style>
```

Ejemplo completo cambiando el valor de src dinámicamente
```js
<script setup>
import { ref } from 'vue'

const images = ['https://bit.ly/3yN7z3B', 'https://bit.ly/3OhIC5P']
const image = ref(images[0])
const imgClasses = 'w-24'

const selectImage = (index) => {
  image.value = images[index]
}
</script>

<template>
  <img
    :src="image"
    :class="imgClasses"
  />
  <div>
    <button @click="selectImage(0)">
      Imagen 1
    </button>
    <button @click="selectImage(1)">
      Imagen 2
    </button>
  </div>
</template>

<style>
.w-24 {
  width: 24rem;
}
</style>
```

Ejemplo básico binding en style
```js
<script setup>
const buttonStyles = 'background-color:red'
</script>

<template>
  <button :style="buttonStyles">
    Botón
  </button>
</template>

<style>
.w-24 {
  width: 24rem;
}
</style>
```
