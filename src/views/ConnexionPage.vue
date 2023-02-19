<template>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
  <ion-page>
    <ion-content :fullscreen="true">
      <div class="container">
        <div class="top">
          <a href="/connexion">
            <ion-icon :icon="arrowBackOutline"></ion-icon>
          </a>
          <ion-text color="light">Bon retour parmis nous</ion-text>
        </div>
        <div class="mid">
          <ion-list class="custom">
            <ion-item class="custom">
              <ion-label class="large-label" position="stacked">Email</ion-label>
              <ion-input class="small-input" color="medium" type="email" placeholder="mail@ges.com"></ion-input>
            </ion-item>
            <ion-item class="custom">
              <ion-label class="large-label" position="stacked">Mot de passe</ion-label>
              <ion-input class="small-input" color="medium" type="password" placeholder="Mot de passe"></ion-input>
            </ion-item>
            <ion-item class="toggle-input">
              <ion-label class="small-label" position="stacked">Mémoriser</ion-label>
              <ion-toggle slot="end"></ion-toggle>
            </ion-item>
          </ion-list>
        </div>
        <div class="bot">
          <ion-button color="success" href="/bde/home">
            <ion-text class="medium-text" color="dark">Connexion</ion-text>
          </ion-button>
        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import {defineComponent} from 'vue';
import {IonPage, IonContent, IonInput, IonItem, IonLabel, IonList} from '@ionic/vue';
import {arrowBackOutline} from 'ionicons/icons';
import logo from '../assets/peoplefamily.svg'
import HeaderComponent from "@/components/current/HeaderComponent.vue";

export default defineComponent({
  name: 'IdentificationPage',
  components: {IonContent, IonPage},
  setup() {
    return {
      arrowBackOutline
    }
  },
  data: function () {
    return {
      logo: logo
    }
  }
});
</script>

<style scoped>

.medium-text {
  font-weight: 500;
}

.small-input {
  font-size: 14px;
}

.mid ion-label {
  font-size: 16px;
  color: #7C7C7C;
}

.large-label {
  font-weight: 700;
}

* {
  font-family: 'Inter', sans-serif;
  font-weight: 400;
}

.toggle-input {
  --background: transparent;
  background-color: transparent;
  --border-style: none;
  --highlight-color-focused: #0DCDAA !important;
}

ion-toggle {
  --background-checked: #32D74B;
  scale: 0.6;
}

ion-icon {
  color: black;
  margin-bottom: 2rem;
  scale: 1.5;
}

.top a {
  text-decoration: none;
}

.top ion-text {
  font-size: 24px;
  font-weight: bold;
}

.bot ion-button {
  width: 317px;
}

.container {
  display: flex;
  text-align: center;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  justify-content: space-around;
  height: 100%;
}

.top {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}

.bot {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

ion-text {
  text-transform: none;
}

.custom {
  --background: transparent;
  --border-color: #C0BCBC;
  background-color: transparent;
  color: #7C7C7C;
  font-weight: bold;
  --highlight-color-focused: #0DCDAA !important;
}
</style>
  