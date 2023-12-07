<script setup></script>
<template>

<div class="main-container">
    <h1> MONTE SEU BURGER</h1>
    <form class="formBurger">
        <div class="input-container">
            <label for="nome">Nome do Cliente:</label>
            <input id="nome" name="nome" v-model="message" placeholder="Digite Seu Nome">
        </div>
        <div class="input-container">
            <label for="pao">Escolha seu Pão:</label>
            <select v-model="selected" id="pao">
                <option value="Integral">Integral</option>
            </select>
        </div>
        <div class="input-container">
            <label for="Carne">Escolha sua carne:</label>
            <select v-model="selected" id="carne">
                <option value="Maminha">Maminha</option>
            </select>
        </div>
          <div class="opcionais-container">
            <label id="opcionais-title" for="opcionais">Escolha seu opcional:</label>
            <div class="checkboxContainer">
              <input type="checkbox" name="" id="checkbox" v-model="opcionais">   
              <span> Salame</span>
            </div>
            <div class="checkboxContainer">
              <input type="checkbox" name="" id="checkbox" v-model="opcionais">   
              <span> Salame</span>
            </div>
            <div class="checkboxContainer">
              <input type="checkbox" name="" id="checkbox" v-model="opcionais">   
              <span> Salame</span>
            </div>
        </div>
        <div class="input-container">
            <input type="submit"  id="btn-form" value="criar meu burger!">
        </div>
    </form>
</div>
</template>

<style scoped>
.formBurger{
   margin: 0 auto;
   max-width: 400px;
}
.input-container{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}
label{
    font-weight: bold;
    margin-bottom: 15px;
    color:#222;
    padding: 5px 10px;
    border-left: 4px solid #fcba03;
}
input, select{
    padding: 5px, 10px;
    width:300px;
}
.opcionais-container{
    flex-direction: row;
    flex-wrap: wrap;

}
.opcionais-title{
    width: 100%;
}
.checkboxContainer{
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom:20px;
}
.checkboxContainer span,
 .checkboxContainerinput{
    width:auto;
}
.checkboxContainer span{
    margin-left: 6px;
    font-weight: bold;

}
#btn-form{
    background-color:#222;
    color:#fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 2%;
    margin:0 auto;
    cursor: pointer;
}
#btn-form:hover{
    background-color: transparent;
    color:#222;
}
</style>