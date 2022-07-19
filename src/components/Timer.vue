<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometer :timeInSeconds="timeInSeconds" />
    <button class="button" @click="startCounter" :disabled="rollingCronometer">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finishCounter" :disabled="!rollingCronometer">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometer from "./Cronometer.vue";

export default defineComponent({
  name: "Timer",
  emits: ['whenFinishedTimer'], 
  components: { Cronometer },
  data() {
    return {
      timeInSeconds: 0,
      cronometer: 0,
      rollingCronometer: false,
    };
  },
  methods: {
    startCounter() {
      this.rollingCronometer = true
      this.cronometer = setInterval(() => {
        this.timeInSeconds++;
      }, 1000);
    },
    finishCounter() {
      this.rollingCronometer = false
      clearInterval(this.cronometer);
      this.$emit('whenFinishedTimer', this.timeInSeconds)
      this.timeInSeconds = 0
    },
  },
})
</script>