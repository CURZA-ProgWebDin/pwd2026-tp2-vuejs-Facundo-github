<script setup>

import ProductItem from './ProductItem.vue';
const props = defineProps({productos: Array})
const emit = defineEmits(['eliminar'])

</script>

<template>

    <ul>
        <ProductItem
        v-for="p in productos"
        :key="p.id"
        :producto="p"
        @eliminar="emit('eliminar', p.id)"
        />
    </ul>

</template>

<style>
</style>