<script setup>
import { RouterView } from "vue-router";
import Navbar from "./components/navbar.vue";
import Footer from "./components/footer.vue";
</script>
<template>
  <div>
    <Navbar />
    <RouterView />
    <Footer />
  </div>
</template>
<style scoped></style>
