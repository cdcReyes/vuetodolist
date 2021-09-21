<template>
    <header class="header">
        <h1>Carl's Todo List</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .header {
        color:white;
        text-align: center;
        padding: 10px;
        padding-top: 100px;
        background: rgb(33, 60, 71);
        
    }
    .header a {
        color:rgb(180, 94, 94);
        padding-right: 5px;
        text-decoration: none;
    }
</style>