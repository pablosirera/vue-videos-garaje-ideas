## Video 9. Provide / inject

Definición de componentes básicos para el ejemplo
```html
// App.vue
<script setup>
import { ref } from 'vue'
import BaseHeader from './BaseHeader.vue'

const msg = ref('Hello World!')
const links = [
  {
    url: '',
    name: 'Blog'
  },
  {
    url: '',
    name: 'About'
  },
]
</script>

<template>
  <BaseHeader :links="links" />
  <h1>{{ msg }}</h1>
</template>
```

```html
// BaseHeader.vue
<script setup>
import HeaderLinks from './HeaderLinks.vue'
defineProps({
  links: {
    type: Array,
    default: () => []
  }
})
</script>

<template>
  <header class="base-header">
    <img
      src="https://api.lorem.space/image/shoes?w=150&h=150&t=3"
    />

    <div>
      <HeaderLinks :links="links" />
    </div>
  </header>
</template>

<style scoped>
.base-header {
  border-bottom: 1px solid lightgray;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.base-header img {
  border-radius: 8px;
  width: 50px;
}
</style>
```

```html
// HeaderLinks.vue
<script setup>
defineProps({
  links: {
    type: Array,
    default: () => []
  }
})
</script>

<template>
  <a v-for="link in links" :href="link.url">
    {{ link.name }}
  </a>
</template>
```

Definir un provide dentro del `App.vue`
```js
import { provide } from 'vue'

provide('header-links', links)
```

Definir un inject dentro de `HeaderLinks.vue`
```js
import { inject } from 'vue'

const links = inject('header-links')
```

Modificar un provide desde un componente inferior
```js
// App.vue
const updateLinks = () => {
  links.value[2].name = 'Homeee'
}
provide('header-links', { links, updateLinks })

// HeaderLinks.vue
const { links, updateLinks } = inject('header-links')

const changeName = () => {
  updateLinks()
}
```