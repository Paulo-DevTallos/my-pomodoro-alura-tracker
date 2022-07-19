<template>
  <div class="box">
    <div class="columns"> 
      <div class="columns is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?">
      </div>
      <div class="column">
        <div class="is-flex is-align-items-center is-justify-content-space-between">
          <Cronometer :timeInSeconds="timeInSeconds" />
          <button class="button" @click="startCounter">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>play</span>
          </button>
          <button class="button" @click="finishCounter">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometer from "./Cronometer.vue";

export default defineComponent({
  name: "Form",
  components: { Cronometer },
  data() {
    return {
      timeInSeconds: 0,
      cronometer: 0
    };
  },
  methods: {
    startCounter() {
      this.cronometer = setInterval(() => {
        this.timeInSeconds++;
      }, 1000);
    },
    finishCounter() {
      clearInterval(this.cronometer);
    },
  },
})
</script>

<style scoped>
  
</style>