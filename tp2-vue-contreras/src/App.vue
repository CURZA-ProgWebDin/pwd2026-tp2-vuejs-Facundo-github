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

    <h1>Gestion de Productos</h1>
    <ProductForm @crear="crearProducto" />
    <ProductList
        :productos="ProductosFiltrados"
        @eliminar="eliminarProducto"
    />
    <p>Total Productos: {{ resumen.total }}</p>
    <p>Valor Inventario: {{ resumen.valorInventario }}</p>

</template>
