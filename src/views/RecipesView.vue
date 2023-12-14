<template>
  <main>
      <div class="recipe">

        <h1>Write your recipes here: </h1>
        
        <div class="recipe-text">
          <input type="textarea">
          <button>Save</button>
        </div>

      </div>
  </main>
</template>

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
.recipe-text input{
  height:20vh;
  width:90%;
  margin: 0 auto;
  overflow-y: auto; 
  border-radius: 10px;
  border:1px solid rgb(167, 105, 198);
  outline:none;
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
  margin:15px auto 0 auto;
  padding:12px;
}

</style>

<!-- https://www.youtube.com/watch?v=Vuu3JRn51QI -->