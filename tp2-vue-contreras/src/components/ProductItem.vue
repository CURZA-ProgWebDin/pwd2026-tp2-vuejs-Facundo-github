<script setup>
const props = defineProps({producto: Object })
const emit = defineEmits(['eliminar'])
</script>

<template>
    <li>
        {{ producto.nombre }} - ${{ producto.precio }} - Stock:{{ producto.stock }} - 
        <button @click="emit('eliminar', producto.id)">Eliminar</button>
    </li>
</template>

<style>
</style>