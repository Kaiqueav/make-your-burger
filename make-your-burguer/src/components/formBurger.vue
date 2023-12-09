<script setup>
 import Message from './message.vue';
 import {ref, onMounted} from 'vue';

 
const paes = ref(null);
const carnes = ref(null);
const opcionaisData = ref(null);
const nome = ref(null);
const pao = ref(null);
const carne = ref(null);
const opcionaisCli = ref([]);
const msg = ref(null);


// função para consumir json
const getIngredients = async () =>{
    const req = await fetch ('http://localhost:3000/ingredientes');
    const data = await req.json();
    paes.value = data.paes;
    carnes.value = data.carnes;
    opcionaisData.value = data.opcionais
}
// funçao para enviar para o servidor
 const createBurger = async (e) => {
    e.preventDefault();

     const data = {
        nome: nome.value,
        pao: pao.value,
        carne: carne.value,
        opcionais: Array.from(opcionaisCli.value),
        status: "Solicitado"
     }

    //CONVERTENDO PARA JSON

    const dataJson = JSON.stringify(data)

    const req = await fetch("http://localhost:3000/burgers",{
        method: 'POST',
        headers: {"Content-Type": "application/json"},
        body: dataJson
    });


    const res = await req.json();

    msg.value = `pedido N° ${res.id} realizado`
    setTimeout(()=>{
        msg.value = ""
    },3000);
    limpar()
 }


// função para limpar os campos
const limpar = () =>{
    nome.value ='';
    pao.value = '';
    carne.value = '';
    opcionaisCli.value ='';
}
 onMounted(() => {
    getIngredients();
});

</script>



<template>
<div class="main-container">
   
    <h1> MONTE SEU BURGER</h1>
    <Message :msg="msg" v-show="msg"/>
    <form class="formBurger" @submit="createBurger">
        <div class="input-container">
            <label for="nome">Nome do Cliente:</label>
            <input id="nome" name="nome" v-model="nome" placeholder="Digite Seu Nome">
        </div>

        <div class="input-container">
            <label for="pao">Escolha seu Pão:</label>
            <select v-model="pao" id="pao" name="pao">
                <option value=""> Selecione seu pão</option>
                <option v-for="(pao, index) in paes" :key="index" :value="pao.tipo">{{ pao.tipo }}</option>
            </select>
        </div>

        <div class="input-container">
            <label for="carne">Escolha sua carne:</label>
            <select v-model="carne" id="carne" name="carne">
                <option value=""> Selecione sua carne</option>
                <option v-for="(carne, index) in carnes" :key="index" :value="carne.tipo">{{carne.tipo}}</option>
            </select>
        </div>

          <div class="opcionais-container">
            <label id="opcionais-title" for="opcionais">Escolha seu opcional:</label>
            <div class="checkboxContainer" v-for="opcional in opcionaisData" :key="opcional.id">
              <input type="checkbox" name="opcioanis" id="checkbox" v-model="opcionaisCli" :value="opcional.tipo">   
              <span> {{opcional.tipo}}</span>
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