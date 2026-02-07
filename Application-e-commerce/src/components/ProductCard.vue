<script setup>
    defineProps(['product'])
    const emit = defineEmits(['add-to-cart'])
</script>

<template>
    <div class="product-card">
        <img :src="product.thumbnail" :alt="product.title">
        <h3>{{ product.title }}</h3>
        <p>Prix : {{ product.price }} $</p>
        <p>Note : ⭐ {{ product.rating }}</p>
        <div class="actions">
            <router-link :to="'/product/' + product.id"><button>Voir détails</button></router-link>
            <button @click="emit('add-to-cart', product)">Ajouter au panier</button>
        </div>
    </div>
</template>
