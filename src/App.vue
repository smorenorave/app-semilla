<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <SeedPlot msg="HOLA"/>
</template>

<script>
import SeedPlot from './components/SeedPlot.vue'

export default {
  name: 'App',
  components: {
    SeedPlot
  }
}
</script>

<style>
#app {
  padding-right: 400px;
  padding-left: 400px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
