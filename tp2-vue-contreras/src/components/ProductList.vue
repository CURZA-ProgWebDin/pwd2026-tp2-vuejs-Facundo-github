<script setup>

import ProductItem from './ProductItem.vue';
const props = defineProps({productos: Array})
const emit = defineEmits(['eliminar'])

</script>

<template>

    <ul class="lista">
        <ProductItem
        v-for="p in productos"
        :key="p.id"
        :producto="p"
        @eliminar="emit('eliminar', p.id)"
        />
    </ul>

</template>

<style scoped>
.lista {
    margin-top: 20px;
    list-style: none;
    padding: 0;
    display: flex;
    flex-direction: column;
    gap: 10px;
}
</style>