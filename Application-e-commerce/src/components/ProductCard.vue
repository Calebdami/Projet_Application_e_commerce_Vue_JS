<script setup>
    defineProps(['product'])
    const emit = defineEmits(['add-to-cart'])
</script>

<template>
    <div>
        <img :src="product.thumbnail" :alt="product.title">
        <h3>{{ product.title }}</h3>
        <p>Prix : {{ product.price }} $</p>
        <p>Note : ⭐ {{ product.rating }}</p>
        <router-link :to="'/product/' + product.id"><button>Voir détails</button></router-link>
        <button @click="emit('add-to-cart', product)">Ajouter au panier</button>
    </div>
</template>