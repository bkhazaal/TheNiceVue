<script setup>
import { ref } from 'vue';

// Define a reactive property for the search query
const query = ref('');

// Function to handle Google search
function searchGoogle() {
    // If the query is empty, return nothing
    if (!query.value.trim()) return;

    // Encode the query string
    const encodedQuery = encodeURIComponent(query.value.trim());

    // Define the URL for the Google search
    const url = `https://www.google.com/search?q=${encodedQuery}`;

    // Open the URL in a new tab
    window.open(url, '_blank');
}

// Define props for the component
defineProps({
    msg: {
        type: String,
        required: true
    }
});
</script>

<template>
    <div class="google-search">
        <h1>{{ msg }}</h1>
        <input 
            v-model="query"
            @keyup.enter="searchGoogle"
            placeholder="Search Google"
            class="input"
        />
        <button @click="searchGoogle" class="btn">Search</button>
    </div>
</template>

<style scoped>
.google-search {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 40px;
    margin-top: 20px;
}

h1 {
    margin: none;
}
</style>