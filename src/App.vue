<template>
  <div>
    <NavSection />
    <MainSection />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import NavSection from './components/NavSection.vue'
import MainSection from './components/MainSection.vue'

@Component({
  components: {
    NavSection,
    MainSection,
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
