<template>
  <section class="display">
    <strong>{{ currentTime }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: 'Cronometer',
  props: {
    timeInSeconds: {
      type: Number,
      default: 0
    }
  },
  computed: {
    currentTime(): string {
      return new Date(this.timeInSeconds * 1000).toISOString().substr(11,8)
    }
  },
})
</script>

<style scoped>
  .display {
    color: #fff;
    background-color: var(--bg-primary);
  }
</style>