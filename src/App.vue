<template>
  <main class="columns is-gapless is-multiline">
    <div class="columns is-one-quarter">
      <SideBar />
    </div>
    <div class="columns is-three-quarter">

    </div>
  </main>
</template>

<script lang="ts">
import SideBar from "./components/SideBar.vue";
export default {
    name: "App",
    components: { SideBar }
}
</script>

<style>
  @import './assets/base.css';
</style> 