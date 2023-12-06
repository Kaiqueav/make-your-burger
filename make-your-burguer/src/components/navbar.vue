<script setup>
const props = defineProps(['logo'])

 </script>
<template>
    <div class="nav">
      <RouterLink to="/" id="logo-url">
        <img :src="props.logo" alt="" id="logo" />
      </RouterLink>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/pedidos">Pedidos</RouterLink>
    </div>
</template>
<style scoped>  
  .nav{
    display: flex;
    justify-content: flex-end;
    background-color: #222;
    border-bottom:  4px solid #111;
    padding: 0px 50px;
    align-items: center;

  }
  #logo-url{
    margin:auto;
    margin-left: 0;
  }
  #logo{
    width: 50px;
    height:50px
  }
  .nav a{
    color:#fcba03;
    text-decoration: none;
    margin: 4%;
    transition: .5s;
    font-size: 20px;
  }
  .nav a:hover{
    color:#fff;
  }

</style>

