<template>
  <BoxEmpty>
    <div class="columns">
      <div class="column is-7">
        {{ todo.description || 'Tarefa sem descrição'}}
      </div>
      <div class="column">
        <Cronometer :timeInSeconds="todo.durationInSeconds" />
      </div>
    </div>
  </BoxEmpty>
</template>

<script lang="ts">
import type { IToDo } from "@/interfaces/IToDo"
import { defineComponent } from "vue"
import Cronometer from "./Cronometer.vue"
import type { PropType } from "vue"
import BoxEmpty from "./BoxEmpty.vue"

export default defineComponent({
  name: 'ToDoList',
  props: {
    todo: {
      type: Object as PropType<IToDo>,
      required: true
    }
  },
  components: {
    Cronometer,
    BoxEmpty
}
})
</script>
