<template>
  <div class="main-section">
    <AddTask :todos="todos" @newTodo="newTodo" />
    <BaseTask
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @removeTask="removeTask"
      @isCompleted="isCompleted"
    />
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
  todos: TaskInterface[] = []

  newTodo(e: TaskInterface): void {
    this.todos = e
  }
  removeTask(e: number): void {
    this.todos = this.todos.filter(function (obj) {
      return obj.id != e
    })
  }
  isCompleted(e: number): void {
    console.log(e)
  }
}
</script>

<style lang="scss" scoped>
.main-section {
  height: 100vh;
  width: 70vw;
  float: right;
}
</style>
