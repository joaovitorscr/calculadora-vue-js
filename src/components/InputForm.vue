<script setup>
    const props = defineProps(['operador', 'input1', 'input2', 'calcular'])
</script>

<template>
    <input @keyup="props.input1" type="number" class="form-control text-center">
    <h2 v-if="props.operador == 'somar'" class="ms-4 me-4 pt-2">+</h2>
    <h2 v-else-if="props.operador == 'subtrair'" class="ms-4 me-4 pt-2">-</h2>
    <h2 v-else-if="props.operador == 'dividir'" class="ms-4 me-4 pt-2">÷</h2>
    <h2 v-else-if="props.operador == 'multiplicar'" class="ms-4 me-4 pt-2">x</h2>
    <input v-on:change="props.calcular" @keyup="props.input2" type="number"
        class="form-control text-center">
</template>