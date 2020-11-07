<template>
  <div id="app">
    <arbol :indice="0" titulo="Root">
      <arbol :indice="1" titulo="Child">
        <span>Hola Mundo</span>
      </arbol>
      
    </arbol>
    
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import Fecha from "./components/Fecha.vue";
import Tabla from "./components/Tabla.vue";
import Arbol from "./components/Arbol.vue";

export default Vue.extend({
  name: 'App',
  components: {
    HelloWorld,
    Fecha,
    Tabla,
    Arbol
  },
  data: function(){
    return({
      a:1
    });
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
}
</style>
