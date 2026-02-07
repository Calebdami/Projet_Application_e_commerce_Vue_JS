<script setup>
    import { computed } from 'vue';
    import CartItem from '../components/CartItem.vue';
    import PaymentForm from '../components/PaymentForm.vue';

    // On reçoit les données et fonctions depuis App.vue
    const props = defineProps(['cart']);
    const emit = defineEmits(['remove-from-cart', 'clear-cart']);

    // Calcul du total général avec une propriété calculée (computed)
    const totalGeneral = computed(() => {
        function formatDecimal(n) {
            if (!Number.isFinite(n)) return '';
            const r = Math.round(n * 100) / 100;
            return r % 1 === 0 ? '' : r.toString();
        }
        const price = props.cart.reduce((acc, item) => acc + (item.price * item.quantity), 0);
        return formatDecimal(price);
    });

    const gererSuccesPaiement = () => {
        emit('clear-cart');
    };

    function remove_1(e){
        console.log(e.id)
        console.log(props.cart)
        if (e.quantity > 0){ e.quantity -- }
        if (e.quantity==0){emit('remove-from-cart', e.id)}
        return;
    }

    function add_1(e){
        e.quantity ++
    }

</script>

<template>
    <div class="cart-container">
        <h1>Mon Panier</h1>
    
        <div v-if="cart.length > 0">
            <CartItem v-for="item in cart" :key="item.id" :item="item" @remove="emit('remove-from-cart', $event)" @remove_1="remove_1(item)" @add_1="add_1(item)"/>
            <hr>
            <div class="cart-total">
                Total Général : {{ totalGeneral }} $
            </div>
            <hr>
            <PaymentForm class="paymentform" :cartLength="cart.length" @payment-success="gererSuccesPaiement"/>
        </div>
    
        <div v-else class="cart-empty">
            <p>Votre panier est vide.</p>
            <router-link to="/products">Retourner à la boutique</router-link>
        </div>
    </div>
</template>