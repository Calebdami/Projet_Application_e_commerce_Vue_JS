<script setup>
    import { ref, reactive } from 'vue';

    const props = defineProps(['cartLength']);
    const emit = defineEmits(['payment-success']);

    const messageSucces = ref(false);
    const form = reactive({
        nom: '',
        carte: '',
        expiration: '',
        cvv: ''
    });

    const validerPaiement = () => {
        // Vérification : champs non vides et panier non vide
        if (props.cartLength > 0 && form.nom && form.carte && form.expiration && form.cvv) {
            messageSucces.value = true;
            
            // On attend un peu pour montrer le message avant de vider le panier
            setTimeout(() => {
                emit('payment-success');
                messageSucces.value = false;
                // Reset du formulaire
                form.nom = ''; form.carte = ''; form.expiration = ''; form.cvv = '';
            }, 2000);
        } 
        else { alert("Veuillez remplir tous les champs et avoir des articles dans le panier.")}
    };
</script>

<template>
    <div>
        <h2>Paiement</h2>
        <div v-if="messageSucces">
            <p>✅ Paiement effectué avec succès !</p>
        </div>
        
        <form v-else @submit.prevent="validerPaiement">
            <input v-model="form.nom" type="text" placeholder="Nom du client">
            <input v-model="form.carte" type="text" placeholder="Numéro de carte">
            <input v-model="form.expiration" type="text" placeholder="MM/AA">
            <input v-model="form.cvv" type="text" placeholder="CVV">
            
            <button type="submit">Payer</button>
        </form>
    </div>
</template>