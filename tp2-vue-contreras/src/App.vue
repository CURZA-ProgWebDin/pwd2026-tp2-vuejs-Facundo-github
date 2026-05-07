<script setup>

import {ref, computed, reactive} from 'vue';
import ProductForm from './components/ProductForm.vue';
import ProductList from './components/ProductList.vue';

const state = reactive({
    productos: [],
    filtro: 'Todos'
})

let idCounter = 1

function crearProducto(nuevoProducto) {
    state.productos.push({
        ...nuevoProducto,
        id: Date.now()
    });
}

function eliminarProducto(id) {
    state.productos = state.productos.filter(p => p.id !== id)
}

const ProductosFiltrados = computed(() => {
    if (state.filtro === 'Todos') return state.productos
    return state.productos.filter(p => p.categoria === state.filtro)
})

const resumen = computed(() => ({
    total: state.productos.length,
    valorInventario: state.productos.reduce((acc, p) => acc + p.precio * p.stock , 0) 
}))

</script>

<template>
    
    <div class="container">
        <h1>Gestion de Productos</h1>
        <ProductForm @crear="crearProducto" />
        <ProductList
            :productos="ProductosFiltrados"
            @eliminar="eliminarProducto"
        />
        <p>Total Productos: {{ resumen.total }}</p>
        <p>Valor Inventario: {{ resumen.valorInventario }}</p>
    </div>

</template>

<style scoped>
.container {
    font-family: "Roboto", sans-serif;
    background-color: #f9f9f9;
    min-height: 100vh;
    padding: 20px;
}
h1{
    text-align: center;
    color: rgb(39, 34, 34);
}

</style>
