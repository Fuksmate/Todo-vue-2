<template>
  <div class="main-section">
    <AddTask />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import AddTask from './AddTask.vue'

@Component({
  components: {
    AddTask,
  },
})
export default class main extends Vue {}
</script>

<style lang="scss" scoped>
.main-section {
  height: 100vh;
  width: 70vw;
  float: left;
}

</style>
