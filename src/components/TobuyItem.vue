<script setup>
import { Icon } from '@iconify/vue';
const props = defineProps({
    buy: {
        type: Object,
        required: true,
    },
   
});

const emit = defineEmits(["line-buy","delete-buy", "edit-buy","update-buy"]);

</script>

<template>
    <li>
    <div>
       <input v-if ="buy.isEditing" type="text" :value="props.buy.tobuy" @input="$emit ('update-buy', props.buy.id, $event.target.value)"
/>

       <h3 v-else :class="{'completed': props.buy.isCompleted}" class ="products">- {{ props.buy.tobuy }}</h3>
       
    </div>

    <div class="actions">
        <Icon icon="material-symbols:heart-check" class="icon" color="red" @click="$emit('line-buy',props.buy.id)"/>

        <Icon icon="mdi:lead-pencil" class="icon" color="green" @click="$emit('edit-buy',props.buy.id)" />

        <Icon icon="solar:trash-bin-trash-linear" class="icon" color="orange" @click="$emit('delete-buy', props.buy.id)"/>

    </div>

    </li>
</template>

<style scoped>
.products {
    font-weight: 400;
    color:rgb(143, 65, 182);
    cursor:pointer;
    margin-left:20px;
}
.products:hover {
    color:rgb(237, 26, 216);
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
  padding: 16px 10px;
  /* background-color: #f2de8b; */
  border-radius: 6px;
  /* box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1), */
    /* 0 8px 10px -6px rgb(0 0 0 / 0.1); */
  margin-bottom: 20px;
  height: 25px;
  width: 85%;

}
li:hover .actions {
    opacity: 10;
    transition: 150ms ease-in-out;
}
.actions {
    opacity:0;
    margin-left: 20px;
    display:flex;
    gap:10px;
    display:flex;
    justify-items: right;
}
.icon {
    cursor:pointer;
    margin-right:20px;
}
.icon:hover{
    color:cornflowerblue;
}

.completed {
    text-decoration: line-through 2px;
}
  
</style>