<template>
  <main class="columns is-gapless is-multiline">
    <div class="columns is-one-quarter">
      <SideBar />
    </div>
    <div class="columns is-three-quarter">
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
      todos: [] as IToDo[]
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
    }
  }
})
</script>

<style>
  .lista {
    padding: 1.25rem;
  }
</style>
