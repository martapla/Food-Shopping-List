
<script  setup>
import { reactive } from "vue"; 

const emit = defineEmits(["create-tobuy"]); 

const tobuyState = reactive({
    tobuy: "",
    invalid: null, //null = not value assigned
    errMsg: "",

});

const createBuy = () => {          
    tobuyState.invalid = null;
    if (tobuyState.tobuy !== "") {  // if is not equal to an empty string, then we listen the next emit line:
        emit("create-tobuy", tobuyState.tobuy);
        tobuyState.tobuy = ""; //reset to an empty string
        return;
    } 
    tobuyState.invalid = true;            
    tobuyState.errMsg = "... Add Food ... ☝ "
    setTimeout(() => {
        tobuyState.invalid = null;
    }, 1000);
    
};



// Done with REF, when is only one element
// const tobuy = ref("");

// const createBuy = () => { 
//     emit("create-tobuy", tobuy.value); //We put .value with Ref, not need .value with Reactive
//};
//https://www.youtube.com/watch?v=KTFH4P8unUQ min:51

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
/* *{
    border: 1px solid green;
} */
.input-wrap {
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 20px;
    transition:250ms ease;
    width:80%;
    height: 40px;
    margin:0 auto;
}

input {
    width:80%;
    border:1px solid rgba(237,118,237,1);
    padding: 8px 30px;
    border-radius: 18px;
}

input:focus {
    outline:none;
}

button {
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
    margin-top:15px;
    padding:12px;
   
}
button:hover {
    color:white;
}

.errMsg {
    margin-left: 150px;
    color:crimson;
}

/* --------  Tablet and Desktop --------*/
/* ------------------------------------ */
@media screen and (min-width: 768px){ 
    .input-wrap {
    display: flex;
    flex-direction: row;
    border-radius: 20px;
    transition:250ms ease;
    width:80%;
    height: 40px;
    margin:0 auto;
}

button {
    color: rgba(237,118,237,1);
    background-color: rgb(244, 213, 99);
    width: 60px;
    height: 40px;
    border-radius: 20%;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    margin-top:0px;
    padding:0px;
}
input {
   margin-right:20px;
}

}
</style>

<!-- value:null -->

<!-- null represents the absence of a value or the lack of a value.

When a variable is assigned a value of null, it means that the variable is intentionally empty and doesn't point to any object or data.

null can also be used to indicate an error condition or to signal the end of a data stream or list. It is often used in conditional statements and logical expressions to check if a variable contains a value or not. -->