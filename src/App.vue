<script setup>
import { reactive } from 'vue';
import InputForm from './components/InputForm.vue';
import Seletor from './components/Seletor.vue'


const estado = reactive({
  operador: 'somar',
  input1: 0,
  input2: 0,
  resultado: 0,
  desktop: true
})

const calcular = () => {
  if (estado.operador == 'somar') {
    return estado.resultado = parseInt(estado.input1) + parseInt(estado.input2)
  } else if (estado.operador == 'subtrair') {
    return estado.resultado = estado.input1 - estado.input2
  } else if (estado.operador == 'dividir') {
    return estado.resultado = estado.input1 / estado.input2
  } else if (estado.operador == 'multiplicar') {
    return estado.resultado = estado.input1 * estado.input2
  }
}

const screenWidth = window.innerWidth
</script>
<template>
  <div v-if="screenWidth < 768">
    <div class="container">
      <div class="row">
        <div class="col">
          <h1 class="text-center mb-5">Calculadora</h1>
        </div>
      </div>
      <div class="row ">
        <div class="col-12">
          <InputForm :calcular="calcular" :operador="estado.operador"
            :input1="evento => estado.input1 = evento.target.value"
            :input2="evento => estado.input2 = evento.target.value" />
        </div>
        <div class="col-12 mt-2">
          <h2 class="text-center">Resultado:</h2>
          <h2 class="text-center">{{ estado.resultado }}</h2>
        </div>
        <div class="col-12">
          <Seletor :calcular="calcular" :set-operador="evento => estado.operador = evento.target.value" />
        </div>
      </div>
    </div>
  </div>
  <div v-else>
    <div class="container">
      <div class="row">
        <div class="col">
          <h1 class="text-center mb-5">Calculadora</h1>
        </div>
      </div>
      <div class="row mt-5">
        <div class="col-6 d-flex">
          <InputForm :calcular="calcular" :operador="estado.operador"
            :input1="evento => estado.input1 = evento.target.value"
            :input2="evento => estado.input2 = evento.target.value" />
        </div>
        <div class="col-1 pt-2">
          <h2 class="text-center">=</h2>
        </div>
        <div class="col-1 pt-2">
          <h2>{{ estado.resultado }}</h2>
        </div>
        <div class="col-4">
          <Seletor :calcular="calcular" :set-operador="evento => estado.operador = evento.target.value" />
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.container {
  margin-top: 10vw;
}
</style>