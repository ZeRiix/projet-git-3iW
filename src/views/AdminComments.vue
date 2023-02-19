<template>
    <div>
        <h2>Commentaires</h2>
        <div v-for="(comment, index) in comments" :key="index" class="comment">
            <div class="author">{{ comment.author }}</div>
            <div class="content">{{ comment.content }}</div>
            <button class="delete-button" @click="deleteComment(index)">Supprimer</button>
            <button class="reply-button" @click="toggleReply(index)">Répondre</button>
            <div v-if="comment.showReply">
                <textarea v-model="comment.reply"></textarea>
                <button @click="submitReply(comment)">Envoyer</button>
            </div>
        </div>
    </div>
</template>
<script>
import { ref } from 'vue';

export default {
    setup() {
        const comments = ref([
            { author: 'Jean', content: 'Super produit !' },
            { author: 'Marie', content: 'Mauvaise expérience, je ne recommande pas.' },
            { author: 'Pierre', content: 'Rapport qualité/prix excellent.' },
        ]);

        const deleteComment = (index) => {
            comments.value.splice(index, 1);
        };

        const toggleReply = (index) => {
            comments.value[index].showReply = !comments.value[index].showReply;
        };

        const submitReply = (comment) => {
            comment.showReply = false;
            // envoyer la réponse à la base de données, etc.
        };

        return {
            comments,
            deleteComment,
            toggleReply,
            submitReply,
        };
    },
};
</script>
<style scoped>
.comment {
    border: 1px solid black;
    padding: 1rem;
    margin-bottom: 1rem;
}

.author {
    font-weight: bold;
}

.delete-button {
    background-color: red;
    color: white;
    border: none;
    padding: 0.5rem;
    margin-top: 1rem;
}

.delete-button:hover {
    cursor: pointer;
}

.delete-button:active {
    background-color: darkred;
}

.delete-button:focus {
    outline: none;
}

</style>