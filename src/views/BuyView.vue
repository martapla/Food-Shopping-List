
// WITHOUT EMITS
<template>
  <main>
    <div>
      <h1>List 📝 </h1>
      <form @submit.prevent="addTask">
        <div class="input-wrap">
        <input type="text" v-model="newTask" placeholder="Write here">
        <button type="submit">Add</button>
      </div>
      </form>

      <ul>
        <li class="points" v-for="(task, index) in tasks" :key="index">
          {{ task }}
        </li>
      </ul>
    </div>
  </main>
  </template>
  
  <script setup>
    import { ref } from 'vue'
  
    const tasks = ref([])
    const newTask = ref('')
  
    const addTask = () => {
      tasks.value.push(newTask.value)
      newTask.value = ''
    }
  </script>

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
</style>
  
  
  