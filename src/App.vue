<template>
  <div id="app">
<<<<<<< HEAD
    <!--     
    <arbol :indice="0" titulo="Root">
=======
    <!-- <arbol :indice="0" titulo="Root">
>>>>>>> 94b70727233271903043e2053957f8a588efe76a
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
<<<<<<< HEAD
    </arbol>-->

    <PanelAlarma></PanelAlarma>
=======
    </arbol> -->

    <!-- <PanelAlarma></PanelAlarma> -->

    <tree-node nombre="Reconquista">
      <tree-node nombre="Las Flores"></tree-node>
        <tree-node nombre="San Geronimo">
          <tree-node nombre="Casa 52"></tree-node>
        </tree-node>
        <tree-node nombre="Las Flores"></tree-node>
    </tree-node>
>>>>>>> 94b70727233271903043e2053957f8a588efe76a
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import Fecha from "./components/Fecha.vue";
import Tabla from "./components/Tabla.vue";
import Arbol from "./components/Arbol.vue";
import treenode from "./components/tree-node.vue";

import PanelAlarma from "./components/PanelAlarma.vue";
import TreeNode from './components/tree-node.vue';

export default Vue.extend({
  name: "App",
  components: {
    HelloWorld,
    Fecha,
    Tabla,
    Arbol,
    PanelAlarma,
    TreeNode
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
