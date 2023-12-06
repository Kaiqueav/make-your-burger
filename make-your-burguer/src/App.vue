<script setup>
import { RouterView } from "vue-router";
import Navbar from "./components/navbar.vue";
import Footer from "./components/footer.vue";
 
</script>
<template>
  <div class="main-container">
    <Navbar logo="/img/logo.png"/>
    <RouterView />
    <Footer />  
   
  </div>
    
  
</template>
<style>
*{
  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  border: 0;
}
.main-container{
   min-height: 250px;
}
h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}

</style>
