<script setup>
import { ref, computed } from 'vue'

const nome = ref('')
const idade = ref(16)
const email = ref('')
const senha01 = ref('')
const senha02 = ref('')
const dataNascimento = ref()
const endereco = ref('')
const cidade = ref('')
const estado = ref('')
const hobbies = ref('')
const linguagensProgramacao = ref('')
const biografia = ref('')




const mostrar = ref(false)

function processarForm(e) {
  if (senha01.value === senha02.value) {
    mostrar.value = true;
  }
  else {
    mostrar.value = false;
    // alert('senha inválida');
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
  <div v-if="mostrar">
    <p>nome: {{ nome }}</p>
    <p>email: {{ email }}</p>
    <p>Vocé é maior de idade</p>
    <p>Data de nascimento {{ dataNascimento }}</p>
    <p>Endereço {{ endereco }}</p>
    <p>estado: {{ estado }}</p>
    <p>cidade:{{ cidade }}</p>
    <p>linguagens de programação:{{ linguagensProgramacao }}</p>
    <P>hobbies: {{ hobbies }}</P>
    <p>biografia: {{ biografia }}</p>
  </div>
  <div v-else>
    <form @submit.prevent="processarForm" class="form">
      <label for="nome">Nome:</label>
      <input type="text" v-model="nome" minlength="3" maxlength="20" required placeholder="Insira o nome">
      <label for="idade">Você é maior de idade? </label>
      <input type="checkbox" v-model="idade" required>

      <label for="dataNascimento">Data de nascimento</label>
      <input type="date" min="1923-01-01" max="2007-04-16" v-model="dataNascimento" required>
      <label for="email">E-mail:</label>
      <input type="email" v-model="email" required>
      <label for="endereco">Qual seu endereço?</label>
      <input type="text" v-model="endereco" minlength="3">
      <label for="estado">Estado</label>
      <select v-model="estado" required>
        <option value="AC">ACRE</option>
        <option value="AL">ALAGOAS</option>
        <option value="AP">AMAPÁ</option>
        <option value="AM">AMAZONAS</option>
        <option value="BA">BAHIA</option>
        <option value="CE">CEARÁ</option>
        <option value="DF">DISTRITO FEDERAL</option>
        <option value="ES">ESPIRITO SANTO</option>
        <option value="GO">GOIÁS</option>
        <option value="MA">MARANHÃO</option>
        <option value="MT">MATO GROSSO</option>
        <option value="MS">MATO GROSSO DO SUL</option>
        <option value="MG">MINAS GERAIS</option>
        <option value="PA">PARÁ</option>
        <option value="PB">PARAIBA</option>
        <option value="PR">PARANÁ</option>
        <option value="PE">PERNAMBUCO</option>
        <option value="PI">PIAUÍ</option>
        <option value="RJ">RIO DE JANEIRO</option>
        <option value="RN">RIO GRANDE DO NORTE</option>
        <option value="RS">RIO GRANDE DO SUL</option>
        <option value="RO">RONDONIA</option>
        <option value="RR">RORAIMA</option>
        <option value="SC">SANTA CATARINA</option>
        <option value="SP">SÃO PAULO</option>
        <option value="SE">SERGIPE</option>
        <option value="TO">TOCANTINS</option>
      </select>


      <label for="cidade">Cidade:</label>
      <input type="text" v-model="cidade" required>
      <label for="biografia">Biografia</label>
      <textarea cols="30" rows="10" v-model="biografia"></textarea>
      <label for="hobbies">Hobbies</label>
      <input type="text" v-model="hobbies" required>
      <label for="linguagemProgramacao">linguagens De Programação</label>
      <input type="text" v-model="linguagensProgramacao" required>
      <label for="senha01">Senha:</label>
      <input type="password" v-model="senha01" required>
      <label for="senha02">Confirme sua senha:</label>
      <input type="password" v-model="senha02" required>
      <div>
        <p class="erro">{{ msgErro }}
        </p>
      </div>
      <button type="submit">Enviar</button>
    </form>
  </div>
</template>

<style scoped>
.erro {
  color: red;
  font-weight: bolder;
}

.form {
  display: grid;
  grid-template-columns: 1fr;
  width: 450px;
  height: 800px;
}

.form {
  background-color: rgb(0, 255, 149);
  padding: 40px;
  border-radius: 10px;
}
</style>
