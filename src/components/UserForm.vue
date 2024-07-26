  <script setup>
  import { ref, reactive, watch } from 'vue'
  import { defineProps, defineEmits } from 'vue'
  
  const props = defineProps({
    user: Object
  })
  
  const emit = defineEmits(['update-user'])
  
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
  
  const localUser = reactive({ ...props.user })
  const senhaVerificada = ref('')
  
  watch(() => props.user, (newUser) => {
    Object.assign(localUser, newUser)
  })
  
  function handleSubmit() {
    if (senhaVerificada.value === localUser.senha) {
      emit('update-user', localUser)
    } else {
      alert('As senhas não correspondem!')
      document.getElementById('senhaConfirma').focus()
    }
  }
  </script>

<template>
  <form @submit.prevent="handleSubmit">
    <div class="custom-input-container">
      <label for="nome">Nome:</label>
      <input type="text" v-model="localUser.nome" required minlength="3" maxlength="20" />
    </div>

    <div class="custom-input-container">
      <label for="email">E-mail:</label>
      <input type="email" v-model="localUser.email" required />
    </div>

    <div class="custom-input-container">
      <label for="senha">Senha:</label>
      <input type="password" v-model="localUser.senha" required minlength="8" />
    </div>

    <div class="custom-input-container">
      <label for="senhaConfirma">Confirmação de senha:</label>
      <input type="password" id="senhaConfirma" v-model="senhaVerificada" required minlength="8" />
    </div>

    <div class="custom-input-container">
      <label for="nascimento">Data de nascimento:</label>
      <input type="date" v-model="localUser.nascimento" required />
    </div>

    <div class="custom-input-container">
      <label for="idade">Idade:</label>
      <input type="number" v-model="localUser.idade" min="18" max="60" required />
    </div>

    <div class="custom-input-container">
      <label for="estado">Estado:</label>
      <select v-model="localUser.estado" required>
        <option v-for="estado in estados" :key="estado.sigla" :value="estado.sigla">
          {{ estado.name }}
        </option>
      </select>
    </div>

    <div class="custom-input-container">
      <label for="cidade">Cidade:</label>
      <input type="text" v-model="localUser.cidade" />
    </div>

    <div class="custom-input-container">
      <label for="endereco">Endereço:</label>
      <input type="text" v-model="localUser.endereco" />
    </div>

    <div class="custom-check-container">
      <label>Hobbies:</label>
      <div v-for="hobbie in hobbies" :key="hobbie.id">
        <input type="checkbox" :value="hobbie.hobbie" v-model="localUser.hobbies" :id="hobbie.hobbie" />
        <label :for="hobbie.hobbie">{{ hobbie.hobbie }}</label>
      </div>
    </div>

    <div class="custom-check-container">
      <label>Linguagens:</label>
      <div v-for="linguagem in linguagens" :key="linguagem.id">
        <input type="checkbox" :value="linguagem.tipo" v-model="localUser.linguagens" :id="linguagem.tipo" />
        <label :for="linguagem.tipo">{{ linguagem.tipo }}</label>
      </div>
    </div>

    <div class="custom-bio-container">
      <label for="biografia">Biografia:</label>
      <textarea v-model="localUser.biografia"></textarea>
    </div>

    <div class="custom-submit-container">
      <input type="submit" value="Enviar dados" class="custom-submit" />
    </div>
  </form>
</template>
  
  <style scoped>

  custom-input-container
.custom-form {
  max-width: 900px;
  margin: 30px auto;
  padding: 30px;
  background-color: #ffffff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #333;
  margin-bottom: 20px;
  font-size: 24px;
}

.custom-input-container {
  margin-bottom: 20px;
}

label {
  display: block;
  padding: 40px;
  font-size: 16px;
  margin-bottom: 5px;
  color: #555;
}

input[type='text'],
input[type='email'],
input[type='password'],
input[type='number'],
input[type='date'],
textarea,
select {
  width: 100%;
  padding: 12px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #ddd;
  box-sizing: border-box;
}

input[type='checkbox'] {
  margin-right: 10px;
}

.custom-check-container {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
}

.custom-checkbox {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.custom-bio-container {
  margin-bottom: 20px;
}

textarea {
  height: 120px;
}

.custom-submit-container {
  text-align: center;
}

.custom-submit {
  padding: 12px 20px;
  font-size: 18px;
  color: white;
  background-color: #61287c;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.custom-submit:hover {
  background-color: #7c4396;
}

.usuario > p {
  color: #333;
  padding: 5px;
  margin-bottom: 10px;
  border-bottom: 1px solid #ddd;
}

  </style>
  