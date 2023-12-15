
<script setup>
import BuyCreator from '../components/BuyCreator.vue';
import { ref } from "vue";
import { uid } from 'uid';
import TobuyItem from '../components/TobuyItem.vue';


const tobuyList = ref([]);

const fetchToBuyList = () => {
    const savedToBuyList = JSON.parse(localStorage.getItem("tobuyList"));
    if (savedToBuyList) {
        tobuyList.value = savedToBuyList;
    }
};

fetchToBuyList();

const setToBuyListLocalStorage = () => {
    localStorage.setItem("tobuyList", JSON.stringify(tobuyList.value))
};

const createList = (tobuy) => {
    console.log(tobuyList.value);
    tobuyList.value.push({
        id: uid(),
        tobuy,
        isCompleted: null,
        isEditing: null,
    });
    setToBuyListLocalStorage();
};

// COMPLETE-LINE BUY 
const lineBuy = (id) => {
  const item = tobuyList.value.find((item) => item.id === id);
  if (item) {
    item.isCompleted = !item.isCompleted;
  }
  setToBuyListLocalStorage();
};

//EDIT BUY
const editBuy = (id) => {
    const item = tobuyList.value.find((item) => item.id === id);
    if (item) {
        item.isEditing = !item.isEditing;
    }
    setToBuyListLocalStorage();
};

//UPDATE BUY

const updateBuy = (id, buyVal) => {
    console.log("updateBuy id:", id, "and buyVal:", buyVal);
    const item = tobuyList.value.find((item) => item.id === id);
    if (item) {
        item.tobuy = buyVal;
    }
    setToBuyListLocalStorage();
};


//DELETE BUY
const deleteBuy = (del) => {
    tobuyList.value = tobuyList.value.filter((buy) => buy.id !== del);
    setToBuyListLocalStorage();
};


// DELETE Notes: 'del'representa el valor del identificador del elemento a eliminar de la lista.
//filter() crea un nuevo array, solo con el valor 'id'

</script>

<template>
    <main>
        <h1>List 📝 </h1>
        <BuyCreator @create-tobuy = "createList"/> 
        
        <div>
            <ul>
                
              <TobuyItem v-for= "food in tobuyList" :key="food.id" 
              :buy="food" 
              @delete-buy="deleteBuy" 
              @line-buy="lineBuy"
              @edit-buy="editBuy"
              @update-buy="updateBuy"/>

            </ul>
        </div>
    </main>
</template>

<style scoped>
main {
    display:flex;
    flex-direction: column;
    max-width: 70vw;
    width:100%;
    margin:40px auto;
    border:6px solid #f7b088;
    border-radius:6px;
    background-color: #f9cfb7;
    max-height: 80vh; 
    overflow-y: auto; 
}

h1 { 
    text-align: center;
    color:rgb(143, 65, 182);
    font-weight: 400;
    font-size: 20px;
}
.input-wrap {
    display: flex;
    border:2px solid rgb(238, 134, 223);
    border-radius: 3px;
    transition:250ms ease;
    width:80%;
    height: 30px;
    margin:0 auto;
}

input {
    width:100%;
    border:none;
    padding: 8px 6px;
}

input:focus {
    outline:none;
}

button {
    border:none;
    width:80px;
    color:rgb(241, 55, 170);
    background: rgb(146, 236, 176);
}

.errMsg {
    /* margin-left: 10px; */
}

ul {
    padding: 0px;
}


/* --------  Tablet and Desktop --------*/
/* ------------------------------------ */
@media screen and (min-width: 768px){ 
main {
   max-height: 70vh; 
   overflow-y: auto; 
}

.errMsg {
    margin-left: 150px;
}


}

</style>
  