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
            <router-link to="/products">Produits</router-link>
            <router-link to="/cart" style="margin-left: 0.5rem;">
                <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="20"
                    height="20"
                    viewBox="0 0 24 24"
                    fill="blue"
                    stroke="currentColor"
                    stroke-width="1"
                    stroke-linecap="round"
                    stroke-linejoin="round">
                    <circle cx="9" cy="21" r="1" />
                    <circle cx="20" cy="21" r="1" />
                    <path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/>
                </svg> ({{ cart.length }})
            </router-link>|
        </div>
    </nav>
    <router-view class="page" :cart="cart" @add-to-cart="addToCart"  @remove-from-cart="removeFromCart" @clear-cart="clearCart"/>
</template>
