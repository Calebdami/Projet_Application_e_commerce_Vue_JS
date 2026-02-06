<script setup>
    import { ref, onMounted } from 'vue'
    import ProductCard from '../components/ProductCard.vue'

    const products = ref([]);
    const emit = defineEmits(['add-to-cart']);

    onMounted(async () => {
        const res = await fetch('https://dummyjson.com/products');
        const data = await res.json();
        products.value = data.products;
    })
</script>

<template>
    <div>
        <h1>Nos Produits</h1>
        <div v-if="products.length > 0">
            <ProductCard class="products-container" v-for="p in products" :key="p.id" :product="p" @add-to-cart="emit('add-to-cart', $event)"/>
        </div>
        <p v-else>Chargement...</p>
    </div>
</template>