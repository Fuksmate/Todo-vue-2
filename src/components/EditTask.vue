<template>
  <div class="modal">
    <p class="title">Edytuj swój task</p>
    <div class="input">
      <input type="text" v-model="title" required />
      <span class="bottom"></span>
      <span class="right"></span>
      <span class="top"></span>
      <span class="left"></span>
    </div>
    <div class="input">
      <input type="text" v-model="desc" required />
      <span class="bottom"></span>
      <span class="right"></span>
      <span class="top"></span>
      <span class="left"></span>
    </div>
    <button @click="closeWindow">Close</button>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'

import TaskInterface from './AddTask.vue'

@Component({
  components: {},
})
export default class BaseTask extends Vue {
  @Prop({ required: true }) todo!: TaskInterface

  title = this.todo.title
  desc = this.todo.desc

  open: false = false

  closeWindow(): void {
    this.todo.title = this.title
    this.todo.desc = this.desc
    this.$emit('closeWindow', false)
  }
}
</script>

<style lang="scss" scoped>
.modal {
  position: fixed;
  z-index: 999;
  height: 500px;
  width: 500px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #201e1e;
  color: black;
  border: 4px solid #999900;

  .title {
    color: #201e1e;
    font-weight: 700;
  }
  button {
    width: 100px;
    padding: 5px 20px;
    margin-top: 20px;
    z-index: 1;
    position: relative;
    font-size: inherit;
    font-family: inherit;
    color: white;
    outline: none;
    background-color: #221a1a;
     border: 1px solid #999900;
  }

  button:hover {
    cursor: pointer;
  }

  button::before {
    content: '';
    z-index: -1;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    border: 4px solid #201e1e;
    transform-origin: center;
    transform: scale(1);
  }

  button:hover::before {
    transition: all 0.75s ease-in-out;
    transform-origin: center;
    border: 4px solid #fc2f70;
    transform: scale(1.75);
    opacity: 0;
  }
}
.input {
  width: 26.5em;
  margin: 20px auto 10px auto !important;
  position: relative;
  margin: 0px auto;
}

input {
  width: 25.5em;
  color: white;
  font-size: inherit;
  font-family: inherit;
  background-color: #221a1a;
  border: 1px solid #999900;
  padding: 0.35em 0.45em;
  transition: background-color 0.3s ease-in-out;
}

input:focus {
  outline: none;
}

input::placeholder {
  color: hsla(0, 0%, 100%, 0.6);
}

span {
  position: absolute;
  background-color: #fc2f70;
  transform-origin: center;
  transition: transform 0.5s ease;
}

.bottom,
.top {
  height: 2px;
  left: 0;
  right: 0;
  transform: scaleX(0);
}

.left,
.right {
  width: 2px;
  top: 0;
  bottom: 0;
  transform: scaleY(0);
}

.top {
  top: 0;
}

.bottom {
  bottom: 0;
}

.left {
  left: 0;
}

.right {
  right: 0;
}

input:focus ~ .top,
input:focus ~ .bottom {
  transform: scaleX(1);
}

input:focus ~ .left,
input:focus ~ .right {
  transform: scaleY(1);
}
</style>
