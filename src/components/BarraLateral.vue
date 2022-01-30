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
      <img src="../assets/logo.png" alt="" />
    </h1>

    <button class="button" @click="alterarTema">
      {{ textoBotao }}
    </button>
  </header>
</template>

<script lang="ts">
// colocamos o lang por que usaremos em especific o typescript
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'BarraLateral',
  emits: ['aoTemaAlterado'],
  data() {
    return {
      modoEscuroAtivo: false,
    }
  },
  computed: {
    textoBotao() {
      if (this.modoEscuroAtivo) {
        return 'Desativar modo escuro'
      } else {
        return 'Ativar modo escuro'
      }
    },
  },
  methods: {
    alterarTema() {
      this.modoEscuroAtivo = !this.modoEscuroAtivo
      this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
    },
  },
})
</script>

<style scoped>
header {
  background: #0d3b66;
  /* cor de fundo  */
  width: 100%;
  /* largura  */
  height: 100vh;
  padding: 0.5rem;
  display: grid;
  justify-content: center;
  /* altura  */
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
