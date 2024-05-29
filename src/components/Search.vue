<template>
    <form @submit.prevent="searchStore.getMovies(searchMovie)">
        <input type="text" class="search-input" placeholder="Input movie name" v-model="searchMovie">
    </form>
    <Loader v-if="searchStore.loader" />
    <div v-else>
        <Movie v-for="movie of searchStore.movies" :key="movie.id" :movie="movie" :isSearch="true"/>
    </div>
</template>

<script setup>
import Loader from '../components/Loader.vue'
import Movie from '../components/Movie.vue'
import { ref } from 'vue'
import { useSearchStore } from '../stores/SearchStore.js'

const searchMovie = ref('')
const searchStore = useSearchStore()
</script>

<style lang="css" scoped>
.search-input {
    width: 100%;
    height: 40px;
    padding: 0 10px;
    border-radius: 10px;
    border: 1px solid #efefef;
    margin-bottom: 20px;
    border-radius: 10px;
}
</style>