<template>
  <div class="add-todo">
    <form>
      <input type="text" placeholder="Title" />
      <input type="text" placeholder="Description" />
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component({
  components: {},
})
export default class AddTask extends Vue {}
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
