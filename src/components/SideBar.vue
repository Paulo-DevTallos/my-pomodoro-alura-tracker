<template>
  <header class="header">
    <h1>
      My <span>Pomodoro</span>
    </h1>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: 'SideBar,'
})
</script>


<style scoped>
  .header {
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    padding: 1rem;
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