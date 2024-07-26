  <script setup>
  import { computed } from 'vue'
  import { defineProps } from 'vue'
  
  const props = defineProps({
    user: Object
  })
  
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
  
  const estadoName = computed(() => {
    const estado = estados.find(e => e.sigla === props.user.estado)
    return estado ? estado.name : 'Desconhecido'
  })
  </script>

<template>
  <div class="user-info">
    <h2>Informações do Usuário</h2>
    <p><strong>Nome:</strong> {{ user.nome }}</p>
    <p><strong>E-mail:</strong> {{ user.email }}</p>
    <p><strong>Data de Nascimento:</strong> {{ user.nascimento }}</p>
    <p><strong>Idade:</strong> {{ user.idade }}</p>
    <p><strong>Estado:</strong> {{ estadoName }}</p>
    <p><strong>Cidade:</strong> {{ user.cidade }}</p>
    <p><strong>Endereço:</strong> {{ user.endereco }}</p>
    <p><strong>Hobbies:</strong> {{ user.hobbies.join(', ') }}</p>
    <p><strong>Linguagens:</strong> {{ user.linguagens.join(', ') }}</p>
    <p><strong>Biografia:</strong> {{ user.biografia }}</p>
  </div>
</template>
  
<style scoped>
.user-info {
  max-width: 900px;
  margin: 30px auto;
  padding: 30px;
  background-color: #ffffff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h2 {
  color: #333;
  margin-bottom: 20px;
  font-size: 24px;
}

p {
  font-size: 16px;
  color: #555;
  margin-bottom: 10px;
}

strong {
  color: #333;
}

  </style>
  