<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps(['pessoaFinal']);
const emit = defineEmits(['editar']);

function editar() {
  emit('editar'); 
}
</script>

<template>
  <div class="usuario">
    <p>Nome: {{ pessoaFinal.nome }}</p>
    <p>Idade: {{ pessoaFinal.idade }}</p>
    <p>Email: {{ pessoaFinal.email }}</p>
    <p>Senha: {{ pessoaFinal.senha }}</p>
    <p>Nascimento: {{ pessoaFinal.nascimento }}</p>
    <p>Estado: {{ pessoaFinal.estado }}</p>
    <p>Cidade: {{ pessoaFinal.cidade }}</p>
    <p>Endereço: {{ pessoaFinal.endereco }}</p>
    <p>Hobbies: {{ pessoaFinal.hobbies.join(', ') }}</p>
    <p>Linguagens: {{ pessoaFinal.linguagens.join(', ') }}</p>
    <p>Autobiografia: {{ pessoaFinal.biografia }}</p>
    <button @click="editar" class="custom-submit">Voltar</button>
  </div>
</template>

<style scoped>
.usuario {
  display: flex;
  justify-content: center;
  flex-direction: column;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  border-radius: 15px;
  width: 500px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-weight: normal;
  line-height: 1.5;
  align-items: center;
  padding: 30px;
}

p {
  color: rgb(0, 0, 0);
  margin-top: 10px;
}

button {
  cursor: pointer;
  background-color: black;
  color: white;
  border: none;
  margin-top: 70px;
  border-radius: 10px;
  width: 150px;
  height: 50px;
}
</style>