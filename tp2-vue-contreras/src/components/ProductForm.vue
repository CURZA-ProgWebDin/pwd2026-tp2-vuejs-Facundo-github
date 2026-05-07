<script setup>
import { ref } from 'vue';
const nombre = ref('')
const precio = ref('')
const stock = ref('')
const categoria = ref('')

const emit = defineEmits(['crear'])

function submitForm() {
    if (!nombre.value || !precio.value || !stock.value || !categoria.value) {
        alert('Todos los campos son obligatorios')
        return
    }
    emit('crear', {
        nombre: nombre.value,
        precio: Number(precio.value),
        stock: Number(stock.value),
        categoria: categoria.value
    });
    
    nombre.value = '';
    precio.value = '';
    stock.value = '';
    categoria.value = '';
}

</script>

<template>

    <form @submit.prevent="submitForm">
        <input v-model="nombre" placeholder="Nombre" />
        <input v-model="precio" type="number" placeholder="Precio" />
        <input v-model="stock" type="number" placeholder="Stock"/>
        <select v-model="categoria">
            <option disabled value="">Seleccione Categoria</option>
            <option>Electronica</option>
            <option>Ropa</option>
            <option>Alimentos</option>  
        </select>
        <button type="submit">Agregar</button>        
    </form>

</template>

<style scoped>

form{
    display: grid;
    grid-template-columns: auto;
    gap: 20px;
}

input, select {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 6px;
}

button {
    grid-column: span 2;
    background-color: #acf789;
    color: rgb(15, 10, 10);
    border: none;
    padding: 12px;
    border-radius: 6px;
    cursor: pointer;
    
}
button:hover {
    background-color: #45a049;
}

</style>