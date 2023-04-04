<script setup>
import { ref, computed } from 'vue'

const nome = ref('')
const idade = ref(10)
const email = ref('')
const senha01 = ref('')
const senha02 = ref('')

const mostrar = ref(false)

function processarForm(e) {
  if(senha01.value === senha02.value)
  { mostrar.value = true; 
    } 
  else {
    mostrar.value = false;
    alert('senha inválida');
   }
}

const msgErro = computed(() => {
  if (senha01.value != senha02.value) {
  return 'As senhas devem ser iguais'
  } else {
    return ''
  }
})


</script>

<template>
  <form @submit.prevent="processarForm" style="color: ;">
    <label for="nome">Nome:</label>
    <input type="text" v-model="nome" minlength="3" maxlength="20" required placeholder="Insira o nome">
    <br>
    <label for="idade">Idade:</label>
    <input type="number" v-model="idade" required min="16" max="60">
    <br>
    <label for="email">E-mail:</label>
    <input type="email" v-model="email" required>
    <br>
    <label for="senha01">Senha:</label>
    <input type="password" v-model="senha01" required>
    <br>
    <label for="senha02">Confirme sua senha:</label>
    <input type="password" v-model="senha02" required>
    <label for="dataNascimento">Data de nascimento</label>
    <input type="date" v-model="dataNascimento">
    <div>
      <p class="erro">{{ msgErro }}
      </p>
    </div>
<br>
    <button type="submit">Enviar</button>
    
    <div v-if="mostrar">
      <p>nome: {{ nome }}</p>
      <p>email: {{ email }}</p>
      <p>idade: {{ idade }}</p>
    </div>
  </form>
</template>

<style scoped>
.erro{
  color: red;
font-weight:bolder;
}
</style>
