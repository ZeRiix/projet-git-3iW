<template>
    <button class="button" :class="{ 'button--hover': hover }" @click="onClick">
        <slot>{{ name }}</slot>
    </button>
</template>

<script>
export default {
    data() {
        return {
            hover: false,
        };
    },
    methods: {
        onClick() {
            // Code JavaScript à exécuter lorsque le bouton est cliqué
        },
    },
    props: {
        name: String,
    },
};
</script>

<style scoped>
.button {
    background-color: #4caf50;
    /* couleur verte */
    border-radius: 20px;
    /* bordures arrondies */
    color: white;
    /* texte blanc */
    font-size: 16px;
    /* taille de police */
    padding: 10px 20px;
    /* rembourrage du bouton */
    border: none;
    /* supprime les bordures */
    transition: all 0.3s;
    /* animation de transition pour l'état survolé */
}

.button--hover:hover {
    background-color: #3e8e41;
    /* couleur verte plus foncée au survol */
}

@media screen and (max-width: 767px) {
    .button {
        font-size: 14px;
        /* taille de police réduite pour les petits écrans */
        padding: 8px 16px;
        /* rembourrage du bouton réduit pour les petits écrans */
    }
}</style>
