<script setup>
    // On reçoit l'élément du panier en prop
    defineProps(['item']);
    // On déclare l'action de suppression
    const emit = defineEmits(['remove', 'add_1', 'remove_1']);
</script>

<template>
    <div>
        <img :src="item.thumbnail" :alt="item.title" width="50">
        <span>{{ item.title }}</span>
        <span>Prix : {{ item.price }} $</span>
        <div class="gestion_quantite">
            <button @click="emit('add_1', item.id)">+</button>
            <span>Quantité : {{ item.quantity }}</span>
            <button @click="emit('remove_1', item.id)">-</button>
        </div>
        <span>Sous-total : {{ item.price * item.quantity }} $</span>
        <button @click="emit('remove', item.id)">Supprimer</button>
    </div>
</template>