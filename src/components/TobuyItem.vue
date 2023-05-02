<script setup>

const props = defineProps({
    buy: {
        type: Object,
        required: true,
    },
});

</script>

<template>
    <div>
       <h3 class ="products">✪ {{ props.buy.tobuy }}</h3>
    <div>
   

   <!-- <li>
    <input type="checkbox" :checked="todo.isCompleted"/>
   </li> -->
</div>
</div>
  
</template>

<style scoped>
.products {
    font-weight: 400;
    color:rgb(143, 65, 182);
}
</style>