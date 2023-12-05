<script setup>
import { RouterView } from "vue-router";
import Navbar from "./components/navbar.vue";
import Footer from "./components/footer.vue";
 
</script>
<template>
    <Navbar logo="/img/logo.png"/>
    <RouterView />
    <Footer />
  
</template>
<style scoped>
*{
  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;

}
.main-container{
margin: 50px;
min-height: 250px;
}
h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}

</style>
