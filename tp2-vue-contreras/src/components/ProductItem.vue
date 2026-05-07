<script setup>
const props = defineProps({producto: Object })
const emit = defineEmits(['eliminar'])
</script>

<template>
    <li class="producto">
        <span class="nombre">{{ producto.nombre }}</span>
        <span class="precio">$ {{ producto.precio }}</span>
        <span class="stock">Stock:{{ producto.stock }}</span>
        <button class="eliminar" @click="emit('eliminar', producto.id)">Eliminar</button>
    </li>
</template>

<style scoped>

.producto{
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #ccc;
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 6px;
    
}
.nombre, .precio, .stock{
    color: black;
    flex: 1;
    text-align: left;
}

.eliminar {
    background-color: #e74c3c;
    border: none;
    color: white;
    padding: 8px 12px;
    border-radius: 4px;
    cursor: pointer;
}
.eliminar:hover{
    background-color: #c0392b;
}
</style>