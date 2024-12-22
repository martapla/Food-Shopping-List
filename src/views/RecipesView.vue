<template>
  <main>
      <div class="recipe">

        <h1>Your recipes here: </h1>
        
        <div class="recipe-text">
          <textarea v-model="newRecipe" placeholder="Write your new recipe !!"></textarea>
          <button @click="saveRecipe">Save</button>
        </div>
        
        <!-- List -->
        <div class="recipe-list">
          <div v-for="(recipe, index) in recipeList" :key="index" class="recipe-item">
            <div v-if="recipe.isEditing" class="edit-box">
              <textarea 
                v-model="recipe.text" 
                @keydown.enter="saveEdit(index)" 
                class="edit-textarea"
              ></textarea>
          </div>
          <div v-else>
            {{ recipe.text }}
          </div>

          <div class="actions">
            <Icon 
              icon="mdi:lead-pencil" 
              class="icon" 
              color="green" 
              @click="editRecipe(index)" 
            />
            <Icon 
              icon="solar:trash-bin-trash-linear" 
              class="icon" 
              color="orange" 
              @click="deleteRecipe(index)" 
            />
          </div>

          </div>
        </div>
      </div>
  </main>
</template>

<script setup>
import { ref, onMounted} from "vue";
import { Icon } from '@iconify/vue';


const newRecipe = ref("");
const recipeList = ref([]);


const saveRecipe = () => {
  if (newRecipe.value.trim()) {
    recipeList.value.push({ text: newRecipe.value, isEditing: false });
    newRecipe.value = "";
    saveToLocalStorage();
  }
};


const deleteRecipe = (index) => {
  recipeList.value.splice(index, 1);
  saveToLocalStorage();
};


const editRecipe = (index) => {
  const recipe = recipeList.value[index];
  if (recipe.isEditing) {
    // Guarda los cambios si ya está en modo edición
    saveEdit(index);
  } else {
    // Activa el modo de edición
    recipe.isEditing = true;
  }
};


const saveEdit = (index) => {
  recipeList.value[index].isEditing = false;
  saveToLocalStorage();
};

const saveToLocalStorage = () => {
  console.log("Saving to localStorage", recipeList.value);
  localStorage.setItem("recipes", JSON.stringify(recipeList.value));
};

const loadFromLocalStorage = () => {
  console.log("Loading from localStorage");
  const savedRecipes = localStorage.getItem("recipes");
  if (savedRecipes) {
    recipeList.value = JSON.parse(savedRecipes);
    console.log("Loaded recipes:", recipeList.value);
  }
};

// Cargar recetas al montar el componente
onMounted(() => {
  loadFromLocalStorage();
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

.recipe {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  margin-top: 20px;
  color:rgb(167, 105, 198);
  font-weight: 300;
  font-size: 14px;
}
.recipe-text {
  display: flex;
  flex-direction: column;
  width:80%;
  margin: 20px auto 0 auto;
  align-items: flex-end;
}
.recipe-text textarea {
  height:20vh;
  width:100%;
  margin: 0 auto;
  overflow-y: auto; 
  border-radius: 10px;
  border:1px solid rgb(167, 105, 198);
  outline:none;
  box-sizing: border-box; 
  padding: 30px;
  font-style: italic; 
  font-size: 16px;
  color: #3d3c3c;
}

textarea::placeholder {
  color: #999;
  font-style: italic; 
  padding:10px;
  text-align:start;
}

.edit-box {
  margin: 0 auto;
  width: 100%;
}

.edit-textarea {
  width:100%;
  min-height: 130px; 
  font-size: 14px; 
  padding: 10px; 
  border: 1px solid rgb(142, 212, 37); 
  border-radius: 6px; 
  box-sizing: border-box; 
  outline: none; 
  resize: none; 
  overflow-y: auto; 
}

.edit-textarea:focus {
  border-color: rgb(167, 105, 198); 
  background-color: #f9f9f9; 
}

.recipe-text button {
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
  margin:10px auto 30px auto;
  padding:12px;
}

/* recipe list box */
.recipe-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 40px;
  width:80%;
  margin: 0 auto;
}

.recipe-item {
  position: relative;
  background-color: rgb(244, 237, 211);
  border: 2px solid  rgb(142, 212, 37);
  border-radius: 8px;
  padding: 15px;
  width: 60%;
  margin: 10px 0;
  font-size: 16px;
  font-weight: 400;
  color: rgb(167, 105, 198);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.actions {
  position: absolute; 
  top: 50%; 
  right: -90px; 
  transform: translateY(-50%); 
  display: flex;
  gap: 10px;
}

.icon {
  cursor: pointer;
  padding: 6px;
  border: 2px solid  rgb(244, 237, 211);
  border-radius:6px;
}

.icon:hover {
  border: 2px solid rgb(142, 212, 37);
}

/* --------  Mobile --------*/
/* ------------------------ */

@media (max-width: 768px) {
  .recipe {
    font-size: 12px;
  }
  .recipe-text textarea {
    width: 100%;
    padding: 10px;
    font-size: 14px;
  }
  .recipe-item {
    width: 100%; 
    margin-bottom: 60px;
  }

  .actions {
    position: absolute; 
    bottom: -20px; 
    right: 0; 
    transform: translateY(90%); 
    display: flex;
    flex-direction: row; 
    justify-content: flex-end; 
    gap: 10px; 
  }

}

</style>

