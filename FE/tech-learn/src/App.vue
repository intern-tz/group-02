<template>
  <div class="home-page">
    <Header class="header"></Header>
    <Navbar class="navbar"></Navbar>
    <div class="content">
      <RouterView/>
    </div>
  </div>
</template>

<script setup>
import Header from './components/Header/Header.vue';
import Navbar from './components/Navbar/Navbar.vue';
import 'vue3-toastify/dist/index.css';
import {RouterView} from 'vue-router'

</script>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.home-page {
    display: grid;
    grid-template-areas:
        "header header header header"
        "navbar content content content"
        "navbar content content content";
    grid-template-columns: 250px 1fr 1fr 1fr;
    grid-template-rows: auto 90px 1fr;
    height: 100vh;
    background-color: #f4f7fa;
}

.header {
    grid-area: header;
    background-color: #2c3e50;
    color: white;

}

.navbar {
    grid-area: navbar;
    padding: 20px;
    color: white;
    display: flex;
    flex-direction: column;
}

.navbar a {
    color: white;
    text-decoration: none;
    font-size: 18px;
    transition: color 0.3s ease;
}


.content {
    grid-area: content;
    background-color: #ffffff; /* Clean white background */
    height: 80%;
    padding: 40px;
    margin: 100px auto;
    width: 90%;
    box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1); /* Soft shadow for depth */
    border-radius: 10px; /* Rounded corners for a modern look */
   
}





</style>
