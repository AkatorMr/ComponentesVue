<template>
  <div id="app">
    <!--     
    <arbol :indice="0" titulo="Root">
      <arbol :indice="1" titulo="Child3" :conborde="true">
        <arbol :indice="4" titulo="Child3.1" :conborde="true"></arbol>
        <arbol :indice="5" titulo="Child3.2" :conborde="true"></arbol>
        <arbol :indice="6" titulo="Child3.3" :conborde="true"></arbol>
        <div>
          <u>
            <li>Uno</li>
            <li>Dods</li>
          </u>
        </div>
      </arbol>
      <arbol :indice="3" titulo="Child4" :conborde="true">
        <arbol :indice="4" titulo="Child5" :conborde="false">
          <div>
            <u>
              <li>Uno</li>
              <li>Dods</li>
            </u>
          </div>
        </arbol>
      </arbol>
      <div>Hola Mundo3</div>
    </arbol>-->

    <PanelAlarma></PanelAlarma>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import Fecha from "./components/Fecha.vue";
import Tabla from "./components/Tabla.vue";
import Arbol from "./components/Arbol.vue";

import PanelAlarma from "./components/PanelAlarma.vue";

export default Vue.extend({
  name: "App",
  components: {
    HelloWorld,
    Fecha,
    Tabla,
    Arbol,
    PanelAlarma
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
