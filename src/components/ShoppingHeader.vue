<script setup></script>

<template>
    <header>
        <nav class="container">
            <div class="title">
                <h1>Food Shopping <span> 🥕 🍅 🥑</span></h1>
            </div>
            <ul class="nav-routes">
                <RouterLink to='/'>Home 🏡 </RouterLink>
                <RouterLink to='/recipes'>Recipes 🥣 </RouterLink>
            </ul>        
        </nav>
    </header>
</template>


<style scoped>

.container {
    background-color: rgb(244, 213, 99);
    display:flex;
    width: 100%;
    margin:0 auto;

}
.title {
  text-align:left;
  margin-left: 20px;
  width: 50%;
  color:rgb(241, 55, 170);
  text-shadow: 2px 2px greenyellow;
}
span {
    text-shadow: none;
}
.nav-routes {
    display: flex;
    align-content: center;
    align-items: center;
    justify-content:space-around;
    width:35%;
    margin:10 auto;
}
.nav-routes a {
    text-decoration: none;
    color:white;
    font-weight: 700;
    font-size: 17px;
    
}
</style>