## Video 5. Form Binding

Ejemplo formulario básico sin usar directiva `v-model`
```html
<script setup>
</script>

<template>
  <form @submit.prevent="onSubmit()" class="contact-form">
    <h3>
      Contáctame
    </h3>
    <label for="name">Name:</label>
    <input id="name">

    <label for="msg">Mensaje:</label>      
    <textarea id="msg"></textarea>

    <label for="location">Localidad:</label>
    <select id="location">
      <option disabled value="">Please select one</option>
      <option>Spain</option>
      <option>France</option>
    </select>
    
    <label for="accept">Aceptas:</label>
    <input id="accept" type="checkbox">
    
    <button class="button" type="submit">Enviar</button>
  </form>
</template>

<style scoped>
  .contact-form {
    display: flex;
    flex-direction: column;
    width: 50%;
    border: 1px solid lightgrey;
    padding: 20px;
    border-radius: 8px;
  }
  .contact-form label {
    margin-top: 10px;
  }
  .contact-form .button {
    margin-top: 20px;
  }
</style>
```

Ejemplo formulario usando la directiva `v-model`
```html
<script setup>
import { ref } from 'vue'

const name = ref('')
const msg = ref('')
const location = ref(null)
const accept = ref(false)
</script>

<template>
  <form @submit.prevent="onSubmit()" class="contact-form">
    <h3>
      Contáctame
    </h3>
    <label for="name">Name:</label>
    <input v-model="name" id="name">

    <label for="msg">Mensaje:</label>      
    <textarea v-model="msg" id="msg"></textarea>

    <label for="location">Pais:</label>
    <select id="location" v-model="location">
      <option disabled value="">Please select one</option>
      <option>Spain</option>
      <option>France</option>
    </select>
    
    <label for="accept">Aceptas:</label>
    <input id="accept" type="checkbox" v-model="accept">
    
    <button class="button" type="submit">Enviar</button>
  </form>
  
  <pre>
    Nombre: {{ name }}
    Mensaje: {{ msg }}
    Pais: {{ location }}
    Acepta: {{ accept }}
  </pre>
</template>
```

Método de submit para agrupar valores de un formulario
```js
const onSubmit = () => {
  const form = {
    name: name.value,
    message: msg.value,
    location: locations.value,
    accept: accept.value,
  }
}
```