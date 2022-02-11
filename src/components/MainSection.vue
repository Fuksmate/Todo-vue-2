<template>
  <div class="main-section">
    <AddTask />
    <BaseTask />
    <BaseTask />
    <BaseTask />
    <BaseTask />
    <BaseTask />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import AddTask from './AddTask.vue'
import BaseTask from './BaseTask.vue'
@Component({
  components: {
    AddTask,
    BaseTask,
  },
})
export default class main extends Vue {}
</script>

<style lang="scss" scoped>
.main-section {
  height: 100vh;
  width: 70vw;
  float: right;
}
</style>
