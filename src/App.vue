<template>
  <div id="app">
    <arbol :indice="0" titulo="Root">
      <arbol :indice="1" titulo="Child3">
        <div>
          <u>
            <li>Uno</li>
            <li>Dods</li>
          </u>
        </div>
      </arbol>
      <arbol :indice="3" titulo="Child4">
        <arbol :indice="4" titulo="Child5">
          <div>
            <u>
              <li>Uno</li>
              <li>Dods</li>
            </u>
          </div>
        </arbol>
      </arbol>
      <div>Hola Mundo3</div>
    </arbol>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import Fecha from "./components/Fecha.vue";
import Tabla from "./components/Tabla.vue";
import Arbol from "./components/Arbol.vue";

export default Vue.extend({
  name: "App",
  components: {
    HelloWorld,
    Fecha,
    Tabla,
    Arbol
  },
  data: function() {
    return {
      a: 1
    };
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
