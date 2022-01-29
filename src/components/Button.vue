<template>
  <button class="button" @click="clicando" :disabled="desabiltado">
    <span class="icon">
      <i class="fas fa-play"></i>
    </span>
    <span>{{ texto }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
  name: 'Button',
  emits: ['clicando'],
  props: {
    desabiltado: {
      type: Boolean,
    },
    icone: {
      type: String,
      required: true,
    },
    texto: {
      type: String,
      required: true,
    },
  },
  methods: {
    click(): void {
      this.$emit('clicando')
    },
  },
})
</script>
