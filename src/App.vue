<template>
  <div id="app">
    <fecha />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Fecha from "./components/Fecha.vue"

export default {
  name: 'App',
  components: {
    HelloWorld,
    Fecha
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
