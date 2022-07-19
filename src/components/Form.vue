<template>
  <div class="box form">
    <div class="columns"> 
      <div class="columns is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input type="text" v-model="description" class="input" placeholder="Qual tarefa você deseja iniciar?">
      </div>
      <div class="column">
        <Timer @whenFinishedTimer="finishWork"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import Timer from './Timer.vue'

export default defineComponent({
  name: "Form",
  emits: ['whenSaveWorks'],
  components: {
    Timer,
  },
  data() {
    return {
      description: '',
    }
  },
  methods: {
    finishWork(currentTime: number): void {
      this.$emit('whenSaveWorks', {
        durationInSeconds: currentTime,
        description: this.description,  
      })
      this.description = '' 
    }
  }
})
</script>

<style>
  .form {
    color: var(--text-primary);
    background-color: var(--bg-primary);
  }
</style>