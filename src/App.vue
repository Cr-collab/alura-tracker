<template>
    <main class="columns is-gapless is-multiline">
      <!-- a tag main vai comportar tudo na nossa aplicação   -->
      <!-- 
         columns -> esta falando que a nossa aplicação vai ter varias colunas 
         is-gapless -> diz que não vai ter espaçamentos entre nossas colunas 
         is-multiline -> ele pode permitir multiplas linhas 
        -->

        <!-- 
           dividir em duas porções 
        -->

        <div class="column is-one-quarter"> 
          <!-- 

            -->
            <BarraLateral/>

        </div>
        <!-- cada div são uma porção   -->
        <div class="column is-three-quarter">
           <Formulario/>
        </div>
    </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import BarraLateral from '../src/components/BarraLateral.vue'
import Formulario from './components/Formulario.vue';



export default defineComponent({
  name: 'App',
  components:{
    BarraLateral,
    Formulario  
  }
});

</script>

<style scoped>

</style>
