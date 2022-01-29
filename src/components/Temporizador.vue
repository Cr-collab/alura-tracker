<template>
  <div class="is-flex is-align-itens-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />

    <Button
      :desabiltado="cronometroRodando"
      icone="fas fa-play"
      texto="iniciar"
      @click="iniciar"
    />
    <Button
      :desabiltado="!cronometroRodando"
      icone="fas fa-stop"
      texto="Stop"
      @click="finalizar"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Cronometro from './Cronometro.vue'
import Button from './Button.vue'

export default defineComponent({
  name: 'Temporizador',
  emits: ['aoTemporizadorFinalizado'],
  components: {
    Cronometro,
    Button,
  },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false,
    }
  },

  methods: {
    iniciar() {
      // comecar a contagem
      this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1
      }, 1000)
    },
    finalizar() {
      this.cronometroRodando = false
      clearInterval(this.cronometro)
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
      this.tempoEmSegundos = 0
    },
  },
})
</script>
