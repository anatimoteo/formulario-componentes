<template>
  <div class="app">
    <button @click="toggleForm">{{ showForm ? 'Mostrar Informações' : 'Mostrar Formulário' }}</button>
    
    <UserForm v-if="showForm" :user="user" @update-user="updateUser" />
    <UserInfo v-else :user="user" />
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import UserForm from './components/UserForm.vue'
import UserInfo from './components/UserInfo.vue'

const estados = [
  { sigla: 'AC', name: 'Acre' },
  { sigla: 'AL', name: 'Alagoas' },
  { sigla: 'AP', name: 'Amapá' },
  { sigla: 'AM', name: 'Amazonas' },
  { sigla: 'BA', name: 'Bahia' },
  { sigla: 'CE', name: 'Ceará' },
  { sigla: 'DF', name: 'Distrito Federal' },
  { sigla: 'ES', name: 'Espírito Santo' },
  { sigla: 'GO', name: 'Goiás' },
  { sigla: 'MA', name: 'Maranhão' },
  { sigla: 'MT', name: 'Mato Grosso' },
  { sigla: 'MS', name: 'Mato Grosso do Sul' },
  { sigla: 'MG', name: 'Minas Gerais' },
  { sigla: 'PA', name: 'Pará' },
  { sigla: 'PB', name: 'Paraíba' },
  { sigla: 'PR', name: 'Paraná' },
  { sigla: 'PE', name: 'Pernambuco' },
  { sigla: 'PI', name: 'Piauí' },
  { sigla: 'RJ', name: 'Rio de Janeiro' },
  { sigla: 'RN', name: 'Rio Grande do Norte' },
  { sigla: 'RS', name: 'Rio Grande do Sul' },
  { sigla: 'RO', name: 'Rondônia' },
  { sigla: 'RR', name: 'Roraima' },
  { sigla: 'SC', name: 'Santa Catarina' },
  { sigla: 'SP', name: 'São Paulo' },
  { sigla: 'SE', name: 'Sergipe' },
  { sigla: 'TO', name: 'Tocantins' }
]

const hobbies = [
  { id: 1, hobbie: 'Esporte' },
  { id: 2, hobbie: 'Ler' },
  { id: 3, hobbie: 'Cozinhar' },
  { id: 4, hobbie: 'Viajar' }
]

const linguagens = [
  { id: 1, tipo: 'Java' },
  { id: 2, tipo: 'C++' },
  { id: 3, tipo: 'Python' },
  { id: 4, tipo: 'PHP' }
]

const user = reactive({
  nome: '',
  idade: 18,
  email: '',
  senha: '',
  nascimento: '',
  estado: '',
  cidade: '',
  endereco: '',
  hobbies: [],
  linguagens: [],
  biografia: ''
})

const showForm = ref(true)

function toggleForm() {
  showForm.value = !showForm.value
}

function updateUser(updatedUser) {
  Object.assign(user, updatedUser)
}
</script>

<style>
.app {
  font-family: Arial, sans-serif;
  text-align: center;
  background-color: #f0f2f5;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  border-radius: 5px;
  color: white;
  background-color: #61287c;
  cursor: pointer;
  margin: 10px;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #7c4396;
}

</style>
