<script setup>
import { ref } from 'vue'

const nome = ref('')
const idade = ref(10)
const email = ref('')

const mostrar = ref(false)
function processarForm(e) {
  mostrar.value = !mostrar.value
}

</script>

<template>
  <form @submit.prevent="processarForm">
    <input @input="mostrar = false" type="text" v-model="nome" minlength="3" maxlength="20" required>
    <input @input="mostrar = false" type="number" v-model="idade" required min="16" max="60">
    <input @input="mostrar = false" type="email" v-model="email" required>
    <button type="submit">Enviar</button>
    <div v-if="mostrar">
      <p>nome: {{ nome }}</p>
      <p>email: {{ email }}</p>
      <p>idade: {{ idade }}</p>
    </div>
  </form>
</template>

<style scoped></style>
