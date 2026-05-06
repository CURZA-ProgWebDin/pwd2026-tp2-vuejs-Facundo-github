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
    })
    nombre.value = precio.value = stock.value = categoria.value = ''
}

</script>

<template>

    <form @submit.prevent="submitForm">
        <input v-model="nombre" placeholder="Nombre" />
        <input v-model="precio" type="number" placeholder="precio" />
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