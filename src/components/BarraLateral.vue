<template>
    <!-- 
      o nosso component vai ser divido em trés porções 
      template -> que é o html 
      script -> que é o javascript 
      style -> que é a estilização 
     -->
     <header>
       <!-- ele tem o titulo da nossa aplicação por isso estamos utilizando header   -->
       <h1>
         <img src="../assets/logo.png" alt="">
       </h1>
     </header>
</template>


<script lang="ts">
 // colocamos o lang por que usaremos em especific o typescript 
 import  { defineComponent } from  'vue'
 
 export default defineComponent({
   name: 'BarraLateral'
 })

</script>


<style scoped>
   header { 
      background: #0d3b66;
      /* cor de fundo  */
      width: 100%;
      /* largura  */
      height: 100vh;
      /* altura  */
   }

   @media only screen and (max-width: 768px){
      header {
           padding: 2.5rem;
           height: auto;
        }  
   }
</style>
