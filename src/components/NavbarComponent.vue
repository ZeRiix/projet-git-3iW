<template>
    <nav class="navbar">
        <div class="navbar__brand">
            <router-link to="/" class="navbar__brand-link">{{ brand }}</router-link>
        </div>
        <ul class="navbar__links">
            <li v-for="(link, index) in links" :key="index">
                <router-link :to="link.to" class="navbar__link">{{ link.label }}</router-link>
            </li>
        </ul>
    </nav>
</template>

<script>
export default {
    name: 'NavbarComponent',
    props: {
        brand: {
            type: String,
            default: 'Mon blog',
        },
        links: {
            type: Array,
            default: () => [ /* exemple de liens */ /* remplacez par les liens de l'application */
                { label: 'Accueil', to: '/' },
                { label: 'Articles', to: '/articles' },
                { label: 'A propos', to: '/a-propos' },
            ],
        },
    },
};
</script>

<style scoped>
.navbar {
    width: 100%;
    /* largeur totale de la page */
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #eee;
    /* arrière-plan gris clair */
    padding: 20px;
    /* espacement interne */
}

.navbar__brand-link {
    font-size: 24px;
    font-weight: bold;
    text-decoration: none;
    color: #333;
    /* texte noir */
}

.navbar__links {
    list-style: none;
    display: flex;
    margin: 0;
    padding: 0;
}

.navbar__link {
    margin-left: 20px;
    font-size: 18px;
    text-decoration: none;
    color: #333;
    /* texte noir */
}

@media screen and (max-width: 767px) {
    .navbar__brand-link {
        font-size: 20px;
        /* réduire la taille de la police pour les petits écrans */
    }

    .navbar__link {
        font-size: 16px;
        /* réduire la taille de la police pour les petits écrans */
    }
}
</style>
