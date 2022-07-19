<template>
  <main class="columns is-gapless is-multiline" :class="{ 'dark-mode': dark_mode_activit }">
    <div class="columns is-one-quarter">
      <SideBar @changedTheme="changeTheme" />
    </div>
    <div class="columns is-three-quarter content">
      <Form @whenSaveWorks="saveWork"/>
      <div class="lista">
        <ToDoList v-for="(todo, index) in todos" :key="index" :todo="todo"/>
        <BoxEmpty v-if="emptyList">
          Você não está muito produtivo hoje :(
        </BoxEmpty>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "./components/SideBar.vue";
import Form from "./components/Form.vue";
import ToDoList from './components/ToDoList.vue'
import type { IToDo } from "./interfaces/IToDo";
import BoxEmpty from "./components/BoxEmpty.vue";

export default defineComponent({
  name: "App",
  components: {
    SideBar,
    Form,
    ToDoList,
    BoxEmpty
},
  data() {
    return {
      todos: [] as IToDo[],
      dark_mode_activit: false,
    }
  },
  computed: {
    emptyList(): boolean {
      return this.todos.length === 0
    }
  },
  methods: {
    saveWork(work: IToDo) {
      this.todos.push(work)
    },
    changeTheme(dark_mode_activit: boolean): void {
      this.dark_mode_activit = dark_mode_activit
    } 
  }
})
</script>

<style>
  .lista {
    padding: 1.25rem;
  }

  main {
    --bg-primary: #fff;
    --text-primary: #000;
  }
  main.dark-mode {
    --bg-primary: #2b2b4b;
    --text-primary: #ddd;
  }

  .content {
    background-color: var(--bg-primary);
  }
</style>
