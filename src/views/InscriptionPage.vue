<template>
    <ion-page>
        <ion-content fullscreen="true">
            <div class="container">
                <div class="top">
                    <a href="/connexion">
                        <ion-icon :icon="arrowBackOutline"></ion-icon>
                    </a>
                    <ion-text color="light">Crée ton compte</ion-text>
                </div>
                <div class="mid">
                    <ion-list class="custom">
                        <ion-item class="custom">
                            <ion-label position="stacked">Nom complet</ion-label>
                            <br>
                            <ion-input color="medium" type="text" placeholder="Richard Pastel"></ion-input>
                        </ion-item>
                        <ion-item class="custom">
                            <ion-label position="stacked">Email</ion-label>
                            <br>
                            <ion-input color="medium" type="email" placeholder="mail@ges.com"></ion-input>
                        </ion-item>
                        <ion-item class="custom">
                            <ion-label position="stacked">Mot de passe</ion-label>
                            <br>
                            <ion-input color="medium" type="password" max="20" placeholder="Mot de passe" @input="checkPasswordLength"></ion-input>
                            <p v-if="password.length > 0 && password.length < 20">Le mot de passe doit contenir au moins 20 caractères.</p>
                        </ion-item>
                        <ion-item class="custom">
                            <ion-label position="stacked">Confirmation du mot de passe</ion-label>
                            <br>
                            <ion-input color="medium" type="password" v-model="password" placeholder="Confirmer mot de passe"></ion-input>
                        </ion-item>
                    </ion-list>
                </div>
                <div class="bot">
                    <ion-button color="success" href="/">
                        <ion-text color="dark">Inscription</ion-text>
                    </ion-button>
                </div>
            </div>
        </ion-content>
    </ion-page>
</template>

<script>
import { arrowBackOutline } from 'ionicons/icons';
import { ref } from 'vue';

export default {
    name: "InscriptionPage",
    setup() {

        const password = ref('');

        const checkPasswordLength = () => {
            if (password.value.length > 20) {
                password.value = password.value.slice(0, 20);
            }
        };

        return {
            arrowBackOutline,
            password: "",
            checkPasswordLength
        }
    },
    methods: {
        togglePasswordVisibility() {
            const passwordInput = document.getElementById("password");
            const passwordToggle = document.getElementById("password-toggle");

            if (passwordInput.type === "password") {
                passwordInput.type = "text";
                passwordToggle.innerText = "Cacher";
            } else {
                passwordInput.type = "password";
                passwordToggle.innerText = "Afficher";
            }
        }
    }
}
</script>

<style scoped>
ion-list .custom>ion-label {
    font-size: 24px;
}

.bot ion-button {
    width: 317px;
}

ion-icon {
    color: black;
    margin-bottom: 2rem;
    scale: 1.5;
}

.top ion-text {
    font-size: 24px;
    font-weight: bold;
}

.bot ion-button ion-text {
    text-transform: none;
}

.container {
    display: flex;
    text-align: center;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    height: 100%;
}

.mid {
    width: 100%;
}

.top {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: left;
}

.bot {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.custom {
    --border-color: #C0BCBC;
    --background: transparent;
    background-color: transparent;
    font-weight: bold;
    color: #7C7C7C;
    --highlight-color-focused: #0DCDAA !important;
}
</style>