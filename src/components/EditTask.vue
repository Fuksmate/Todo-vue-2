<template>
  <div class="modal">
    <p class="title">Edytuj swój task</p>
    <div class="input">
      <input type="text" placeholder="Title" />
      <span class="bottom"></span>
      <span class="right"></span>
      <span class="top"></span>
      <span class="left"></span>
    </div>
    <div class="input">
      <input type="text" placeholder="Description" />
      <span class="bottom"></span>
      <span class="right"></span>
      <span class="top"></span>
      <span class="left"></span>
    </div>
    <button @click="closeWindow">Close</button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component({
  components: {},
})
export default class BaseTask extends Vue {
  open: false = false
  closeWindow(): void {
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
  background-color: #999900;
  color: black;
  border: 4px solid black;

  .title {
    color: #201e1e;
    font-weight: 700;
  }
  button {
    z-index: 1;
    position: relative;
    font-size: inherit;
    font-family: inherit;
    color: white;
    width: 100px;
    height: 40px;
    outline: none;
    border: none;
    background-color: #201e1e;
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
  background-color: #201e1e;
  padding: 0.35em 0.45em;
  border: 1px solid transparent;
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
