<script setup>
import { ref, reactive, defineEmits } from 'vue';

const emit = defineEmits(['salvar']);

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
];

const hobbies = reactive([
  { id: 1, hobbie: 'Esporte' },
  { id: 2, hobbie: 'Ler' },
  { id: 3, hobbie: 'Cozinhar' },
  { id: 4, hobbie: 'Viajar' }
]);

const linguagens = reactive([
  { id: 1, tipo: 'JavaScript' },
  { id: 2, tipo: 'C#' },
  { id: 3, tipo: 'Python' },
  { id: 4, tipo: 'PHP' }
]);

const pessoa = reactive({
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
});

const senhaVerificada = ref('');

function enviarDados() {
  if (senhaVerificada.value === pessoa.senha) {
    emit('salvar', { ...pessoa });
  } else {
    alert('As senhas não correspondem corretamente!');
    document.getElementById('senhaConfirma').focus();
  }
}
</script>

<template>
  <div class="custom-form">
    <h1>Formulário</h1>
    <form @submit.prevent="enviarDados">
      <div class="custom-input-container">
        <label for="nome"><i>Digite seu nome:</i></label>
        <input type="text" v-model="pessoa.nome" minlength="3" maxlength="20" autocomplete="on" required />
      </div>

      <div class="custom-input-container">
        <label for="email"><i>Digite seu email:</i></label>
        <input v-model="pessoa.email" placeholder="Por favor, insira um email válido!" type="email" required />
      </div>

      <div class="custom-input-container">
        <label for="senha"><i>Digite sua senha:</i></label>
        <input type="password" v-model="pessoa.senha" minlength="8" required />
      </div>

      <div class="custom-input-container">
        <label for="senhaConfirma"><i>Confirme sua senha:</i></label>
        <input type="password" id="senhaConfirma" v-model="senhaVerificada" minlength="8" required />
      </div>

      <div class="custom-input-container">
        <label for="date"><i>Data de nascimento:</i></label>
        <input v-model="pessoa.nascimento" type="date" required />
      </div>

      <div class="custom-input-container">
        <label for="idade"><i>Digite sua idade:</i></label>
        <input type="number" v-model="pessoa.idade" min="18" max="60" required />
      </div>

      <div class="custom-input-container">
        <label for="estado"><i>Informe seu estado:</i></label>
        <select v-model="pessoa.estado">
          <option v-for="estado in estados" :key="estado.sigla" :value="estado.sigla">
            {{ estado.name }}
          </option>
        </select>
      </div>

      <div class="custom-input-container">
        <label for="cidade"><i>Informe sua cidade:</i></label>
        <input type="text" v-model="pessoa.cidade" />
      </div>

      <div class="custom-input-container">
        <label for="endereco"><i>Informe seu endereço:</i></label>
        <input type="text" v-model="pessoa.endereco" />
      </div>

      <div class="OrgCheckBox">
        <div class="custom-check-container">
          <label><i>Selecione seus hobbies:</i></label>
          <div class="custom-checkbox" v-for="passatempo in hobbies" :key="passatempo.id">
            <input type="checkbox" :value="passatempo.hobbie" v-model="pessoa.hobbies" :id="passatempo.hobbie" />
            <label :for="passatempo.hobbiei"><i>{{ passatempo.hobbie }}</i></label>
          </div>
        </div>

        <div class="custom-check-container">
          <label><i>Selecione as suas linguagens favoritas:</i></label>
          <div class="custom-checkbox" v-for="linguagem in linguagens" :key="linguagem.id">
            <input type="checkbox" :value="linguagem.tipo" v-model="pessoa.linguagens" :id="linguagem.tipo" />
            <label :for="linguagem.tipoi"><i>{{ linguagem.tipo }}</i></label>
          </div>
        </div>
      </div>
      <div class="custom-bio-container">
        <label for="biografia"><i>Fale um pouco sobre você:</i></label>
        <textarea v-model="pessoa.biografia"></textarea>
      </div>

      <div class="custom-submit-container">
        <input type="submit" @click="enviarDados" value="Enviar dados" class="custom-submit" />
      </div>
    </form>
  </div>
</template>

<style scoped>

.custom-form {
  margin: 30px auto;
  padding: 20px;
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

i {
  color: #000000;
}

h1 {
  text-align: center;
  color: #000;
  margin-bottom: 20px;
}

.custom-input-container {
  margin-bottom: 15px;
}

label {
  display: block;
  font-size: 18px;
  margin-bottom: 5px;
  color: #0000;
}

input[type='text'],
input[type='email'],
input[type='password'],
input[type='number'],
input[type='date'],
textarea,
select {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #000000;
}

.custom-check-container {
  margin-bottom: 15px;
}

.custom-checkbox {
  display: flex;
  align-items: center;
  margin-bottom: 5px;
}

.custom-checkbox input {
  margin-right: 10px;
}

.custom-bio-container {
  margin-bottom: 15px;
}

textarea {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid black;
}

.custom-submit-container {
  text-align: center;
}

.custom-submit {
  width: 200px;
  padding: 10px;
  background-color: #fff7e8;
  color: black;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 18px;
}

.custom-submit:hover {
  border: 1px solid black;
}

.usuario>p {
  color: white;
  padding: 3px;
  margin-bottom: 10px;
}

.OrgCheckBox{
  display: flex;
  width: 100%;
  gap: 30%;
  justify-content: center;
}
</style>