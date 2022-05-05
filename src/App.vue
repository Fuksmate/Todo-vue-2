<template>
  <div>
    <NavSection />
    <MainsSection />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import NavSection from './components/NavSection.vue'
import MainsSection from './components/MainSection.vue'

@Component({
  components: {
    NavSection,
    MainsSection,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Vesper+Libre&display=swap');
body {
  color: #fff;
  text-align: center;
  font-family: 'Vesper Libre', serif;
  background-color: #201e1e;
  margin: 0;
  padding: 0;
}
</style>
