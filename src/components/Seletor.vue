<script setup>
    const props = defineProps(['calcular', 'setOperador',])
</script>
<template>
    <select v-change="props.calcular" @change="props.setOperador"
        class="form-select text-center p-3">
        <option value="somar">Somar</option>
        <option value="subtrair">Subtrair</option>
        <option value="dividir">Dividir</option>
        <option value="multiplicar">Multiplicar</option>
    </select>
</template>