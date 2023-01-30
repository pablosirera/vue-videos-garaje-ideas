## Video 14. Transitions

Ejemplo básico del uso del componente `Transition`:
```html
<script setup>
import { ref } from 'vue'
const show = ref(true)
</script>

<template>
  <div>
    <button @click="show = !show">Toggle</button>
    <Transition>
      <p v-if="show">Hello World</p>
    </Transition>
  </div>
</template>

<style>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
```

Ejemplo haciendo uso del atributo `name` en el componente `Transition`
```html
<script setup>
import { ref } from 'vue'
const show = ref(true)
</script>

<template>
  <div>
    <button @click="show = !show">Toggle</button>
    <Transition name="fade">
      <p v-if="show">Hello World</p>
    </Transition>
  </div>
</template>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
```

Ejemplo eliminando y añadiendo nuevos elementos haciendo uso del componente `TransitionGroup`
```html
<script setup>
import { ref } from 'vue'
const items = ref(['Pablo', 'Luis', 'Maria'])

const add = () => {
  items.value.push(Math.floor(Math.random() * 100))
}
const remove = () => {
  items.value.splice(Math.floor(Math.random() * items.value.length), 1)
}
</script>

<template>
  <button @click="add()">
    Add random number
  </button>
  <button @click="remove()">
    Remove random number
  </button>
  <TransitionGroup name="list" tag="ul">
    <li v-for="item in items" :key="item">
      {{ item }}
    </li>
  </TransitionGroup>
</template>

<style>
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>
```

Modificar el nombre de las clases de transiciones por defecto
```html
<script setup>
import { ref } from 'vue'
const show = ref(true)
</script>

<template>
  <button @click="show = !show">Toggle</button>
  <Transition
    name="custom-classes"
    enter-active-class="animate__animated animate__tada"
    leave-active-class="animate__animated animate__bounceOutRight"
  >
    <p v-if="show">hello</p>
  </Transition>
</template>

<style>
@import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css";
</style>
```