<template>
  <header class="header">
    <h1>
      My <span>Pomodoro</span>
    </h1>
    <button class="button" @click="changeTheme">{{ changeButtonText }}</button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: 'SideBar',
  emits: ['changedTheme'],
  data() {
    return {
      dark_mode_activit: false
    }
  },
  computed: {
    changeButtonText() {
      if(this.dark_mode_activit) {
        return 'Desativar modo escuro'
      } else {
        return 'Ativar modo escuro'
      }
    }
  },
  methods: {
    changeTheme() {
      this.dark_mode_activit = !this.dark_mode_activit
      this.$emit('changedTheme', this.dark_mode_activit)
    }
  },
})
</script>


<style scoped>
  .header {
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    padding: 1rem;
    text-align: center;
  }

  .header h1 {
    color: #fff;
    font-size: 40px;
  }

  .header h1 span {
    color: rgb(217, 16, 16);
    font-weight: 600;
  }

  @media only screen and (max-width: 768px) {
    .header {
      padding: 2.5em;
      height: auto;
    }
  }

</style>