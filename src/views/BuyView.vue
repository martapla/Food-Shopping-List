
<script setup>
import BuyCreator from '../components/BuyCreator.vue';
import { ref } from "vue";
import { uid } from 'uid';
import TobuyItem from '../components/TobuyItem.vue';


const tobuyList = ref([]);

const createList = (tobuy) => {
    console.log(tobuyList.value);
    tobuyList.value.push({
        id: uid(),
        tobuy,
        isCompleted: null,
        isEditing: null,
    });
};
</script>

<template>
    <main>
        <h1>List 📝 </h1>
        <BuyCreator @create-tobuy = "createList"/> 
        
        <div class="ineed">
           
            <h2>I Need :</h2>
            <ul>
                
              <TobuyItem v-for= "food in tobuyList" :key="food" :buy="food"/>
            </ul>
        </div>
    </main>
</template>

<style scoped>
main {
    display:flex;
    flex-direction: column;
    max-width: 500px;
    width:100%;
    margin:60px auto;
    border:2px solid #f7b088;
    border-radius:6px;
    background-color: rgb(163, 242, 216);
    height:80vh;
}

h1 { 
    text-align: center;
    color:rgb(143, 65, 182);
    font-weight: 400;
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
    margin-left: 150px;
   
}
.points{
   margin-left:150px;
}
h2{
    text-align: left;
    margin-left: 50px;
    margin-top: 30px;
    color:  rgb(244, 201, 46);
    font-weight: 400;
}
</style>
  