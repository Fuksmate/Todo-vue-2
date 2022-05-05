<template>
  <div class="task">
    <h2 class="title">{{ todo.title }}</h2>
    <span class="description">
      {{ todo.desc }}
    </span>
    <div class="button-section">
      <button @click="open = true" class="button red" type="button"></button>
      <button
        @click="removeTask(todo.id)"
        class="button yellow"
        type="button"
      ></button>
      <button
        @click="isCompleted(todo.id)"
        class="button green"
        type="button"
      ></button>
    </div>
    <EditTask v-if="open" @closeWindow="closeWindow" :todo="todo" />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import EditTask from './EditTask.vue'
import TaskInterface from './AddTask.vue'

@Component({
  components: { EditTask },
})
export default class BaseTask extends Vue {
  @Prop({ required: true }) todo!: TaskInterface

  open: false = false

  closeWindow(close: false): void {
    this.open = close
  }
  removeTask(e: number): void {
    this.$emit('removeTask', e)
  }
  isCompleted(e: number): void {
    this.$emit('isCompleted', e)
  }
}
</script>

<style lang="scss" scoped>
.task {
  width: 50%;
  height: 170px;
  position: relative;
  background-color: #201e1e;
  margin: 30px auto;
  border: 1px solid #cccc00;
  .title {
    font-size: 16px;
    width: 100%;
    text-align: left;
    margin-top: 20px;
    padding-left: 20px;
    font-weight: 300;
  }
  .description {
    margin-top: 5px;
    padding-left: 20px;
    float: left;
    max-height: 50px;
  }
  .button-section {
    width: 200px;
    height: 50px;
    position: absolute;
    bottom: 0;
    right: 0;
    button {
      z-index: 1;
      position: relative;
      outline: none;
      overflow: hidden;
      transition: color 0.4s ease-in-out;
    }

    button::before {
      content: '';
      z-index: -1;
      position: absolute;
      bottom: 100%;
      right: 100%;
      width: 1em;
      height: 1em;
      border-radius: 50%;
      background-color: #cccc00;
      transform-origin: center;
      transform: translate3d(50%, 50%, 0) scale3d(0, 0, 0);
      transition: transform 0.45s ease-in-out;
    }

    button:hover::before {
      transform: translate3d(50%, 50%, 0) scale3d(15, 15, 15);
    }

    .button {
      border: none;
      color: white;
      padding: 15px 15px;
      margin: 0 5px;
      text-decoration: none;
      cursor: pointer;
    }
    .red {
      background-color: red;
    }
    .yellow {
      background-color: #999900;
    }
    .green {
      background-color: green;
    }
  }
}
</style>
