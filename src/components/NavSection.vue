<template>
  <div class="nav-section">
    <div class="menu">
      <ul>
        <li><a href="#">Item 1</a></li>
        <li><a href="#">Item 2</a></li>
        <li><a href="#">Item 3</a></li>
        <li><a href="#">Item 4</a></li>
        <li><a href="#">Item 5</a></li>
        <li><a href="#">Item 6</a></li>
        <li><a href="#">Item 7</a></li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component({
  components: {},
})
export default class Nav extends Vue {}
</script>

<style lang="scss" scoped>
.nav-section {
  height: 100vh;
  width: 30vw;
  background-color: #999900;
  float: left;
  .menu {
    width: 100%;
  }
  ul {
    padding: 50px 0 0 0;
    margin: 0;
  }
  ul li a {
    display: block;
    color: #fff;
    text-decoration: none;
    padding: 30px 0;
    background-color: #cccc00;
    margin: 20px;
  }
  ul li:first-child {
  }
}
</style>
