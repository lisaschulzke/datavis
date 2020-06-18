<template>
  <div id="app">
    <Datavis msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Datavis from './components/Datavis.vue'

export default {
  name: 'App',
  components: {
    Datavis
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
