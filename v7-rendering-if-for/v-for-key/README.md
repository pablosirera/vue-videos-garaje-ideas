## Directiva `v-for` y atributo `key`
[Link](https://vuejs.org/guide/essentials/list.html#maintaining-state-with-key) a la documentación oficial.


### Ejemplo básico usando directiva v-for y el atributo key
```js
<script setup>
const names = ['Juan', 'Laura', 'Pepe', 'Paula']
</script>

<template>
  <h1>Ejemplo v-for con atributo key</h1>
  
  <li v-for="(n, key) in names" :key="key">
    {{ `${key} -> ${n}` }}
  </li>
</template>
```
