

<template>
  <div>
    <navbar/>
    <RouterView />
    <footer/>
  </div>

</template>
<script>
import { RouterLink, RouterView } from 'vue-router';
import navbar from './components/navbar.vue';
import footer from './components/footer.vue';
export default{
  componets:{
    navbar,
    footer
  }

}

</script>
<style scoped>
 
</style>
