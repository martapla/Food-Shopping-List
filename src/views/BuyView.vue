<script setup>
import BuyCreator from '../components/BuyCreator.vue';
import { ref } from "vue";
import { uid } from 'uid';
const tobuyList = ref([]);

const createList = (tobuy) => {
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
    </main>
</template>

<style scoped>
main {
    display:flex;
    flex-direction: column;
    max-width: 500px;
    width:100%;
    margin:60px auto;
}

h1 {
    /* margin-top: 100px auto; */
    text-align: center;
    color:rgb(143, 65, 182);
    font-weight: 400;
}
</style>