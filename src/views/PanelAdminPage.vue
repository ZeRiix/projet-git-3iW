<template>
  <div>
    <h2>Connexion administrateur</h2>
    <form @submit.prevent="login">
      <label for="username">Nom d'utilisateur:</label>
      <input type="text" id="username" v-model="username">

      <label for="password">Mot de passe:</label>
      <input type="password" id="password" v-model="password">

      <button type="submit">Se connecter</button>
    </form>
  </div>
  <div>
    <h1>Tableau de bord administrateur</h1>
    <h2>Récapitulatif des transactions</h2>
    <table>
      <thead>
      <tr>
        <th>ID de transaction</th>
        <th>Utilisateur</th>
        <th>Date</th>
        <th>Montant</th>
        <th>Statut</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="transaction in transactions" :key="transaction.id">
        <td>{{ transaction.id }}</td>
        <td>{{ transaction.user }}</td>
        <td>{{ transaction.date }}</td>
        <td>{{ transaction.amount }} €</td>
        <td>{{ transaction.status }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      transactions: [
        { id: 1, user: 'John Doe', date: '2023-02-18', amount: 100, status: 'Validée' },
        { id: 2, user: 'Jane Smith', date: '2023-02-18', amount: 50, status: 'En attente' },
        { id: 3, user: 'Bob Johnson', date: '2023-02-17', amount: 75, status: 'Annulée' },
        // Ajouter d'autres transactions ici
      ],
      username: "",
      password: "",
      isLoggedIn: false,
    };
  },
  methods: {
    login() {
      if (this.username === "admin" && this.password === "admin123") {
        this.isLoggedIn = true;
        // rediriger vers la page d'administration
      } else {
        alert("Nom d'utilisateur ou mot de passe incorrect.");
      }
    },
  },
};
</script>