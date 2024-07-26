<script setup>
import { ref } from 'vue';
import Formulario from './components/Formulario.vue';
import Resultado from './components/Resultado.vue';

const exibirFormulario = ref(true);
const usuario = ref({});

function mostrarResultado(pessoa) {
  usuario.value = pessoa;
  exibirFormulario.value = false;
}

function voltarParaFormulario() {
  exibirFormulario.value = true;
}
</script>

<template>
  <div class="all">
    <div class="container">
      <div class="form1" v-if="exibirFormulario">
        <Formulario @salvar="mostrarResultado"  />
      </div>
      <div class="result" v-else>
        <Resultado :pessoaFinal="usuario" @editar="voltarParaFormulario"  />
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40%;
}

.all {
  display: flex;
  justify-content: center;
  width: 100%;
  height: 130vh;

}
</style>