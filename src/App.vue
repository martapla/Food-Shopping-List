<script setup>
import { RouterView } from 'vue-router';
import ShoppingHeader from './components/ShoppingHeader.vue';

</script>

<template>
  <body class="background-container">
  <div>
   
     <ShoppingHeader />
     <RouterView />
    
  </div>
</body>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500;700&display=swap');

* {
font-family: 'Rubik', sans-serif;
margin:0;
padding:0;
box-sizing:border-box;
}
.container {
  /* max-width:1100px; */
  margin: 0 auto;
}
.background-container {
  background-image: url('@/assets/image.jpeg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 100vh; 
  overflow: hidden; 
}

</style>