<template>
  <main
    class="columns is-gapless is-multiline"
    :class="{ 'modo-escuro': modoEscuroAtivo }"
  >
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
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <!-- cada div são uma porção   -->
    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <Tarefa
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tarefa="tarefa"
        />
        <Box v-if="listaEstaVazia">
          Você não esta Muito Produtivo Hoje 😟
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

import BarraLateral from '../src/components/BarraLateral.vue'
import Formulario from './components/Formulario.vue'
import ITarefa from './components/interface/ITarefa'
import Tarefa from './components/Tarefa.vue'
import Box from './components/Box.vue'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box,
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false,
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    },
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0
    },
  },
})
</script>

<style scoped>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #fff;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
