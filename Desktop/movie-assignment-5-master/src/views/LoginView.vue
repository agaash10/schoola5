<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
const router = useRouter();
const username = ref("");
const password = ref("");
const error = ref(false);
const login = () => {
 if (username.value === "tmdb" && password.value === "movies") {
   router.push("/purchase");
 } else {
   error.value = true;
 }
};
</script>
<template>
 <div class="login-container">
   <h1> Please login with username and password to browse movies.</h1>
   <form @submit.prevent="login()">
     <input type="text" v-model="username" placeholder="Username" />
     <input type="password" v-model="password" placeholder="Password" />
     <input type="submit" value="Login" />
   </form>
   <div v-if="error" class="error">
     <p>Incorrect! Hint: use tmdb for username and movies for password</p>
   </div>
 </div>
 
</template>
<style scoped>
.login-container {
 display: flex;
 flex-direction: column;
 align-items: center;
 justify-content: center;
 width: 100vw;
 height: 100vh;
 font-size: 20px;
 font-family: 'Play', sans-serif;
 color: rgb(58, 186, 237);
 border-color: navy;
 border-width: 10px;
 margin-bottom: 220px;

}
 
form {
 display: flex;
 flex-direction: column;
 
}
 
form input {
 color: rgb(58, 186, 237);
 font-size: 20px;
 height: 65px;
 border-color: navy;
 border-width: 10px;
 font-family: 'Play', sans-serif;
 
}
 
h1 {
  font-size: 30px;
}
 
 :hover {
  border-color: white;

}

</style>



   