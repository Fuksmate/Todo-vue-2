<template>
  <div class="main-section">
    <AddTask />
    <BaseTask v-for="todo in todos" :key="todo.id" :todo="todo" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import AddTask from './AddTask.vue'
import BaseTask from './BaseTask.vue'
import TaskInterface from './AddTask.vue'

@Component({
  components: {
    AddTask,
    BaseTask,
  },
})
export default class MainSection extends Vue {
  todos: TaskInterface[] = localStorage.todos
    ? JSON.parse(localStorage.todos)
    : []
}
</script>

<style lang="scss" scoped>
.main-section {
  height: 100vh;
  width: 70vw;
  float: right;
}
</style>
