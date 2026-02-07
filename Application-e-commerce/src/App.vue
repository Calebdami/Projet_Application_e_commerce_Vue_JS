<script setup>
    import { reactive } from 'vue'

    // État global du panier
    const cart = reactive(JSON.parse(localStorage.getItem("cart")) || []);

    // Fonction pour ajouter au panier
    const addToCart = (product) => {
        const existing = cart.find(item => item.id === product.id)
        if (existing) { return } 
        else { 
            cart.push({ ...product, quantity: 1 })
            localStorage.setItem('cart', JSON.stringify(cart));
        } 
    }

    // Fonction pour supprimer du panier
    const removeFromCart = (productId) => {
        const index = cart.findIndex(item => item.id === productId)
        cart.splice(index, 1);
        localStorage.setItem('cart', JSON.stringify(cart));
    }
        
    // Vider le panier après paiement
    const clearCart = () => { cart.length = 0; localStorage.setItem('cart', JSON.stringify(cart)) }
</script>

<template>
    <nav class="navbar">
        <div class="navbar-links">
            <router-link to="/">Accueil</router-link> |
            <router-link to="/products">Produits</router-link> |
            <router-link to="/cart">Panier ({{ cart.length }})</router-link>
        </div>
    </nav>
    <router-view class="page" :cart="cart" @add-to-cart="addToCart"  @remove-from-cart="removeFromCart" @clear-cart="clearCart"/>
</template>
