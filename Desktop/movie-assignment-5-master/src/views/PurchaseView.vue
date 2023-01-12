<script setup>
import axios from "axios";
import { ref } from 'vue';
import SiteModal from '../components/SiteModal.vue';
const showModal = ref(false);
const selectedId = ref(0);
const openModal = (id) => {
  showModal.value = true;
  selectedId.value = id;
};
const closeModal = () => {
  showModal.value = false;
};
let data = (await axios.get("https://api.themoviedb.org/3/trending/movie/week", {
    params: {
        api_key: "f944b70daa59b60504fca0c383e63483"
    }
})).data.results;
console.log(data)
</script>

<template>
   <div>
      <h1> Here are some trending movies </h1>
 
    </div>

    <div>
        <img v-for="movie in data" @click="openModal(movie.id)" class="poster" :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`" alt="">
    </div>
    <SiteModal v-if="showModal" @toggleModal="closeModal()" :id="selectedId" />
</template>

<style scoped>


</style>

