<template>
  <div id="app">
    <h1>Welcome to the IMDb Random Generator</h1>
    <h2>Click on the button below and find a random movie on the Internet Movie Database</h2>
    <RandomGenerator />
  </div>
</template>

<script>
import RandomGenerator from './components/RandomGenerator.vue'

export default {
  name: 'App',
  components: {
    RandomGenerator
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
