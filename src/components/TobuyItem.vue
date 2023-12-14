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
    <div class="list-wrap">
        <li>
            <div class="item-wrap">
                <input v-if ="buy.isEditing" type="text" :value="props.buy.tobuy" @input="$emit ('update-buy', props.buy.id, $event.target.value)"/>

                <h3 v-else :class="{'completed': props.buy.isCompleted}" class ="products">- {{ props.buy.tobuy }}</h3>
                
            </div>

            <div class="actions">
                <Icon icon="material-symbols:check" class="icon" color="red" @click="$emit('line-buy',props.buy.id)"/>

                <Icon icon="mdi:lead-pencil" class="icon" color="green" @click="$emit('edit-buy',props.buy.id)" />

                <Icon icon="solar:trash-bin-trash-linear" class="icon" color="orange" @click="$emit('delete-buy', props.buy.id)"/>

            </div>

        </li>
    </div>
</template>

<style scoped>

/* *{
    border: 1px solid red;
} */
.products {
    font-weight: 400;
    color:rgb(143, 65, 182);
    cursor:pointer;
    margin-left:20px;
}
.products:hover {
    color:rgb(237, 26, 216);
}
.list-wrap {
    margin-top: 50px;
    /* border: 1px solid violet; */
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
  padding: 8px 0px;
  /* margin-bottom: 20px; */
  height: 25px;
  width: 94%;
  border-bottom: 1px solid white;
  /* margin-top: 50px; */
  margin: 10px auto 10px auto;

}
li:hover .actions {
    opacity: 10;
    transition: 150ms ease-in-out;
}

.item-wrap {
    width: 100%;
}

.item-wrap input{
   font-size: 10px;
}

.item-wrap h3 {
    width: 100%;
    font-size: 16px;
    margin:6px;
}

.actions {
    opacity:0;
    margin-left: 20px;
    display:flex;
    justify-items: right;
    width: 60%;
}
.icon {
    cursor:pointer;
    margin-right:10px;
    border: 1px solid white;
    padding: 2px;
}
.icon:hover{
    color:cornflowerblue;
}

.completed {
    text-decoration: line-through 2px;
}

/* --------  Tablet and Desktop --------*/
/* ------------------------------------ */
@media screen and (min-width: 768px){ 
.actions {
    gap:10px;
}
.icon {
   margin-right:20px;
}

}
  
</style>