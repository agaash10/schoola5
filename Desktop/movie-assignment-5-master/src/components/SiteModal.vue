<script setup>
import axios from 'axios';
const props = defineProps(["id"]);
const emits = defineEmits(["toggleModal"]);

const info = await axios.get(`https://api.themoviedb.org/3/movie/${props.id}`, {
      params: {
        api_key: "f944b70daa59b60504fca0c383e63483",
        append_to_response: "videos"
      },
    })

console.log(info)

</script>

<template>

  <Teleport to="body">
    <div class="modal-outer-container" @click.self="emits('toggleModal')">
      <div class="modal-inner-container">
        <button class="close-button" @click="emits('toggleModal')">X</button>
        <img :src="`https://image.tmdb.org/t/p/w500${info.data.poster_path}`" alt="">
        <p> {{info.data.original_title}}</p>
        <p> Release Date: {{info.data.release_date}}</p>
        <p> Rating: {{info.data.vote_average}} Stars </p>
        <p> Popularity: {{info.data.popularity}}</p>
        <p> Box Office: {{info.data.revenue}} USD </p>
        <iframe :src="`https://www.youtube.com/embed/${info.data.videos.results.filter((video) => video.type === 'Trailer').at(0).key}`"></iframe>
      </div>
    </div>
  </Teleport>
</template>

<style scoped>
.modal-outer-container {


}

.modal-outer-container .modal-inner-container {

  
}

.modal-outer-container .modal-inner-container .close-button {
 

}

img {

}

iframe {


}

</style>
