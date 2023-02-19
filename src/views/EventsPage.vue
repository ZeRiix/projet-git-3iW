<template>
  <ion-page>
    <HeaderComponent title="Home"></HeaderComponent>
    <ion-content :fullscreen="true">
      <ion-text>Dernier article</ion-text>
      <div class="container">
        <ion-card>
          <ion-card-header>
            <ion-img
                src="https://images.ctfassets.net/hrltx12pl8hq/3j5RylRv1ZdswxcBaMi0y7/b84fa97296bd2350db6ea194c0dce7db/Music_Icon.jpg"></ion-img>
            <ion-label>Card Title</ion-label>
            <ion-badge color="success">New</ion-badge>
            <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
          </ion-card-header>

          <ion-card-content>
            Here's a small text description for the card content. Nothing more, nothing less.
          </ion-card-content>
          <ion-button color="medium" fill="outline" href="/payment">
            <ion-text color="success">Rejoindre</ion-text>
          </ion-button>
        </ion-card>
        <button @click="likeEvent">{{ event.likes }} Likes</button>

        <h3>Ajouter un commentaire</h3>
        <form @submit.prevent="addComment">
          <label for="comment">Commentaire:</label>
          <textarea id="comment" v-model="newComment"></textarea>
          <button type="submit">Ajouter</button>
        </form>

        <h3>Commentaires</h3>
        <ul>
          <li v-for="comment in event.comments" :key="comment.id">{{ comment.text }}</li>
        </ul>
      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import {defineComponent} from 'vue';
import axios from 'axios';
import {ref} from 'vue';
import {
  IonContent,
  IonPage,
  IonTitle,
  IonToolbar,
  IonText,
  IonCard,
  IonCardContent,
  IonCardHeader,
  IonCardSubtitle,
  IonCardTitle,
  IonImg,
  IonBadge,
  IonLabel
} from '@ionic/vue';
import HeaderComponent from "@/components/current/HeaderComponent.vue";

export default defineComponent({
  name: "HomePage",
  components: {HeaderComponent, IonPage, IonContent, IonBadge},
  data() {
    return {
      event: {
        title: "Mon évènement",
        description: "Description de l'évènement",
        likes: 0,
        comments: [],
      },
      newComment: "",
    };
  },
  methods: {
    likeEvent() {
      this.event.likes++;
    },
    addComment() {
      if (this.newComment) {
        const newComment = {id: Date.now(), text: this.newComment};
        this.event.comments.push(newComment);
        this.newComment = "";
      }
    },
  },
  setup() {
    const name = ref('');
    const email = ref('');

    const registerForEvent = async () => {
      try {
        // Envoyer les données d'inscription à l'API
        const response = await axios.post('/api/register', {
          name: name.value,
          email: email.value,
          eventId: 'ID_de_l_evenement',
        });

        // Créer une session de paiement avec Stripe
        const session = await axios.post('/api/create-payment-session', {
          priceId: 'ID_du_prix',
          customerId: response.data.customerId,
        });

        // Rediriger l'utilisateur vers la page de paiement de Stripe
        window.location.href = session.data.url;
      } catch (error) {
        console.error(error);
      }
    };

    return {name, email, registerForEvent};
  },
});
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
  color: black;
}

ion-card {
  box-shadow: 5px 5px 5px rgb(56, 55, 55);
}

ion-text {
  color: black;
  font-weight: semi-bold;
  font-size: 20px;
  margin: 10px;
}

ion-label {
  font-weight: bold;
  font-size: 20px;
}
</style>