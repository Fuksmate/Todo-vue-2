<template>
  <div class="add-todo">
    <form>
      <input v-model="title" type="text" placeholder="Title"  required/>
      <input v-model="desc" type="text" placeholder="Description" required />
      <input @click="addTask()" type="submit" value="Submit" />
    </form>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

export interface TaskInterface {
  title: string
  desc: string
  id: number
  completed: boolean
}
@Component({
  components: {},
})
export default class AddTask extends Vue {
  title = ''
  desc = ''
  todos: TaskInterface[] = localStorage.todos
    ? JSON.parse(localStorage.todos)
    : []

  addTask(): void {
    this.todos.push({
      id: Math.random(),
      title: this.title,
      desc: this.desc,
      completed: true,
    })
    localStorage.setItem('todos', JSON.stringify(this.todos))
  }
}
</script>

<style lang="scss" scoped>
.add-todo {
  width: 35%;
  margin: 80px auto;
}
input[type='text'],
select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  text-align: center;
  box-sizing: border-box;
}

input[type='submit'] {
  width: 100%;
  background-color: #999900;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type='submit']:hover {
  background-color: #cccc00;
}
</style>
