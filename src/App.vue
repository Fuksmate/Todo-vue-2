<template>
  <div>
    <NavSection />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import NavSection from './components/NavSection.vue'

@Component({
  components: {
    NavSection,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
body {
  color: #fff;
  text-align: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: #201e1e;
  margin: 0;
  padding: 0;
}
</style>
