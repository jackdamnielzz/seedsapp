<template>
  <div id="app">
    <h1>Gardening Assistant</h1>
    <SeedManager />
  </div>
</template>

<script>
import SeedManager from './components/SeedManager.vue'

export default {
  name: 'App',
  components: { SeedManager }
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
