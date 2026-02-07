<script setup>
    import { ref, onMounted } from 'vue'
    import { useRoute, useRouter } from 'vue-router'

    const route = useRoute();
    const router = useRouter();
    const product = ref(null);
    const emit = defineEmits(['add-to-cart']);

    onMounted(async () => {
        const res = await fetch(`https://dummyjson.com/products/${route.params.id}`);
        product.value = await res.json();
    })
</script>

<template>
    <div class="product-details" v-if="product">
        <button @click="router.push('/products')">Retour aux produits</button>
        
        <h1>{{ product.title }}</h1>
        
        <div class="gallery">
            <img v-for="img in product.images" :key="img" :src="img" width="100">
        </div>

        <p>{{ product.description }}</p>
        <p>Marque : {{ product.brand }}</p>
        <p>Catégorie : {{ product.category }}</p>
        <p>Prix : {{ product.price }} $ (-{{ product.discountPercentage }}%)</p>
        <p>Note : ⭐ {{ product.rating }}</p>
        <p>Stock : {{ product.stock }} restants</p>

        <button @click="emit('add-to-cart', product)">Ajouter au panier</button>
    </div>
    <p v-else>Chargement du produit...</p>
</template>
