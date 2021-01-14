<template>
  <header>
    <div class="container">
      <div class="row align-items-center">
        <div class="col-lg-12" id="conteudoPrincipal">
          <h1 class="display-4 mt-5 mb-2 text-center cor3">
            {{ empresa }}
          </h1>
          <p class="lead mb-5 text-center cor4">
            {{ texto }}
          </p>
          <slot></slot>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data(){
    return{
      empresa: "Dedetizações e Imunizações - Allan Peres",
      texto: "Realizamos imunizações em todo o Rio de Janeiro, venha fazer um orçamento!"
    }
  }
};
</script>

<style> 
@import url('https://fonts.googleapis.com/css2?family=Lora&family=Merriweather:wght@300&display=swap');

  h1{
    font-family: 'Lora', serif;
  } 

  #conteudoPrincipal{ 
    padding-left: 10px;
    padding-right: 10px;
    background: rgba(255,255,255); 
    border-radius: 10px; 
  }
 

  header{ 
    background-color: rgb(0, 0, 0); 
    padding-top: 6%; 
    padding-bottom: 6%;  
    background-image: url("../assets/banner3.jpg");
    height: 100%;
    background-position: center; 
    background-size: cover;
    background-repeat: no-repeat;
    opacity: 0.8;      
  }

  @media screen and (min-width: 776px) {

    header{
      background-image: url("../assets/banner3.jpg");  
      background-position: right; 
      background-size: contain; 
      
    }
      
  } 

  
  .cor3{
    color : #3C6E71;
  }

  .cor4{
    color : #353535;
  }
 
</style>