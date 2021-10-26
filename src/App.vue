<template>
  <div id="app">
    <tree-files :list="list"/>
  </div>
</template>

<script>
import TreeFiles from './components/TreeFiles/TreeFiles.vue'

export default {
  name: 'App',
  data: () => ({
    list: require('../public/static/node_modules.json')
  }),
  components: {
    TreeFiles
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 38px;
}
</style>
