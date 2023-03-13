<script  setup>
import { reactive } from "vue"; //emit step 2

const emit = defineEmits(["create-tobuy"]); // emit step 1

const tobuyState = reactive({
    tobuy: "",
    invalid: null, //null = not value assigned
    errMsg: "",

});

const createBuy = () => {           //emit step 3
    tobuyState.invalid = null;
    if (tobuyState.tobuy !== "") {  // if is not equal to an empty string
        emit("create-tobuy", tobuyState.tobuy);
        tobuyState.tobuy = ""; //reset to an empty string
        return;
    } 
    tobuyState.invalid = true;            
    tobuyState.errMsg = "...food missing... ☝ "
    
    
};

//https://www.youtube.com/watch?v=KTFH4P8unUQ min:51

// Done with REF, when is only one element
// const tobuy = ref("");

// const createBuy = () => {  //emit step 3
//     emit("create-tobuy", tobuy.value); //We put .value with Ref, not need .value with reactive
//};

</script>

<template>
    <section>
    <div class="input-wrap">
        <input type="text" v-model="tobuyState.tobuy"/>
        <button @click="createBuy()">Add</button>
    
    </div>
    <p v-show = "tobuyState.invalid" class="errMsg">{{ tobuyState.errMsg }}</p>
    </section>
</template>

<style scoped>
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
</style>

<!-- value:null -->

<!-- null represents the absence of a value or the lack of a value.

When a variable is assigned a value of null, it means that the variable is intentionally empty and doesn't point to any object or data.

null can also be used to indicate an error condition or to signal the end of a data stream or list. It is often used in conditional statements and logical expressions to check if a variable contains a value or not. -->