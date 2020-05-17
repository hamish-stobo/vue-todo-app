<template>
    <header class="header">
        <h1>Todo List</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>    

<script>
 export default {
     name: 'Header'

 }
</script>

<style scoped>
    .header {
        text-align: center
    }

    .header h1 {
        padding: none;
        margin: 0 auto;
        padding: 0;
        background: rgb(32, 32, 32);
        color: white;
    }

    #nav {
        margin: 10px auto;
    }

    .header a {
        text-decoration: none;
    }
</style>