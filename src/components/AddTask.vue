<template>
  <div class="add-todo">
    <form>
      <input v-model="title" type="text" placeholder="Title" required />
      <input v-model="desc" type="text" placeholder="Description" required />
      <input @click="addTask()" type="button" value="submit" />
    </form>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'

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
  @Prop({ required: true }) todos!: TaskInterface[]

  title = ''
  desc = ''

    RadnomNumber(): number {
        return Math.floor(Math.random() * 100) + 1
    }

  addTask(): void {
    this.todos.push({
      id: this.RandomNumber(),
      title: this.title,
      desc: this.desc,
      completed: true,
    })
    ;(this.title = ''), (this.desc = ''), this.$emit('newTodo', this.todos)
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

input[type='button'] {
  width: 100%;
  background-color: #999900;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type='button']:hover {
  background-color: #cccc00;
}
</style>
