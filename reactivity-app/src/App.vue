<template>
  <div id="app">
    <List />
  </div>
</template>

<script>
import List from './components/List.vue'
export default {
  name: 'app',
  components: {
    List
  }
}
</script>

<style>
 
body {
  background-color: lightblue;
  font-family: Georgia, 'Times New Roman', Times, serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  padding-top: 50px;
}
body, html {
  margin: 0;
  height: 100%;
}
#app {
    width: 50%;
}
</style>