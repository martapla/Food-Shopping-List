<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
    <header>
        <nav class="container">
            <div class="title">
                <h1>Food Shopping <span> 🥕 🍅 🥑</span></h1>
            </div>
            <ul class="nav-routes">
                <RouterLink to='/'>Home 🏡 </RouterLink>
                <RouterLink to='/recipes'> Recipes 🍜 </RouterLink>
                <RouterLink to='/ideas'>Ideas 👩‍🍳 </RouterLink>
            </ul>        
        </nav>
    </header>
</template>


<style scoped>
.container {
    background-color: rgb(244, 213, 99);
    display:flex;
    flex-direction: column;
    width: 100%;
    margin:0 auto;
    border-bottom: 3px solid  greenyellow;
}

h1 {
    margin:0px;
}
.title {
    text-align:center;
    font-size: 18px;
    width: 100vw;
    color:rgb(241, 55, 170);
    text-shadow: 2px 2px greenyellow;
    margin:22px 0 24px 0;
}
span {
    text-shadow: none;
}
.nav-routes {
    display: flex;
    justify-content:space-evenly;
    margin:0 auto;
    padding: 0px;
    margin-bottom: 12px;
    font-size: 16px;
    gap: 40px;
}
.nav-routes a {
    text-decoration: none;
    color:white;
    font-weight: 700;
    font-size: 16px;
}


@media screen and (min-width: 880px){ 
    .container {
    background-color: rgb(244, 213, 99);
    display:flex;
    flex-direction: row;
    width: 100%;
    margin:0 auto;
    padding-bottom:30px;
    
    }

    .title {
    text-align:start;
    margin-left: 40px;
    padding-top: 30px;
    font-size: 24px;
    width: 90vw;
    color:rgb(241, 55, 170);
    text-shadow: 2px 2px greenyellow;
    }
    .nav-routes {
    display: flex;
    justify-content:end;
    align-items: center;
    gap:40px;
    width:50%;
    margin:0 auto;
    padding: 30px 40px 0 0;
    margin-bottom: 0px;
    }
    .nav-routes a {
    font-size: 18px;
    }
    
}
</style>