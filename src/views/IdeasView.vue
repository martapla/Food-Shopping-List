<template>
    <main>
        <div class="ideas-container">
            <h1>Search recipes: </h1>
            <input v-model="searchQuery" placeholder="Enter food name" />
            <button @click="searchRecipes">Search</button>
        </div>
           
   
        <ul class="api-wrapper">
            <li v-for="recipe in recipes" :key="recipe.uri">
                <h3>{{ recipe.label }}</h3>
                <img :src="recipe.image" alt="Recipe Image">
                <p><span>Ingredients:</span>  {{ recipe.ingredientLines.join(', ') }}</p>

                <p> <span>Source:</span>  {{ recipe.source}}</p>
            </li>
        </ul>
   
    </main>
 
</template>

<script setup>
import { ref, onMounted } from 'vue';

const recipes = ref([]);
const searchQuery = ref('');

const searchRecipes = async () => {
  const appId = '705b4711';
  const appKey = '45362516d2a63fbec79746e2c0519f73';

  try {
    const response = await fetch(`https://api.edamam.com/search?q=${searchQuery.value}&app_id=${appId}&app_key=${appKey}`);
    const data = await response.json();
      recipes.value = data.hits.map(hit => hit.recipe);
      console.log(data);
  } catch (error) {
    console.error('Error fetching recipes:', error);
  }
};

onMounted(() => {
  
  searchRecipes();
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
  height:72vh;
  overflow-y: auto; 
}

.ideas-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  margin-top: 20px;
  color:rgb(167, 105, 198);
  font-weight: 300;
  font-size: 14px;
}

.ideas-container button {
  border: 1px solid rgb(195, 241, 127);
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

.api-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  color:rgb(167, 105, 198);
  font-weight: 300;
  font-size: 14px;
  margin:0 auto;
  width:86%;
  list-style: none;
  padding: 0px;
}

.api-wrapper li {
    border:1px solid white;
    border-top:4px solid white;
    border-radius: 6px;
    margin:20px auto;
}

.api-wrapper img {
    width:80%;
    border-radius:50%;
    border:2px solid white;
}
.api-wrapper p {
    margin-bottom: 20px;
    padding:0 10px;
}

.api-wrapper span {
    font-weight: bold;
    padding-right: 2px;
}

/* --------  Tablet and Desktop --------*/
/* ------------------------------------ */
@media screen and (min-width: 768px){ 
.api-wrapper h3 {
    font-size: 24px;
    padding:10px 0 20px 0;
}

.api-wrapper p {
    font-size: 16px;
    padding:0 20px;
}
}
</style>

