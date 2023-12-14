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
margin:0px;
padding:0px;
box-sizing:border-box;
}
.background-container {
  background-image: url('@/assets/image.jpeg');
  background-size: cover;
  background-position:inherit;
  background-repeat: no-repeat;
  height: 100vh; 
  overflow: hidden; 
}

</style>