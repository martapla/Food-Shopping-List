<template>
    <main>
        <div class="ideas-wrap">
            <h1>Search recipes: </h1>
            <input type="text">
            <button>Search</button>
            <div>
    <!-- <h2>Recipes</h2> -->
    <!-- <ul> -->
      <li v-for="recipe in recipes" :key="recipe.uri">
        <h3>{{ recipe.label }}</h3>
        <img :src="recipe.image" alt="Recipe Image">
        <p>Ingredients: {{ recipe.ingredientLines.join(', ') }}</p>
      </li>
    <!-- </ul> -->
  </div>
          
        </div>
    </main>
 
</template>

<script setup>
import { ref, onMounted } from 'vue';

const recipes = ref([]);

onMounted(async () => {
  const appId = '705b4711';
  const appKey = '45362516d2a63fbec79746e2c0519f73';
  const query = 'chicken'; // You can modify the query based on the type of recipes you want

  try {
    const response = await fetch(`https://api.edamam.com/search?q=${query}&app_id=${appId}&app_key=${appKey}`);
    const data = await response.json();
    recipes.value = data.hits.map(hit => hit.recipe);
  } catch (error) {
    console.error('Error fetching recipes:', error);
  }
});
</script>

<style scoped>
main {
  display:flex;
  flex-direction: column;
  max-width: 70vw;
  width:100%;
  margin:60px auto;
  border:4px solid #bef788;
  border-radius:6px;
  background-color: #f9cfb7;
  height:70vh;
  overflow-y: auto; 
}

.ideas-wrap {
    display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  margin-top: 20px;
  color:rgb(167, 105, 198);
  font-weight: 300;
  font-size: 14px;
}

.ideas-wrap button {
  border: 1px solid rgb(195, 241, 127);;
  color: rgba(237,118,237,1);
  background-color: rgb(244, 213, 99);
  box-shadow: 2px 2px rgb(142, 212, 37);
  width: 60px;
  height: 40px;
  border-radius: 20%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  margin:15px auto 30px auto;
  padding:12px;
}

input {
    width:50%;
    border:1px solid rgba(237,118,237,1);
    padding: 8px 30px;
    border-radius: 18px;
    margin:0 auto;
}
p {
    margin-bottom: 80px;
}


</style>

