## Directiva `v-for`
[Link](https://vuejs.org/guide/essentials/list.html#v-for) a la documentación oficial.


### Ejemplo completo con número, array de strings y objeto usando la directiva `v-for`
```js
<script setup>
const number = 3
const names = ['Juan', 'Laura', 'Pepe', 'Paula']
const objectNumbers = { a: 1, b:2 }

</script>

<template>
  <h1>Ejemplo v-for</h1>
  
  <h4>Numbers</h4>
  <li v-for="n in number">{{ n }}</li>

  <h4>Arrays</h4>
  <p v-for="name in names">
    {{ name }}
  </p>
  
  <h4>Objects</h4>
  <li v-for="(n, key) in objectNumbers">
    {{ `${key} -> ${n}` }}
  </li>
</template>
```
